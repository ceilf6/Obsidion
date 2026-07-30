# ultracode

⏺ 已用 ultracode 跑了一轮多 Agent 研究：并行学习了当前 FrontAgent 仓库，以及 /Users/ceilf6/Desktop/code-tape 中可复用的 Harness
工程材料；同时专门做了一轮“训练营污染项”排除审查。结论如下。

推荐保存的工作流名称

Open-Source Harness Engineering Workflow / 开源社区 Harness 工程工作流

核心原则：

▎ 用轻量但可验证的 OSS Harness，把贡献过程约束为“有来源、有影响分析、有测试证据、有
▎ CI/Guard、有维护者判断”，但不引入训练营式认领、打分、进度榜、超时关闭或评论触发自动合并。

---

1. 范围与权威源确认

每个非平凡改动必须从明确上下文开始：

1. Issue、Discussion、PR 评论，或维护者明确批准的任务。
2. 先读权威文档，再读代码。
3. 如果文档冲突或预期行为不清楚，先问维护者，不要自行发明架构。

当前仓库的权威顺序是：

1. [README.md](http://readme.md/)：公开产品定位与命令说明。
2. docs/architecture.md、docs/design.md：架构与 SDD 行为。
3. [CONTRIBUTING.md](http://contributing.md/)、docs/workflow.md、docs/knowledge-contract.md：OSS 贡献、Harness、GitNexus 合约规则。
4. Issue / PR 文本。
5. 现有代码，只作为证据，不能覆盖上述文档。

证据：CLAUDE.md:3-10、CONTRIBUTING.md:56-66、docs/workflow.md:20-23。

Gate： scope、预期行为、验证方式不清楚时，不进入实现。

---

1. 分支与本地准备

推荐标准启动流程：

pnpm install
pnpm agent:bootstrap
pnpm quality:predev

然后从 develop 创建短生命周期分支：

feat/<topic>
fix/<topic>
docs/<topic>
chore/<topic>

含义：

- pnpm agent:bootstrap：安装 hooks，并打印本地工作流提示。
- pnpm quality:predev：安装 hooks 并运行本地 GitNexus contract check，刷新/检查代码智能上下文。
- 分支必须短小、聚焦、可独立 review。

证据：CONTRIBUTING.md:4-13、CONTRIBUTING.md:22-33、CLAUDE.md:21-30、package.json:20-30。

Gate： 没有安装依赖、bootstrap、predev 的情况下可以继续，但必须说明为什么不可行，以及后续补偿验证。

---

1. 改动前理解与 GitNexus Impact

对不熟悉的代码，优先使用 GitNexus 了解执行流，而不是直接 grep：

- 用 gitnexus_query 理解概念和流程。
- 用 gitnexus_context 看具体 symbol 的 caller / callee / 所属流程。
- 修改任何 function / class / method / symbol 前，必须先做 upstream impact。
- HIGH / CRITICAL 风险必须先明确告知用户或维护者。
- rename 不用 find-and-replace，必须用 GitNexus rename。

证据：CLAUDE.md:48-59、docs/workflow.md:38-43、docs/knowledge-contract.md:71-78。

Impact 记录至少包含：

- Risk level: LOW | MEDIUM | HIGH | CRITICAL
- Direct callers:
- Affected processes:
- Affected modules:
- Decision:

Gate： 没有 impact 分析，不改 symbol；HIGH / CRITICAL 风险不静默继续。

---

1. 最小可审查实现

实现阶段只做最小 reviewable diff：

1. 只改当前任务需要的文件。
2. 不做无关重构。
3. 不提交无关 generated / vendored / index-only churn。
4. 关键骨架改动必须带匹配测试。
5. 代码要遵守 FrontAgent 的核心工程边界：SDD、MCP-controlled execution、minimal diff、rollback、validation。

当前仓库的 Critical Skeleton 分类：

- agent-core
- sdd-workflow
- mcp-boundary
- memory-boundary
- repo-harness
- authority-docs

这些路径变更要求匹配测试和结构化 GitNexus PR summary。

证据：docs/knowledge-contract.md:21-32、scripts/workflows/contract-rules.mjs:11-89。

Gate： diff 一旦膨胀，应拆分 PR 或回到设计 / plan 阶段。

---

1. 本地验证分层

推荐验证梯度：

5.1 touched area focused tests

先跑和改动最相关的测试。

5.2 最低 final review gate

pnpm quality:precommit

它包含：

pnpm lint
pnpm typecheck
pnpm test
pnpm test:workflows

证据：package.json:27、CONTRIBUTING.md:14-20。

5.3 push 前推荐完整本地 gate

pnpm quality:local

它包含：

pnpm contract:local
pnpm quality:ci

其中 quality:ci 包含 lint、typecheck、test、workflow tests、build。

证据：package.json:27-29、CONTRIBUTING.md:15-20。

5.4 Hook bypass 只作紧急逃生

SKIP_QUALITY_HOOKS=1 只能是本地/紧急例外，CI 仍是权威。

证据：CONTRIBUTING.md:20-21。

Gate： 不带解释地跳过 quality:precommit，不应请求 final review。

---

1. Final diff GitNexus detect_changes

在 commit / PR final review 前运行：

gitnexus_detect_changes(scope: "all" 或对应 scope)

目标是确认：

- 实际 touched symbols 是否符合预期。
- affected execution flows 是否符合 scope。
- 有没有意外扩散。
- Critical skeleton 是否需要 PR impact summary。

证据：CLAUDE.md:18-19、docs/knowledge-contract.md:71-78。

Gate： detect_changes 发现非预期流程时，先调查或补测试，不直接提交。

---

1. PR 准备

PR 目标分支：develop。

PR 必须包含：

1. Linked issue / discussion / standalone context。
2. Summary。
3. Impact scope。
4. GitNexus Impact Summary。
5. Verification。
6. Focused diff checklist。
7. Gates checklist。

Critical skeleton PR 的 GitNexus Impact Summary 不能写 placeholder，必须是结构化内容：

## GitNexus Impact Summary

- Risk level: LOW|MEDIUM|HIGH|CRITICAL
- Critical skeleton changes: ...
- GitNexus impact: detect_changes ... query/context/impact ...
- Verification: ...

Contract Guard 会要求 GitNexus impact 同时提到：

- detect_changes
- 以及 query / context / impact 之一

证据：docs/knowledge-contract.md:34-58、scripts/workflows/contract-rules.mjs:178-211。

Gate： Critical skeleton PR 没有匹配测试或结构化 impact summary，不能视为 ready。

---

1. CI、Guard 与 Review

合并前等待：

- GitHub Actions / CI
- Contract Guard
- Repo Guard
- Codex / Copilot review comments
- Maintainer review

角色划分：

- CI 和 Contract Guard：最低机器检查。
- Repo Guard / Codex / Copilot：辅助 review 信号。
- 维护者：最终 merge readiness 决策者。

证据：docs/workflow.md:45-49、CLAUDE.md:31-33、CONTRIBUTING.md:67-69。

Gate： 不使用评论触发自动合并；不让 AI reviewer 取代维护者判断。

---

1. Harness 自身维护规则

如果改的是 Harness 本身，例如：

- .github/workflows/
- .github/PULL_REQUEST_TEMPLATE.md
- .github/CODEOWNERS
- .githooks/
- scripts/workflows/
- [README.md](http://readme.md/)
- [AGENTS.md](http://agents.md/)
- [CLAUDE.md](http://claude.md/)
- [CONTRIBUTING.md](http://contributing.md/)
- docs/workflow.md
- docs/knowledge-contract.md

则必须同步考虑：

1. docs 是否更新。
2. package scripts 是否仍是唯一命令入口。
3. workflow YAML 是否只是调用 package script，而不是复制逻辑。
4. scripts/tests/ 是否覆盖规则。
5. .gitnexus/lbug / .gitnexus/meta.json 是否只是本地刷新漂移，不能误提交。

证据：docs/knowledge-contract.md:25-32、docs/knowledge-contract.md:60-69、package.json:20-30、scripts/workflows/contract-rules.mjs:66-88
。

Gate： Harness policy 变更必须 docs、scripts、tests 同步。

---

明确不引入的 code-tape 训练营机制

从 /Users/ceilf6/Desktop/code-tape 学习时，保留中性的 Harness 工程实践，但排除训练营机制。

保留

- 本地 quality scripts。
- CI / Contract Guard。
- Issue / PR 模板中的背景、目标、验收标准。
- GitNexus impact summary。
- 文档优先、SDD、TDD、review、质量门禁。
- Hooks + package scripts 作为统一入口。

code-tape 中类似证据包括：

- package.json:12-19 的 neutral scripts。
- .github/workflows/workflow-tests.yml:1-35 的标准 CI。
- .github/workflows/contract-guard.yml:1-30 的 PR Contract Guard。
- scripts/workflows/contract-rules.mjs:79-158 的 critical surface / summary 校验。
- .github/PULL_REQUEST_TEMPLATE.md:13-28 的 impact + self-check。

排除

不要带入：

- 认领 / claim comments。
- score labels / 分数 / 排行。
- progress ledger。
- cohort progress reporting。
- 私有群播报。
- GitHub ID 到真实姓名映射。
- timeout-close 自动关闭。
- 评论触发自动合并。
- CR通过 这类魔法评论。
- reviewer ownership / review 得分。
- 对 fork PR 使用 write token 执行不可信代码。

code-tape 里这类训练营证据包括：

- README.md:21-22 的自动打分和群进度通知。
- skills/progress-reporter/SKILL.md:1-4、:133-143 的进度报告和飞书群发送。
- skills/progress-reporter/references/name-mapping.md:1-11 的 GitHub ID 到姓名映射。
- docs/规范工作流程.md:204-205 的 CR 计分逻辑。

---

可直接保存成 workflow 的精简版

你后续用 /workflows + s 保存时，我建议核心 prompt 可以压缩成这样：

Run the FrontAgent OSS Harness workflow.

Scope:

- This is an open-source community workflow, not a training-camp workflow.
- Do not use claim comments, score labels, progress ledgers, timeout-close automation, private cohort reporting, or comment-triggered
auto-merge.

Phases:

1. Confirm scope and authority:
    - Start from issue/discussion/PR/maintainer-approved task.
    - Follow authority order: README; docs/architecture.md and docs/design.md; [CONTRIBUTING.md](http://contributing.md/), docs/workflow.md,
    docs/knowledge-contract.md; issue/PR text; existing code.
    - Ask maintainers if docs conflict.
2. Bootstrap:
    - Use branch from develop: feat/, fix/, docs/, or chore/.
    - Run pnpm install when needed.
    - Run pnpm agent:bootstrap and pnpm quality:predev when feasible.
3. Pre-change intelligence:
    - Use GitNexus query/context for unfamiliar flows.
    - Before editing any symbol/function/class/method, run upstream GitNexus impact.
    - Report risk, direct callers, affected processes, and modules.
    - Warn before HIGH/CRITICAL risk.
    - Use GitNexus rename for symbol renames.
4. Implement:
    - Make the smallest independently reviewable change.
    - Avoid unrelated refactors and generated/index-only churn.
    - For critical skeleton changes, add matching tests.
5. Verify:
    - Run focused tests for touched areas.
    - Run pnpm quality:precommit before final review at minimum.
    - Run pnpm quality:local before pushing when feasible.
    - Explain skipped gates.
6. Final impact:
    - Run GitNexus detect_changes on final diff.
    - Confirm affected symbols/flows match intended scope.
    - Investigate unexpected scope.
7. PR:
    - Open PR to develop.
    - Fill template with linked context, summary, impact scope, verification, focused diff, and gates.
    - For critical skeleton changes, fill GitNexus Impact Summary with risk level, critical skeleton changes, detect_changes plus
    query/context/impact, and verification.
8. Review:
    - Wait for CI, Contract Guard, Repo Guard, Codex/Copilot, and maintainer comments.
    - Treat Repo Guard and AI comments as advisory.
    - Address actionable review comments with follow-up commits and rerun relevant gates.
    - Maintainers decide merge readiness.
9. Harness maintenance:
    - If changing workflows, hooks, contract scripts, templates, authority docs, or package scripts, update docs + scripts + tests
    together.
    - Keep workflow YAML thin by invoking package scripts.
    - Do not commit .gitnexus seed-index drift unless explicitly in scope.

---

我建议采用的工作流形态

三种方案中，推荐第二种：

1. 纯文档 advisory workflow：轻，但约束太弱。
2. 分层 OSS Harness + critical-surface Contract Guard：推荐。普通贡献保持轻量，关键骨架变更强制证据和测试。
3. 全自动治理 workflow：不推荐，容易滑向训练营式自动化和模板表演。

最终建议：
保持 OSS 轻量贡献体验，但对 critical skeleton、GitNexus impact、质量门禁、PR evidence 做强约束；所有 merge 决策仍交给维护者。