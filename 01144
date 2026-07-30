# openspec

可以这么理解：**像 Superpowers 一样，先和 agent 对话澄清疑惑点；但 OpenSpec 的关键不是“聊完就行”，而是把澄清结果沉淀成仓库里的结构化文档。**

OpenSpec 官方的默认流程是：

```
/opsx:propose → /opsx:apply → /opsx:sync → /opsx:archive
```

扩展流程是：

```
/opsx:new → /opsx:ff 或 /opsx:continue → /opsx:apply → /opsx:verify → /opsx:archive
```

它会在仓库里维护 `openspec/specs/` 和 `openspec/changes/`：前者是当前系统行为的 source of truth，后者是每次变更的提案、设计、任务和 delta spec。([GitHub](https://github.com/Fission-AI/OpenSpec/blob/main/docs/getting-started.md))

## 最常用做法

先安装并初始化：

```bash
npm install -g @fission-ai/openspec@latest
cd your-repo
openspec init --tools claude,codex,cursor
```

`openspec init` 会创建 `openspec/specs/`、`openspec/changes/`、`openspec/config.yaml`，并为你选择的 AI 工具生成对应配置。([GitHub](https://github.com/Fission-AI/OpenSpec/blob/main/docs/cli.md)) OpenSpec 目前支持 Claude Code、Cursor、Codex、Copilot、Gemini CLI、Windsurf 等工具。([openspec.dev](https://openspec.dev/))

然后在 agent 里说：

```
/opsx:propose add-user-profile-filter
```

或者更推荐你这样写：

```
请为“用户资料列表增加按角色和团队筛选”创建一个 OpenSpec change proposal。

在生成文档前，请先：
1. 阅读当前仓库相关代码和已有 openspec/specs
2. 列出需求中的不确定点
3. 先不要实现代码
4. 等我确认后，再生成 proposal.md、design.md、tasks.md 和 delta spec
```

生成后通常会有这些文件：

```
openspec/changes/add-user-profile-filter/
├── proposal.md      # 为什么做、做什么、范围
├── design.md        # 怎么做，技术方案
├── tasks.md         # 实现 checklist
└── specs/
    └── profile/
        └── spec.md  # ADDED / MODIFIED / REMOVED requirements
```

官方说明里，`proposal.md` 负责 why/what，`specs/` 是需求变更 delta，`design.md` 是技术方案，`tasks.md` 是实现清单，并且这些 artifact 是可以在实现过程中继续回改的。([GitHub](https://github.com/Fission-AI/OpenSpec/blob/main/docs/getting-started.md))

## 所以它和 Superpowers 的区别

**相同点：**

你确实可以像和 Superpowers 对话一样，让 agent 先问你疑惑点，例如边界条件、交互细节、接口约束、兼容性、验收标准等。这个阶段很重要。

**不同点：**

OpenSpec 更强调“落文件 + 可审查 + 可验证”。也就是说，不应该只停留在聊天上下文里，而要把最终共识写进：

```
proposal.md
spec.md
design.md
tasks.md
```

这样后面 `/opsx:apply` 实现时，agent 不是凭刚才聊天记忆写代码，而是基于 repo 里的 spec artifacts 写代码。

## 建议你的实际工作流

你可以按这个节奏用：

```
第一步：让 agent 探索代码 + 提疑问
第二步：你回答疑问，确定边界
第三步：让 agent 生成 OpenSpec proposal
第四步：你 review proposal/spec/design/tasks
第五步：通过后再 /opsx:apply 实现
第六步：实现完 /opsx:sync 或 /opsx:archive
```

检查文档是否规范可以用：

```bash
openspec list
openspec show add-user-profile-filter
openspec validate add-user-profile-filter --strict
openspec view
```

`openspec list/show/validate/view` 是官方用于浏览、查看和校验 specs/changes 的命令。([GitHub](https://github.com/Fission-AI/OpenSpec/blob/main/docs/cli.md))

## 你可以直接复用的提示词

```
请使用 OpenSpec 工作流帮我规划这个需求：{需求描述}

要求：
1. 先不要写代码
2. 先阅读相关代码、已有 specs、README 和测试
3. 先列出需求不明确的地方，并给出你的默认假设
4. 等我确认后，再创建 openspec/changes/{change-name}
5. 产物需要包含：
   - proposal.md：背景、目标、范围、非目标
   - specs/{domain}/spec.md：ADDED/MODIFIED/REMOVED Requirements，每个 Requirement 至少有 Scenario
   - design.md：技术方案、数据流、兼容性、风险
   - tasks.md：可执行 checklist
6. spec 只写可验证的外部行为，不要把具体函数名/类名泄露到 requirement 里；实现细节放到 design.md 或 tasks.md
```

最后一句很关键：OpenSpec 官方约定里，spec 应该描述可验证的行为契约，避免把具体库、函数结构、执行细节写进 behavior requirements；这些应放到 `design.md` 或 `tasks.md`。([GitHub](https://github.com/Fission-AI/OpenSpec/blob/main/openspec/specs/openspec-conventions/spec.md))

所以结论是：**是的，使用体验上可以像 Superpowers 一样先和 agent 澄清；但 OpenSpec 的核心价值是把澄清后的共识固化成可 review、可 validate、可 archive 的 spec 文档，而不是只靠对话上下文。**