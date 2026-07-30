# FrontAgent MCP Server v1 技术方案

## Summary

- 新增 `fa mcp serve`，把 FrontAgent 作为本地 stdio MCP Server 暴露给 Claude/Cursor/Codex 等 MCP Host。
- 只暴露 FrontAgent 上层能力，不暴露内部 file/web/shell/RAG 底层工具。
- LLM 后端采用 `auto`：优先使用 **MCP Sampling 调用 Host 模型**；Host 不支持时回退 FrontAgent 自有 LLM 配置。
- 默认沿用 `balanced` 写入策略；需审批动作一律 fail-closed，因为 stdio MCP v1 不提供交互审批 UI。

## Key Changes

- 先修复运行时前置问题：补齐 `packages/runtime-node/src/config.ts`，恢复 `runFrontAgentTask` 的配置解析；缺依赖时允许执行 `pnpm install`。
- 在 runtime 增加 MCP server 启动模块，CLI 增加：
    - `fa mcp serve --project-root <path>`
    - 默认 `projectRoot=process.cwd()`，服务只绑定一个项目根目录。
- 暴露 6 个 MCP tools：
    - `frontagent_status`：返回项目、SDD、skills、LLM backend、RAG、日志状态。
    - `frontagent_run_task`：执行完整 FrontAgent 任务，输入 `task/type/files/url/sddPath/securityMode`。
    - `frontagent_plan_task`：只生成执行计划，不执行、不写文件。
    - `frontagent_validate_sdd`：校验 SDD。
    - `frontagent_list_skills`：列出可见内容技能。
    - `frontagent_init_sdd`：初始化 SDD；已存在时默认失败，只有显式 `force=true` 才覆盖。
- 新增 LLM backend 抽象：
    - `sampling` backend 通过 MCP `sampling/createMessage` 请求 Host 模型。
    - `direct` backend 复用现有 OpenAI/Anthropic 配置。
    - `auto` 先检查/尝试 sampling，失败或不支持时回退 direct。
- `frontagent_run_task` 返回结构化 JSON 文本：`success/taskId/output/error/duration/runLogPath/executedStepsSummary/securityDecisions`。
- `frontagent_plan_task` 需要抽出 plan-only runtime 路径：执行上下文收集、skills/RAG/SDD 注入和 Planner，但不调用 Executor。

## Safety

- 外部 Host 不能直接调用 `read_file/apply_patch/run_command/browser_* /rag_query`。
- FrontAgent 内部仍可调度这些工具，但所有写入、shell、浏览器外部动作继续经过 `SecurityManager`。
- MCP v1 审批策略固定 fail-closed：任何 `ask` 决策都返回拒绝结果，不阻塞等待用户输入。
- `frontagent_init_sdd` 只允许写入项目根目录内的 SDD 文件。

## Test Plan

- `frontagent_status/list_skills/validate_sdd/init_sdd` 在无 LLM 配置下可用。
- `frontagent_run_task/plan_task` 在 Host 支持 sampling 时不读取 API key。
- sampling 不可用时自动回退 direct；direct 配置缺失时返回明确配置错误。
- 敏感写入、依赖文件覆盖、shell install 等需要审批的动作在 MCP 模式下 fail-closed。
- smoke test：通过 stdio JSON-RPC 启动 `fa mcp serve`，验证 `tools/list` 和每个 tool 的基础调用。
- 回归验证：`pnpm --filter @frontagent/runtime-node typecheck`、相关 runtime/CLI tests、根 `pnpm build`。

## Assumptions

- v1 只做 stdio，不做远程 HTTP。
- v1 不暴露内部底层工具。
- v1 默认允许 balanced 模式下的普通项目内写入。
- MCP 设计依据：Server 暴露 tools/resources/prompts，Host 负责模型编排；Sampling 用于 Server 请求 Host LLM。参考 [MCP Architecture](https://modelcontextprotocol.io/specification/2025-06-18/architecture) 和 [MCP Sampling](https://modelcontextprotocol.io/specification/2025-06-18/client/sampling)。