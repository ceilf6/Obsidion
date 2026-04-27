# 风险隔离+平滑迁移 LangGraph

https://github.com/ceilf6/Lab/commit/fd3f5dc25dd71ea3246bd66d8502cea954f87fe2

这是一个“风险隔离 + 平滑迁移”策略，核心原因有 4 点：

1. **稳定性**兜底
    
    native 是你当前线上逻辑；langgraph 是新引入。双引擎可以在新路径出现边缘问题时即时回退，不阻断任务执行。
    
2. **渐进**迁移
    
    你现有流程（错误恢复、事实更新、MCP 调用）很重，直接全量替换风险高。双引擎允许按任务类型/环境逐步切流验证。
    
3. **A/B 对比**与可观测性
    
    同一任务可比较两种引擎的成功率、恢复次数、耗时，便于判断是否可以彻底切换。
    
4. **兼容**现有生态
    
    现有调用方（CLI、脚本、已有参数）无需一次性重构，默认行为不变，只在 --engine langgraph 时启用新流。
    

如果你目标是“只保留一个引擎”，我建议分两步：

1. 先把默认改成 langgraph，保留 native 一段观察窗口。
2. 指标稳定后删除 native 分支和开关。

```tsx
  /**
   * 使用 LangGraph 执行阶段流。
   */
  private async executeStepsWithErrorFeedbackViaLangGraph(
    steps: ExecutionStep[],
    context: {
      task: AgentTask;
      collectedContext: { files: Map<string, string> };
    },
    onStepComplete?: (step: ExecutionStep, output: ExecutorOutput) => void,
    onPhaseError?: (phase: string, errors: Array<{ step: ExecutionStep; error: string }>) => Promise<ExecutionStep[]>,
    onPhaseComplete?: (phase: string, results: ExecutorOutput[]) => Promise<Array<{ step: ExecutionStep; error: string }>>
  ): Promise<ExecutorOutput[]> {
    const orderedPhaseGroups = this.buildOrderedPhaseGroups(steps);
    const serializablePhaseGroups: SerializablePhaseExecutionGroup[] = orderedPhaseGroups.map(group => ({
      phase: group.phase,
      steps: group.steps,
      dependencies: Array.from(group.dependencies),
      firstSeenIndex: group.firstSeenIndex,
      priority: group.priority
    }));

    const RuntimeStateAnnotation = Annotation.Root({
      runtime: Annotation<LangGraphRuntimeState>({
        reducer: (_left, right) => right,
        default: () => ({
          phaseGroups: [],
          phaseIndex: 0,
          completedStepIds: [],
          allResults: []
        })
      })
    });

    const graph = new StateGraph(RuntimeStateAnnotation)
      .addNode('select_phase', () => ({}))
      .addNode('execute_phase', async (state) => {
        const runtime = state.runtime as LangGraphRuntimeState;
        if (runtime.phaseIndex >= runtime.phaseGroups.length) {
          return {};
        }

        const phaseGroupData = runtime.phaseGroups[runtime.phaseIndex];
        const phaseGroup: PhaseExecutionGroup = {
          ...phaseGroupData,
          dependencies: new Set(phaseGroupData.dependencies)
        };
        const completedStepIds = new Set(runtime.completedStepIds);
        const allResults = [...runtime.allResults];

        await this.executeSinglePhaseWithRecovery(
          phaseGroup,
          context,
          completedStepIds,
          allResults,
          onStepComplete,
          onPhaseError,
          onPhaseComplete
        );

        return {
          runtime: {
            ...runtime,
            completedStepIds: Array.from(completedStepIds),
            allResults
          }
        };
      })
      .addNode('advance_phase', (state) => {
        const runtime = state.runtime as LangGraphRuntimeState;
        return {
          runtime: {
            ...runtime,
            phaseIndex: runtime.phaseIndex + 1
          }
        };
      })
      .addEdge(START, 'select_phase')
      .addConditionalEdges('select_phase', (state) => {
        const runtime = state.runtime as LangGraphRuntimeState;
        return runtime.phaseIndex >= runtime.phaseGroups.length ? END : 'execute_phase';
      })
      .addEdge('execute_phase', 'advance_phase')
      .addEdge('advance_phase', 'select_phase')
      .compile({
        checkpointer: this.config.langGraph?.useCheckpoint ? new MemorySaver() : undefined,
        name: 'frontagent.phase.flow'
      });

    const initialState: LangGraphRuntimeState = {
      phaseGroups: serializablePhaseGroups,
      phaseIndex: 0,
      completedStepIds: [],
      allResults: []
    };

    const runnableConfig = this.config.langGraph?.useCheckpoint
      ? {
        configurable: {
          thread_id: `${this.config.langGraph?.threadIdPrefix ?? 'frontagent'}-${Date.now()}`
        }
      }
      : undefined;

    const finalState = await graph.invoke({ runtime: initialState }, runnableConfig as any) as {
      runtime?: LangGraphRuntimeState;
    };

    return finalState.runtime?.allResults ?? [];
  }

  /**
   * 按阶段执行步骤，支持错误反馈循环（Tool Error Feedback Loop）
   */
  async executeStepsWithErrorFeedback(
    steps: ExecutionStep[],
    context: {
      task: AgentTask;
      collectedContext: { files: Map<string, string> };
    },
    onStepComplete?: (step: ExecutionStep, output: ExecutorOutput) => void,
    onPhaseError?: (phase: string, errors: Array<{ step: ExecutionStep; error: string }>) => Promise<ExecutionStep[]>,
    onPhaseComplete?: (phase: string, results: ExecutorOutput[]) => Promise<Array<{ step: ExecutionStep; error: string }>>
  ): Promise<ExecutorOutput[]> {
    if (this.shouldUseLangGraphEngine()) {
      if (this.config.debug) {
        console.log('[Executor] Using LangGraph execution engine');
      }
      return this.executeStepsWithErrorFeedbackViaLangGraph(
        steps,
        context,
        onStepComplete,
        onPhaseError,
        onPhaseComplete
      );
    }

    const orderedPhaseGroups = this.buildOrderedPhaseGroups(steps);

    const allResults: ExecutorOutput[] = [];
    const completedStepIds = new Set<string>();

    // 按阶段顺序执行
    for (const phaseGroup of orderedPhaseGroups) {
      await this.executeSinglePhaseWithRecovery(
        phaseGroup,
        context,
        completedStepIds,
        allResults,
        onStepComplete,
        onPhaseError,
        onPhaseComplete
      );
    }

    return allResults;
  }
```