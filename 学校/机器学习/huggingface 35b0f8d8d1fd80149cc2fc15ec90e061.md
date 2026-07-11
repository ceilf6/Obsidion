# huggingface

不只是微调。**拿到 Hugging Face 上的开放权重模型后，能做的事情大概分三层：**

## 1. 不训练，直接用

这是最常见、成本最低的路线。

你可以直接把模型接进架构里做：

| 用法 | 例子 |
| --- | --- |
| 推理服务 | 本地聊天、API 服务、客服机器人 |
| RAG | 接知识库、文档问答、企业内部搜索 |
| Agent | 调工具、查数据库、写代码、执行工作流 |
| 分类/抽取 | 文本分类、实体抽取、意图识别 |
| Embedding | 语义搜索、推荐、去重、聚类 |
| Rerank | 搜索结果重排，提高 RAG 准确率 |

很多业务场景其实**不用微调**，直接用 **RAG + prompt + 工具调用** 就够了。

## 2. 轻量改造，不动大模型主体

这比微调更常见，也更实用。

比如：

**Prompt engineering**

调整系统提示词、few-shot 示例、输出格式。

**RAG**

把你的私有资料放进向量库，模型回答时检索相关内容。

**Function calling / tool use**

让模型调用你的接口，比如查订单、查库存、生成报表。

**量化**

把模型变小，比如 FP16 → int8 / int4 / GGUF Q4，方便本地跑。

**蒸馏/缓存/路由**

大模型负责难问题，小模型负责简单问题，降低成本。

这些都不一定需要训练模型。

## 3. 微调

微调适合这些情况：

| 适合微调 | 不太适合微调 |
| --- | --- |
| 固定风格输出 | 想让模型记住大量知识 |
| 特定格式生成 | 知识经常变化 |
| 行业术语/流程 | 数据很少、质量差 |
| 分类/抽取任务 | 只是想接公司文档 |
| 多轮客服话术 | 只是想改善事实准确性 |
| 代码风格/DSL | 本地机器资源很弱 |

很重要的一点：

> **微调不是让模型“记住知识库”的最佳方式。**
> 
> 
> 想让模型掌握你的私有文档，通常优先用 **RAG**。
> 
> 想让模型改变行为、风格、格式、任务能力，才考虑 **微调**。
> 

## 你本地资源少的话，优先顺序应该是

**第一步：直接跑量化模型**

比如 Qwen 3B / 7B GGUF、DeepSeek distill 小模型、Gemma 3/4B、Phi 小模型。

**第二步：做 RAG**

接你的文档、数据库、业务资料。

**第三步：优化 prompt 和工具调用**

让模型输出固定 JSON、调用接口、走业务流程。

**第四步：再考虑 LoRA / QLoRA 微调**

而不是一上来全量微调。

## 微调也不是“训练一个新模型”

本地小资源通常做的是 **LoRA / QLoRA**：

```
基础模型不大改
只训练一小部分适配参数
训练成本低很多
最后加载 base model + adapter
```

比如你可以拿一个 7B 模型，用几十 MB 到几百 MB 的 LoRA adapter 去适配你的任务，而不是重新训练一个 7B 模型。

## 一句话

**开放权重模型能做的不只是微调。**

更现实的路线通常是：

> 直接推理 → RAG → 工具调用 → 量化部署 → 必要时 LoRA/QLoRA 微调
> 

对大多数应用来说，**RAG 和系统集成比微调更重要**。

[self-微调](huggingface/self-%E5%BE%AE%E8%B0%83%2035b0f8d8d1fd801e9a4cf13371e20cc2.md)

### 最终推荐你这样填

**Collection Name**

```
FrontAgent: Frontend Engineering Agent
```

**Description**

```
A collection for FrontAgent, an LLM-powered agent system for frontend engineering. It includes the SFT dataset, LoRA planner model, interactive demo Space, and the open-source GitHub project.
```

**Items 顺序**

```
1. https://huggingface.co/spaces/ceilf6/frontagent-planner-demo
2. https://huggingface.co/ceilf6/frontagent-planner-7B-lora
3. https://huggingface.co/datasets/ceilf6/frontagent-planner-sft-data
4. https://github.com/ceilf6/FrontAgent
```