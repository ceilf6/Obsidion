# 在FrontAgent上的使用实例

---

## 实现总结

### 新建文件

**`packages/core/src/memory/types.ts`**

定义了记忆系统的所有类型：`MemoryConfig`、`MemoryIndex`、`MemoryTopicMeta`、`MemoryTopic`、`MemoryEntry`、`PersistenceInput`、`RecallQuery`、`RecalledMemory`，以及目录名、文件名和预算相关常量。

**`packages/core/src/memory/store.ts`**

实现了覆盖四个阶段的 `MemoryStore` 类：

- **阶段 1（预加载）**：`preload()` 会读取 `MEMORY.md` 索引文件和各个 topic 文件，在可配置的字符预算内按最近更新时间排序加载
- **阶段 2（召回）**：`recall(query)` 会基于文件路径匹配、标签重叠、关键词重叠和 topic 相关性对条目打分，并通过 `injectedKeys` 集合实现单次会话内去重，同时受 recall budget 限制
- **阶段 3（持久化）**：`persist(input)` 会将 facts 快照写入 JSON，并对 `project-structure`、`dependencies`、`errors` 这几个 topic 文件做更新，包含去重和条目上限控制，最后重建索引
- **存储形式**：在人类可读的 Markdown topic 文件和 JSON facts 快照之间组合存储，路径位于 `<projectRoot>/.frontagent/memory/`

**`packages/core/src/memory/index.ts`**

记忆模块的 barrel export 文件。

---

### 修改文件

**`packages/core/src/types.ts`**：

- 新增从 memory 模块引入的 `MemoryConfig` 类型
- 在 `AgentConfig` 中新增 `memory?: MemoryConfig`
- 在 `ContextInfo` 中新增 `memoryContext?: string`

**`packages/core/src/agent.ts`**：

- 新增 `MemoryStore` 和 `PersistenceInput` 的导入
- 新增 `memoryStore` 字段，并在构造函数中初始化
- **阶段 1**：新增 `preloadMemory()` 方法，用快照初始化 `ProjectFacts`，并将记忆内容加载到 `collectedContext.memoryContext`
- **阶段 3**：新增 `persistMemory()` 方法，用于提取新建文件、错误修复记录和依赖变更，然后调用 `memoryStore.persist()`；该流程在 `clearContext()` 之前执行，并且会完全吞掉所有错误
- 将 `getMemoryRecall` 回调接入 Executor，用于阶段 2
- 将 `memoryContext` 传给两次 planner 调用

**`packages/core/src/executor.ts`**：

- 在 `ExecutorConfig` 接口中新增 `getMemoryRecall`
- 将 `getMemoryRecall` 继续透传到 skill registry runtime

**`packages/core/src/skills/executor-skills.ts`**：

- 在 `ExecutorSkillRuntime` 接口中新增 `getMemoryRecall`
- `create_file` skill：在生成代码前，将召回的记忆注入上下文字符串
- `apply_patch` skill：在生成修改后代码前，将召回的记忆追加到 `changeDescription`

**`packages/core/src/skills/types.ts`**：

- 在 `PlannerContextSnapshot` 中新增 `memoryContext?: string`

**`packages/core/src/planner.ts`**：

- 在 planner 的 LLM prompt 中，把 `memoryContext` 作为一个独立区块注入

**`packages/core/src/context.ts`**：

- 将 `buildSystemPrompt()` 重构为三个清晰分区：
    1. **规则区（Rules zone）** —— SDD 约束
    2. **记忆区（Memory zone）** —— 跨会话持久知识
    3. **上下文区（Context zone）** —— 当前任务的动态数据（文件、步骤等）

**`packages/core/src/index.ts`**：

- 将 `MemoryStore` 以及所有 memory 相关类型加入包导出

---