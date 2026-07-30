# claude-mem

实现跨 session 记忆

对，**它本质上更像一个“CLI/本地服务 + hooks + MCP 工具”的记忆系统**，不只是一个单纯命令行工具。

可以拆成几层理解：

**1. 安装/管理入口是 CLI**

它有 `npx claude-mem install` 这类安装命令。官方安装文档还特别说明，单纯 `npm install -g claude-mem` 只是装 SDK/library，不会自动注册 hooks 或启动 worker；正确方式是通过 `npx claude-mem install` 或插件命令安装。([Claude-Mem](https://docs.claude-mem.ai/installation?utm_source=chatgpt.com))

**2. 后台有 worker service**

安装后它会启动一个本地 worker 服务，负责接收 hooks 发来的会话事件、工具调用结果、用户 prompt 等，然后做存储、摘要、检索。也就是说 CLI 只是入口，真正长期运行的是本地服务。([Claude-Mem](https://docs.claude-mem.ai/installation?utm_source=chatgpt.com))

**3. 通过 hooks 自动记录 Claude Code 的 session**

它会接入 Claude Code 的生命周期，比如 session 开始、用户提交 prompt、工具调用后、session 结束等时机，把观察结果和上下文发给 worker。相关介绍里提到它会自动配置 hooks，并且新开 Claude Code session 时会加载之前 session 的上下文。([Claude-Mem](https://docs.claude-mem.ai/installation?utm_source=chatgpt.com))

**4. 通过 MCP / mem-search 给模型读取记忆**

你的理解基本对：它不是简单把所有历史都塞回 prompt，而是把历史压缩、入库，然后通过搜索工具让 agent 读取相关记忆。资料里提到它会把 sessions、observations、summaries 存起来，并提供搜索工具/上下文加载能力，让未来 session 可用。([GitHub](https://github.com/thedotmack/claude-mem/blob/main/README.md?utm_source=chatgpt.com))

不过这里的 “skill” 要看你怎么定义：

如果你说的是 **Claude Code / OpenCode / Codex CLI 这类 agent 能调用的工具能力**，那可以类比成一个“记忆 skill”或“记忆插件”：模型在需要时通过 MCP/search 工具查询历史记忆。

如果你说的是 **ChatGPT Skills** 那种 `.skill` 包，claude-mem 本身不是这个格式；它更偏向 **MCP + hooks + 本地数据库 + worker** 的架构。

更准确的流程大概是：

```
Agent/CLI 会话
  ↓ hooks 捕获
本地 worker service
  ↓ 压缩/摘要
SQLite + Chroma/索引
  ↓ 检索
MCP/search 工具
  ↓
下次 session 注入相关记忆给大模型
```

所以一句话：**是 CLI 生态里的持久记忆插件/服务；它会记录和压缩 session，再通过上下文注入或 MCP 搜索工具让大模型读取记忆。**