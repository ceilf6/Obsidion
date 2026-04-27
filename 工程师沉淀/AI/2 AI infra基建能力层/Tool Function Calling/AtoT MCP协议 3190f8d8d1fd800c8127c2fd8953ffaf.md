# AtoT MCP协议

Agent to **Tool**

有时候可以间接实现 AtoA 因为一个 Agent 可以被封装成一个 MCP Tool

核心是让 LLM / Agent 可以标准化地访问外部工具、数据源和环境

如果没有 MCP， LLM不知道如何访问外部世界，每个工具都需要写一套适配

有了 MCP，所有工具都能统一通过MCP接入

```json
Agent: 大模型
  ↓
MCP Client: Agent侧SDK
  ↓
MCP Server: 工具提供方
  ↓
Tool / Data: 实际能力
```

```json
┌─────────────┐
│    Agent    │
│  (Claude)   │
└──────┬──────┘
       │
       │ JSON-RPC
       │
┌──────▼──────┐
│ MCP Client  │
└──────┬──────┘
       │
       │ transport
       │
┌──────▼──────┐
│ MCP Server  │
└──────┬──────┘
       │
       │
 ┌─────▼─────┐
 │   Tools   │
 └───────────┘
```

# **MCP 的通信协议**

MCP 使用：**JSON-RPC** 2.0

通信结构：

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "tools/list",
  "params": {}
}
```

返回：

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {...}
}
```

---

# **MCP 的三大能力**

MCP 定义了三类资源：

### **1 Tools**

工具调用。

例如：

```
read_file
search_code
run_test
open_browser
```

示例：

```
{
  "name": "read_file",
  "description": "Read file content",
  "input_schema": {
    "type": "object",
    "properties": {
      "path": {
        "type": "string"
      }
    }
  }
}
```

---

### **2 Resources**

资源访问。

例如：

```
filesystem
database
git repo
web page
```

示例：

```
repo://frontend/src/App.tsx
```

---

### **3 Prompts**

预定义 prompt 模板。

例如：

```
code_review_prompt
generate_test_prompt
```

---

# **MCP Tool 调用流程**

完整流程：

### **1 Agent 获取工具列表**

```
tools/list
```

返回：

```
read_file
write_file
search
```

---

### **2 Agent 决策调用**

LLM 推理：

```
需要读取文件
```

---

### **3 Agent 调用 Tool**

请求：

```
{
  "method": "tools/call",
  "params": {
    "name": "read_file",
    "arguments": {
      "path": "src/index.ts"
    }
  }
}
```

---

### **4 MCP Server 执行**

```
read_file()
```

---

### **5 返回结果**

```
{
  "content": "file content..."
}
```

---

### **6 Agent 继续推理**

LLM 使用结果继续推理。

---

# **MCP Transport 通信**

MCP 支持多种通信方式：

| **方式** | **场景** |
| --- | --- |
| stdio | 本地工具 |
| HTTP | 远程服务 |
| WebSocket | 实时服务 |

例如：

```
Claude Desktop
    ↓
stdio
    ↓
Local MCP Server
```

---

# **MCP Server 示例**

一个简单 MCP server：

Node.js 示例：

```jsx
import { MCPServer } from "@modelcontextprotocol/sdk";

const server = new MCPServer({
  name: "filesystem"
});

server.tool(
  "read_file",
  {
    path: "string"
  },
  async ({ path }) => {
    return await fs.readFile(path, "utf8");
  }
);

server.start();
```

---

# **MCP 生态里的常见 Server**

常见 MCP server：

### **filesystem**

读写本地文件。

---

### **github**

访问 GitHub：

```
search repo
read issue
create PR
```

---

### **browser**

浏览网页。

---

### **database**

SQL 查询。

---

### **codebase**

代码搜索。

---

# **MCP 与 Function Calling 的区别**

很多人会混淆。

### **OpenAI Function Calling**

```
LLM → function
```

是 **API 层能力**。

---

### **MCP**

```
Agent → Tool Server
```

是 **系统级协议**。

对比：

| **特性** | **Function Calling** | **MCP** |
| --- | --- | --- |
| 协议 | OpenAI API | 独立协议 |
| 工具 | 内嵌 | 外部 |
| 跨应用 | 否 | 是 |
| 生态 | 小 | 正在形成 |

---

# **MCP 在 Agent 系统中的作用**

典型 AI Agent 架构：

```
Agent
  ↓
Planner
  ↓
Tool Use
  ↓
Memory
```

其中：

```
Tool Use
```

就是 MCP。

完整结构：

```
Agent
 ├ Memory
 ├ Planning
 ├ MCP Tool Access
 └ RAG
```

---

# **为什么 MCP 很重要**

MCP 解决的是：

> **AI应用的 USB-C**
> 

就像：

```
USB-C
  ↓
统一设备接口
```

MCP：

```
AI
 ↓
统一工具接口
```

所以 MCP 的目标是：

```
AI Tool Standard
```

---

# **MCP 在多 Agent 系统中的角色**

MCP 本质是：

```
Agent → Tool
```

但有时：

```
Agent B
```

可以被包装成：

```
Tool
```

例如：

```
DevAgent
   ↓
call tool "review_code"
   ↓
ReviewAgent
```

所以在某些架构中：

```
A → MCP → B
```

看起来像 A→A。

---

# **结合你做的 FrontAgent**

如果你现在做：

```
FrontAgent
```

非常适合 MCP。

你可以做：

```
FrontAgent
  ↓
MCP Tools
```

例如：

```
read_repo
search_component
run_playwright
lint_code
score_code
```

评分 Agent 也可以变成：

```
score_code_tool
```

---

# **未来 AI 系统的典型结构**

未来 AI 软件架构基本是：

```
User
  ↓
Agent
  ↓
Planner
  ↓
MCP Tools
  ↓
External Systems
```

其中：

```
Planner → reasoning
MCP → execution
```

---

如果你愿意，我可以再给你详细讲一个 **非常关键但很多人不知道的东西：**

**MCP + Multi-Agent + Workflow Engine 的完整架构**（也是现在 Cursor / Claude Code / Devin 类产品的核心架构）。