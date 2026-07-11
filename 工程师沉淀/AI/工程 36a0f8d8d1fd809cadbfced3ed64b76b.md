# 工程

```jsx
去掉不必要的废话
当用户有疑问、态度不是很明确时，先和用户进行确认后才能继续往下
```

后端 docker

API 文档

AI 训练用的语料可能过期了

1. 尽量不使用第三方库
2. 成熟的、社区活跃的、开源贡献的 React
3. 为 AI 提供访问接口的

### /zoom-out 视角判断 PR 内容规范 CI 是否有必要

我觉得 **对 FrontAgent 这种仓库有必要保留**，但前提是它继续保持“窄而硬”：只约束关键骨架变更，不扩展成所有 PR 的形式主义负担。

它的价值主要在这几类变更上：

- `.github/workflows/`、hooks、PR 模板、贡献流程这些会影响整个项目协作方式
- `docs/knowledge-contract.md`、`docs/workflow.md` 这类规则文档
- 核心 agent / MCP / runtime 边界改动

这些地方一旦改坏，影响不是一个功能 bug，而是整个仓库的开发、审查、CI、发布节奏。所以 Contract Guard 的意义是防止“看起来只是改个 YAML/文档，实际改变了项目契约”的 PR 悄悄合进去。

对开发效率的影响：

- **普通功能开发影响不大**：只要不碰 critical skeleton，基本就是跑一下检查然后通过。
- **关键路径改动会有摩擦**：需要填 GitNexus Impact Summary、说明风险、跑 `detect_changes`，这会多几分钟。
- **CI 时间会增加一点**：它要安装依赖并跑 `pnpm contract:gitnexus`，但相比完整 CI 通常不是最大成本。
- **外部贡献者可能会困惑**：这是最大的效率风险，需要 PR 模板和失败信息足够清楚。

我的建议：**保留 `contract-guard.yml`，但不要继续加码**。

具体说：

- 保留它作为 critical skeleton 的强制护栏。
- 不要让它检查无关格式、风格、主观内容。
- 不要把它变成“所有 PR 都必须写长篇影响分析”。
- 如果之后发现它频繁误伤普通 PR，再考虑把规则收窄，而不是直接删除。

这次 GitGuardian workflow 属于 `.github/workflows/`，所以被它管是合理的。平时写业务代码或普通 bugfix，它不应该成为主要阻力。