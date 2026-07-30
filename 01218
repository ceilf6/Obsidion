# Clean Architecture（整洁架构）

https://github.com/ceilf6/Lab/commit/8b0e6a73df51f4a05de163aa5b826c97eb1f28a2

我认为本质上就是“把**依赖倒置原则**（DIP）放大到整个系统层面”

整洁架构的核心，不是把代码分很多文件夹，而是把“业务规则”和“实现细节”隔离开，并强制依赖方向只向内。

**核心思想**

- **最内层放最稳定**的东西：业务概念、业务规则、用例。
- 最外层放最容易变化的东西：HTTP、数据库、UI、第三方库。
- 依赖规则只有一条：**外层可以依赖内层，内层不能依赖外层**。
- 所以，数据库怎么存、接口怎么传、框架怎么写，**不能反过来污染核心业务**。

### **分层（Layers）**

系统被分成几层，从内到外：

```
[ Entities / domains ]        ← 核心业务规则
[ Use Cases / application ]       ← 业务逻辑
[ Interface Adapters ] ← 控制器 / Presenter / Gateway
[ Frameworks & Drivers / infrastructure / composition root] ← 数据库 / UI / Web
```

如果一句话概括，就是：**让业务逻辑独立于框架和基础设施存在**。

**在你这个示范里的体现**

1. 核心业务规则 - 领域**实体**在 [Order.ts](https://www.notion.so/Users/a86198/Desktop/Lab/Pattern/Architecture-Pattern/Clean-Architecture/ex/domain/Order.ts#L7)。这里负责订单最核心的规则，比如 `customerId` 必填、商品不能为空、数量必须大于 0、总价怎么计算。它**不关心 HTTP，不关心数据库**。
2. 业务逻辑：
    - 应用层用例在 [CreateOrderUseCase.ts](https://www.notion.so/Users/a86198/Desktop/Lab/Pattern/Architecture-Pattern/Clean-Architecture/ex/application/CreateOrderUseCase.ts#L14)。它负责“创建订单”这件**业务流程逻辑**：接收命令、创建实体、调用仓储保存、返回结果。它知道“要保存订单”，但不知道“怎么保存”。
    - 仓储抽象在 [OrderRepository.ts](https://www.notion.so/Users/a86198/Desktop/Lab/Pattern/Architecture-Pattern/Clean-Architecture/ex/application/ports/OrderRepository.ts)。这就是端口（port）。应用层只依赖这个接口，不依赖 MySQL、Prisma、Map。
3. 接口适配层：在 [CreateOrderController.ts](https://www.notion.so/Users/a86198/Desktop/Lab/Pattern/Architecture-Pattern/Clean-Architecture/ex/interface-adapters/CreateOrderController.ts#L16)。它把 HTTP 风格的输入输出，翻译成用例需要的命令和结果。`statusCode`、错误消息这些都留在这一层，不进入用例。
4. 最外层 - 具体实现：
    - 基础设施实现放在 [InMemoryOrderRepository.ts](https://www.notion.so/Users/a86198/Desktop/Lab/Pattern/Architecture-Pattern/Clean-Architecture/ex/infrastructure/InMemoryOrderRepository.ts)。这里才是真正的“**实现细节**”。今天用内存，明天换 MySQL，只需要换这一层。
    - 依赖装配在 [Client.ts](https://www.notion.so/Users/a86198/Desktop/Lab/Pattern/Architecture-Pattern/Clean-Architecture/ex/Client.ts#L5)。这里手动把 `Repository -> UseCase -> Controller` 连起来。整洁架构里，这种“把具体实现注入进去”的工作，通常都放在最外层。

**实际写代码时的规则**

- `domain` 和 `application` 不要直接 import `express`、`axios`、`prisma`、`mongoose` 之类的外部实现。
- 用例层依赖接口，不依赖具体类。
- 控制器只做“协议转换”和简单错误映射，不写核心业务。
- 实体负责业务不变量，用例负责业务流程，基础设施负责技术实现。
- 如果换数据库、换 Web 框架，理想情况下只改外层，不改核心业务层。

你可以把它理解成一个同心圆：

- 中心是“业务为什么这样做”
- 外围是“技术上怎么做”

前者应该稳定，后者应该可替换。

如果你愿意，我可以下一步把这个示例画成一张依赖关系图，或者直接对比一下它和 MVC 的差别。

---

## **一、Clean Architecture 是什么？**

**Clean Architecture 是一种软件设计思想**，由 Robert C. Martin（“Uncle Bob”）提出。

核心目标就一句话：

👉 **让代码更清晰、易维护、可扩展、可测试**

---

## **二、核心思想（最重要的点）**

---

### **2️⃣ 依赖规则（重点！）**

👉 **依赖只能从外往内**

也就是说：

- UI 可以依赖业务逻辑 ✅
- 业务逻辑不能依赖 UI ❌
- 数据库不能影响核心逻辑 ❌

👉 核心永远“独立”

---

## **三、每一层是干嘛的？**

### **🔹 Entities（实体层）**

- 最核心的业务对象
- 不依赖任何框架
- 例如：
    - 用户（User）
    - 订单（Order）

👉 **最稳定的一层**

---

### **🔹 Use Cases（用例层）**

- 描述“系统要做什么”
- 比如：
    - 注册用户
    - 下订单
    - 计算价格

👉 **业务逻辑在这里**

---

### **🔹 Interface Adapters（接口适配层）**

- 把外部数据转换成系统能用的格式
- 比如：
    - Controller（接收请求）
    - Presenter（返回数据）
    - Repository（数据访问接口）

---

### **🔹 Frameworks & Drivers（框架层）**

- 最外层
- 包括：
    - Web框架（Django / Spring）
    - 数据库（MySQL）
    - UI（React）

👉 **最容易变的一层**

---

## **四、为什么要用 Clean Architecture？**

不用它会发生什么👇

- 业务逻辑写在 Controller 里 ❌
- 数据库改了，整个系统爆炸 ❌
- 很难测试 ❌

用了之后👇

✅ 换数据库 → 几乎不影响

✅ 换前端 → 不影响核心逻辑

✅ 好测试（可以单测业务）

✅ 代码结构清晰

---

## **五、一个简单例子**

假设你做一个“下单系统”：

### **❌ 烂结构（常见）**

```
def create_order(request):
    # 直接操作数据库
    # 直接写业务逻辑
```

👉 所有东西混在一起

---

### **✅ Clean Architecture**

```
Controller → UseCase → Entity → Repository
```

- Controller：接收请求
- UseCase：处理下单逻辑
- Entity：订单对象
- Repository：存数据库

👉 每一层职责清晰

---

## **六、一句话总结**

👉 **Clean Architecture = 让业务逻辑“独立”，其他都是可替换的外壳**

---

## **如果你想更深入**

我可以帮你进一步讲👇：

- Clean Architecture vs MVC / MVVM
- 实际项目结构怎么写（Java / Python / Node）
- 面试怎么回答这个问题
- 常见误区（很多人用错）

直接说你想了解哪一部分 👍