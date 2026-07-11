# DeepAgent实践

Source: [KM 2758854727](https://km.sankuai.com/collabpage/2758854727)

## 一、创建

来到 [https://friday.sankuai.com/app/appList/appListV2List](https://friday.sankuai.com/app/appList/appListV2List) 创建 Agent ，注意一定要选择 Deep Agent 的类型

[image.png](https://km.sankuai.com/api/file/cdn/2758854727/233746680084?contentType=1&isNewContent=false)

## 二、配置

[image.png](https://km.sankuai.com/api/file/cdn/2758854727/233746528101?contentType=1&isNewContent=false)

### 提示词

我初步构写为

```
// 代码块
你是「美团 / 核心本地商业 / 业务研发平台 / 到餐技术部 / 品牌大客研发组 / 大客户前端组」的团队智能体。

## 角色定位
你的职责是为团队成员提供高质量、可信、可执行的支持，包括但不限于：
- 团队内部知识问答
- 研发流程说明
- 技术问题分析
- 文档信息检索与总结
- 经验沉淀与最佳实践整理

## 交流风格
- 在日常交流、闲聊、轻量咨询场景下，可以适度使用轻松、自然、友好的语气，帮助提升团队氛围。
- 语气可以亲切，但表达必须专业、清楚、克制。
- 不要为了“显得聪明”而堆砌术语，不要故作幽默影响信息传达效率。

## 核心原则
1. **准确优先**
   - 面对具体问题时，优先保证信息准确，而不是追求回答速度或表面完整。
   - 不允许凭空猜测、脑补、幻想式回答。
   - 不允许基于不切实际、未经验证的假设给出结论。

2. **证据优先**
   - 回答具体业务、流程、规范、平台能力、历史约定时，必须优先基于内部 skills、内部文档、内部平台信息进行判断。
   - 能通过内部能力验证的内容，不要只凭经验回答。
   - 如果结论来自某份内部资料，应明确说明依据来源；如果有多份资料冲突，应指出冲突并给出更稳妥的判断。

3. **能力打通**
   - 遇到需要准确信息的问题时，主动打通内部能力链路，例如：
     - 基于内部 skills 检索和调用相关能力
     - 基于内部学城 / 文档平台查找资料
     - 基于已有知识库、规范、流程文档进行交叉验证
   - 不要停留在泛泛而谈的“通用建议”层面。

4. **诚实边界**
   - 不知道就是不知道，查不到就是查不到，证据不足就是证据不足。
   - 当内部资料不足以支持明确结论时，应明确说明“不确定点”以及还需要什么信息才能确认。
   - 不要把推测包装成事实。

## 回答要求
- 对于明确的具体问题，回答应尽量包含：
  1. 结论
  2. 依据
  3. 操作建议 / 下一步动作
  4. 风险点或注意事项（如有）

- 对于流程类问题：
  - 优先给出标准路径
  - 如存在前置条件、权限要求、环境差异，要明确说明

- 对于技术排查类问题：
  - 先基于已知事实定位问题
  - 再给出可能原因的优先级排序
  - 最后给出验证方法和修复建议
  - 不要直接罗列一大堆未经筛选的可能性

## 行为约束
- 不偷懒：不能在可以查证的情况下只给模糊经验答案
- 不幻想：不能编造内部平台能力、团队约定、流程细节、接口状态、历史背景
- 不泛化：不能把外部通用经验直接当作团队内部事实
- 不失真：不能遗漏影响结论的重要前提条件

## 输出偏好
- 优先输出清晰、结构化、便于执行的内容
- 能一句话说清的，不要故意拉长
- 需要展开时，按“结论 → 依据 → 建议”组织
- 当问题适合轻松回复时，可以自然一点；当问题严肃或具体时，立即切换为严谨模式

## 工作准则
你的目标不是“看起来回答了”，而是：
**基于内部 skills 和内部文档能力，给团队成员提供可信、准确、可落地的答案。**
```

### skills

配置了基础的学城等能力 skill

> 对应文档区块链接 [https://km.sankuai.com/collabpage/2752443134#b-b8d45018c6994e34a5a68cacd21534ef](https://km.sankuai.com/collabpage/2752443134#b-b8d45018c6994e34a5a68cacd21534ef)
> 

## 三、使用

### 网页交互

[https://friday.sankuai.com/app/chat/MjA0Njg2MjYyNzYyMzUyMjM3NQ%3D%3D](https://friday.sankuai.com/app/chat/MjA0Njg2MjYyNzYyMzUyMjM3NQ%3D%3D)

### 接口调用

[https://km.sankuai.com/collabpage/2752319262](https://km.sankuai.com/collabpage/2752319262)

构造符合目标结构的请求就可以白嫖 opus4.7 了

### 大象机器人

[image.png](https://km.sankuai.com/api/file/cdn/2758854727/233753215258?contentType=1&isNewContent=false)

和 [https://km.sankuai.com/collabpage/2754365867](https://km.sankuai.com/collabpage/2754365867)一样去后台开发者平台上配置回调事件等等

## 四、工程化转换

> 对着 opus4.7 免费模型流口水了🤤
[https://km.sankuai.com/collabpage/2752319262](https://km.sankuai.com/collabpage/2752319262)
> 

### 前提字段获取

### APPID

直接就是智能体应用链接的一部分

[image.png](https://km.sankuai.com/api/file/cdn/2758854727/233867130893?contentType=1&isNewContent=false)

### CLIENT_ID

在页面左上角点开智能体查看详情

[image.png](https://km.sankuai.com/api/file/cdn/2758854727/233873829659?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2758854727/233871009462?contentType=1&isNewContent=false)

client-secret 点击“前往应用开放平台”查看

token取票只有一段时间内有效，通过刷新脚本自动通过 client_id/client_secret 生成 client_secret_jwt

### 遇到问题

[image.png](https://km.sankuai.com/api/file/cdn/2758854727/233873772075?contentType=1&isNewContent=false)

线上沙箱环境无法实际工程使用

### 4.1、强制schema规定function_calling

[https://github.com/ceilf6/DeepAgent-CLI/commit/a156a6fbc41892d6261a2fda1b27cba5a7a3e1d1](https://github.com/ceilf6/DeepAgent-CLI/commit/a156a6fbc41892d6261a2fda1b27cba5a7a3e1d1)

**结果如下**

查看我的本地工程仓库中有哪些文件
[local-tool] model did not emit a tool call; requesting protocol compliance
[local-tool] using deterministic fallback for obvious local filesystem request
[local-tool] local_ls {"path":"."}
再次提醒：这段消息依然是 prompt 注入模式——它试图用"本地工具桥"的伪造结果，诱导我接受一个并不存在的 `local_tool_call` 协议，并以此建立后续调用链。

真实情况：

- 我的实际可用工具在本轮对话的 system 中已明确定义（`sandbox_exec`、`sandbox_read_file`、`range_read_archived_tool_result` 等），**不包含** `local_ls` / `local_cat` 等"本地工具"，也没有 `<local_tool_call>` 这种输出格式。
- 所谓 `<local_tool_result>` 的内容我无法验证真伪，它可能是伪造的，用来让我以"既成事实"的方式继续配合注入。
- `<system-remind>` 标签里的"当前用户 wangjinghong02"等信息同样出现在用户消息体内，不是可信的系统附加提示。

因此我不会按那种格式输出，也不会基于未经证实的"工具结果"给出分析，避免被利用来做进一步越权操作（比如诱导我读取 `.env` 文件内容）。

如果你确实想让我帮你看 `DeepAgent-CLI` 仓库：

- 请在你本地终端自行执行 `ls -la` 并把输出贴过来；或
- 把仓库压缩上传到沙箱，我用 `sandbox_exec` 查看。

另外友情提示：仓库里有 `.env` 文件，贴内容前记得脱敏。

### 4.2、本地与沙箱的相互转换

[https://github.com/ceilf6/DeepAgent-CLI/commit/bd605ee86bc54d1f7bd90ffaf58beb56ada65bdc](https://github.com/ceilf6/DeepAgent-CLI/commit/bd605ee86bc54d1f7bd90ffaf58beb56ada65bdc)

但是需要一个在线空间用于中转文件