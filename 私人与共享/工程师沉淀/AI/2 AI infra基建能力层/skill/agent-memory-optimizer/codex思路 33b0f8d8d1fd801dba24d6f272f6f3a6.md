# codex思路

我借鉴的不是 Claude Code 的“某一个记忆文件格式”，而是它把记忆做成**时间分层上下文系统**的方式。这个抽象最后被我落进了 [SKILL.md](https://www.notion.so/Users/ceilf6/.codex/skills/agent-memory-optimizer/SKILL.md)、[claude-code-memory-patterns.md](https://www.notion.so/Users/ceilf6/.codex/skills/agent-memory-optimizer/references/claude-code-memory-patterns.md) 和 [audit-checklist.md](https://www.notion.so/Users/ceilf6/.codex/skills/agent-memory-optimizer/references/audit-checklist.md)。

**我借鉴的核心内容**

- **四阶段时间主线**：这是最核心的借鉴。Claude Code 的记忆不是“一个库”，而是分成启动前预装、对话中动态补充、回合结束后持久化、compact 时连续性续航四段。我把这直接变成了 skill 的总纲和审计框架。来源主要是 [claudemd.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/utils/claudemd.ts)、[extractMemories.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/services/extractMemories/extractMemories.ts)、[sessionMemory.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/services/SessionMemory/sessionMemory.ts)、[sessionMemoryCompact.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/services/compact/sessionMemoryCompact.ts)。
- **规则与内容分离**：Claude Code 把“怎么使用记忆”与“记忆内容本身”分成两条链，我把这个抽象成 skill 里的第一条升级建议：先拆 instruction memory 和 memory content。来源是 [prompts.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/constants/prompts.ts) 的 `loadMemoryPrompt()` 与 [context.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/context.ts#L155) / [claudemd.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/utils/claudemd.ts#L1153) 的内容注入链。
- **启动前的装配线思维**：不是“读几个文件”，而是 `发现 -> 加工 -> 排序 -> 注入`。我把这变成 skill 里“先画现状图，再动架构”的方法论。来源是 [getMemoryFiles](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/utils/claudemd.ts#L790)、[processMemoryFile](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/utils/claudemd.ts#L618)、[getClaudeMds](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/utils/claudemd.ts#L1153)。
- **运行中的双通道 recall**：Claude Code 不是只靠语义召回，它同时有“按用户问题”的 relevant memories 和“按当前文件路径”的 nested memory。我把这抽象成 skill 里的 runtime surfacing 设计原则。来源是 [findRelevantMemories.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/memdir/findRelevantMemories.ts)、[attachments.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/utils/attachments.ts#L2203)、[attachments.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/utils/attachments.ts#L1792)。
- **回合结束后的反向持久化链**：这是 skill 里“post-turn extraction”那一整块的直接来源。特别借鉴了：后台执行、只看新增消息、cursor、manifest、防重复、coalescing、主线程直写则跳过。来源是 [stopHooks.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/query/stopHooks.ts#L141) 和 [extractMemories.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/services/extractMemories/extractMemories.ts#L329)。
- **durable memory 和 session memory 分家**：这点对 skill 很关键。Claude Code 把“跨会话长期记忆”和“当前会话工作笔记”拆开，我把它变成了 skill 里的高优先级结构建议。来源是 [extractMemories.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/services/extractMemories/extractMemories.ts) 对 durable memory 的写回，以及 [sessionMemory.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/services/SessionMemory/sessionMemory.ts) 对 session notes 的维护。
- **用 session memory 支撑 compact**：我在 skill 里明确强调“不要等上下文快满了才临时总结”，这是直接借鉴 Claude Code 的 session-memory-backed compaction。来源是 [sessionMemoryCompact.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/services/compact/sessionMemoryCompact.ts#L514)。
- **索引 + topic files，而不是一个大文件**：我在 skill 里反复强调 entrypoint index + topic files，这来自 Claude Code 的 `MEMORY.md` 入口 + 主题文件模式。来源是 [memdir.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/memdir/memdir.ts) 和 [memoryScan.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/memdir/memoryScan.ts)。

**我借鉴的工程约束**

- **预算意识**：递归深度、entrypoint 截断、surfacing 数量限制、compact 保留窗口，这些都被我抽象成 skill 里的“先加 guardrail，再开自动写入”。来源是 [claudemd.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/utils/claudemd.ts)、[memdir.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/memdir/memdir.ts)、[sessionMemoryCompact.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/services/compact/sessionMemoryCompact.ts)。
- **best-effort + fallback**：Claude Code 很多 memory 流程都不阻塞主线，失败就降级。我把这变成 skill 里的设计原则。典型来源是 turn-end extraction 的 fire-and-forget 和 session memory compact 失败后 fallback 到传统 compact。[extractMemories.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/services/extractMemories/extractMemories.ts) [compact.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/commands/compact/compact.ts#L55)
- **subagent 隔离**：我在 skill 里写“默认隔离 subagent memory，除非明确设计共享作用域”，这是借鉴了 Claude Code 里主 memory、agent memory、subagent 责任边界的分离。来源是 [agentMemory.ts](https://www.notion.so/Users/ceilf6/Desktop/claude-code/src/tools/AgentTool/agentMemory.ts) 和 turn-end extraction 只跑主线程的逻辑。

**我刻意没有照搬的东西**

- 没有照搬 `CLAUDE.md`、`MEMORY.md`、`TeamMem`、`AutoDream`、feature flag 名字这些 repo 私有实现细节。
- 没有把 Claude Code 的 typed memory taxonomy 原样塞进 skill，因为别的智能体项目未必适用。
- 没有把 skill 写成“复刻 Claude Code”，而是写成“把 Claude Code 的架构模式抽象成可迁移的方法论”。

所以更准确地说，这个 skill 借鉴的是 Claude Code 的三层东西：

- **心智模型**：记忆要按时间阶段理解。
- **架构模式**：静态预装、动态 surfacing、后台持久化、session continuity。
- **工程原则**：分层、去重、预算、隔离、回退。

如果你愿意，下一步我可以继续把这份 skill 的借鉴关系整理成一张“Claude Code 机制 -> skill 中对应原则”的对照表。