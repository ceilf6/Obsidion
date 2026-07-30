# 技术方案

截至 **2026-03-14**，结合你当前实现（`Planner -> Executor -> 分阶段执行 -> 错误反馈`），最实用的是“**LangGraph 化编排**”，而不是直接把核心逻辑全交给高层 Agent。

**可选技术方案（按推荐度）**

| 方案 | 如何套到 FrontAgent | 优点 | 缺点 |
| --- | --- | --- | --- |
| 1. 保持自研核心，仅引入 LangSmith 观测 | 不改主流程，只接 tracing/eval | 改造最小，快速提升可观测性 | 不解决恢复/持久化/状态回放 |
| 2. LangChain v1（`createAgent` + middleware） | 用 LangChain 管理模型调用和工具中间件 | 上手快，多模型统一接口，开发效率高 | 对你这种“严格阶段依赖+回放”场景控制粒度偏粗 |
| 3. LangGraph v1 重构编排（推荐） | 把“阶段1~7”映射为 graph nodes + edges；状态放 graph state | 原生支持持久化、checkpoint、HITL 中断恢复、可重放；非常契合你现有 phase 机制 | 改造成本中高；需把副作用操作做幂等/可重放 |
| 4. LangGraph + LangSmith Deployment | 在 3 的基础上用托管运行时部署 | 生产级：长任务、水平扩展、线程态运行、断点续跑更完整 | 平台依赖和成本增加 |
| 5. OpenAI Agents SDK（TS）替代编排层 | 用 `Agent/Handoffs/Guardrails/Sessions/MCP` 重建编排 | TS 体验好、抽象轻、MCP/多 agent/trace 内建 | 生态偏 OpenAI（供应商锁定更强），跨模型策略弱于 LangChain/LangGraph |
| 6. Temporal + 现有或 LangGraph | 把长流程放 Temporal Workflow，LLM/tool 调用做 Activity | 可靠性最强（故障恢复、重试、版本演进） | 工程复杂度最高，团队学习和运维成本大 |

**针对你项目的建议路径（推断）**

1. 先做 **方案3（LangGraph 编排）**：保留你的 `Planner/Executor` 逻辑，先把“阶段、依赖、恢复”迁到 graph runtime。
2. 再接 **方案4/1（LangSmith）**：把每个 phase 与工具调用打成 trace。
3. 若后续要跑超长任务或企业级 SLA，再加 **方案6（Temporal）**。

这个判断是基于你当前代码结构的推断（例如 [planner.ts](https://www.notion.so/Users/a86198/Desktop/Lab/AI/3-Application/FrontAgent-app/packages/core/src/planner.ts)、[executor.ts](https://www.notion.so/Users/a86198/Desktop/Lab/AI/3-Application/FrontAgent-app/packages/core/src/executor.ts) 已经是天然“状态机雏形”）。

**参考资料**

- LangChain v1（`create_agent`、生产定位）: [docs.langchain.com/oss/python/releases/langchain-v1](https://docs.langchain.com/oss/python/releases/langchain-v1)
- LangGraph v1（稳定性、与 LangChain v1 关系）: [docs.langchain.com/oss/javascript/releases/langgraph-v1](https://docs.langchain.com/oss/javascript/releases/langgraph-v1)
- LangGraph Durable Execution: [docs.langchain.com/oss/javascript/langgraph/durable-execution](https://docs.langchain.com/oss/javascript/langgraph/durable-execution)
- LangGraph Interrupts/HITL: [docs.langchain.com/oss/python/langgraph/interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)
- LangSmith Observability: [docs.langchain.com/oss/javascript/langchain/observability](https://docs.langchain.com/oss/javascript/langchain/observability)
- LangSmith Deployment: [docs.langchain.com/langsmith/deployments](https://docs.langchain.com/langsmith/deployments)
- OpenAI Agents SDK Guide: [developers.openai.com/api/docs/guides/agents-sdk](https://developers.openai.com/api/docs/guides/agents-sdk)
- OpenAI Agents SDK TypeScript: [openai.github.io/openai-agents-js](https://openai.github.io/openai-agents-js/)
- OpenAI Background mode: [developers.openai.com/api/docs/guides/background](https://developers.openai.com/api/docs/guides/background)
- Temporal（可靠执行）: [docs.temporal.io](https://docs.temporal.io/)
- Temporal TypeScript SDK 指南: [docs.temporal.io/develop/typescript](https://docs.temporal.io/develop/typescript)