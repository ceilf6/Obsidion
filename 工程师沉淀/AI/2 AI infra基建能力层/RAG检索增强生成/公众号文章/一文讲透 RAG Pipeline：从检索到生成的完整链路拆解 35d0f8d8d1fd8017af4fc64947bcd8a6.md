# 一文讲透 RAG Pipeline：从检索到生成的完整链路拆解

> 本文新一套全新的系列，主要围绕 RAG 相关内容展开
> 
> 
> 这篇文章是该系列的第 1 篇
> 
> 作者：谢杰
> 

先回顾一下前面我们学过的 RAG 基础知识，一个基础的 RAG 分为两个阶段：

1. 数据索引阶段：核心就是将数据存储到向量数据库
2. 数据检索阶段：核心就是将用户的问题转成向量，然后从向量数据库里面找出语义相同的内容，将其作为上下文给 llm 生成答案。

[image-20250528094543784](https://mmbiz.qpic.cn/sz_mmbiz_png/e5CpCFFf1a5dfXpGyO5QWJlKoHdnT50YlejttBWvdCiahicFOtLGoA5UEPuRcr3kwXwavPFatWqicwp9TpW67lbwZKhKYI0bkRZHZ6dFiaSYSHk/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=1)

那有这些知识就够了么？

不够，光掌握这些知识，你是没办法回答这些面试题的：

1. 如何设计一个 RAG 的 SDK？
2. chunking 如何设计？
3. 怎么评估 RAG 系统效果？
4. rerank 为什么重要？
5. Recall@K 是什么？
6. MRR 是什么？
7. ....

这一套课程，就是让你对整个 RAG 彻底通关的。当你学习完这套课程后，你能够对整个 RAG 有一个系统性的理解，而一个东西，当你对它有系统性理解之后，面试题无论怎么变，你都能从容应对。

如何搭建 RAG 的知识框架呢？这里我们可以对 RAG 知识进行分类，而这个分类是有讲究的，分类的视角不同，分出来的类别就不同的。这就好比针对编程语言做分类，按照强弱类型可以分出一个类别，按照编译解释可以分出来一个类别。

RAG 相关的知识，可以按照下面两个不同视角来做分类：

1. RAG pipeline 视角
2. RAG 工程视角

这篇文章我们先介绍一下 RAG pipeline 视角。

所谓 RAG pipeline，就是整个 RAG 的工作流程，其实和我们之前所学的 RAG 知识大差不差的。这里我将其分为 5 个阶段：

1. 数据索引阶段
2. 检索前处理
3. 检索操作
4. 检索后处理
5. 答案生成

## 1\. 数据索引阶段

所谓数据索引，就是将文档存储到向量数据库的过程，回忆一下我们前面所讲的知识：

1. 加载文档
2. 切分成 chunks
3. 转化为向量嵌入
4. 存入向量数据库

[image-20250528101753546](https://mmbiz.qpic.cn/sz_mmbiz_png/e5CpCFFf1a56Vg0ryaQTqTDW7ib3QWQMiawgzXreTdVUXYwYRT3C988QYdibEBGdKrGIzJjicdcdHhbib37gyJGKFuApnELtwSZMBo3lcvfXONWI/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=2)

这里面最重要的在于切分 chunks，这很大程度影响了后续 RAG 的检索质量，前面我们讲过，切割的时候可以：

1. 语义结构维度：强调的是**语义完整性**，防止模型拿到“断句、不完整”的上下文。可以按照句子的粒度进行切割，将每一段文本按句号、问号、叹号等 **标点符号** 分割。
    
    原文
    
    ```
    ChatGPT 是由 OpenAI 开发的大语言模型。它基于 Transformer 架构，具有强大的语言理解和生成能力。
    ```
    
2. 切割后
    
    ```
    ChatGPT 是由 OpenAI 开发的大语言模型。
    ```
    
    ```
    它基于 Transformer 架构，具有强大的语言理解和生成能力。
    ```
    
3. 实现策略维度：满足向量模型有最大词元限制，比如 OpenAI embedding 最大约 8192 词元数。
4. 固定长度字符切分：每 N 字符为一段，适合规则性较强的文档
5. 词元切分：每 N 个词元切一段，兼容模型的词元数限制

上面这两个策略可以组合着来使用。

另外，在切割这一块儿，你还需要理解下面的这些技术名词：

- Simple RAG
- Semantic Chunking
- Recursive Chunking
- Contextual Chunk Headers
- Document Augmentation
- Knowledge Graph
- Hierarchical Indexing
- 元数据抽取
- 去重与清洗
- 增量更新

这些技术名词各自的意思，我会放到具体介绍 pipeline 的时候来解释。

另外一个重点，就是关于向量数据库，这是自 AI 火起来后的一种新型数据库类型，在完成文本切分与 embedding 之后，数据通常会被存储到**向量数据库或支持向量检索能力的存储系统中**。

这些系统提供高效的相似度搜索（如 ANN / KNN），从而支持基于语义的检索能力。常见向量数据库如下：

| 向量库 | 特点 |
| --- | --- |
| Supabase | PostgreSQL + pgvector 扩展 |
| Weaviate | 云服务 + 本地部署均可 |
| Pinecone | 高性能、托管服务、易接入 |
| Milvus | 面向海量数据的高性能搜索 |
| Chroma | 轻量级、本地优先、开发友好 |
| MemoryVectorStore | 纯 JS 内存向量库（测试用） |

## 2\. 检索前处理

英语称之为 Pre-Retrieval。

所谓检索前处理，就是完成诸如：

- 查询转换
- 查询扩充
- 检索路由

等处理工作。

**查询转换（Query Rewriting）**

将用户的原始问题“重写”为一个更清晰、更标准、更检索友好的表达方式。例如：

| 原始问题 | 转换后查询 |
| --- | --- |
| “这个 App 支不支持退款？” | “App 退款政策是什么？” |
| “我买的耳机怎么一直没声音？” | “耳机无声音的常见原因与解决方法” |

**查询扩充（Query Expansion）**

在不改变用户意图的前提下，**添加相关词语或同义表达**，让检索系统能够匹配到更多语义相关的文档。例如用户输入：

```
项目合同
```

扩充后的 Query 变成了：

```
["项目合同", "合作协议", "法律文件", "合同模板"]
```

这类操作能显著提高召回率，避免“字不对字”导致遗漏。

**检索路由（Retrieval Routing）**

在准备外挂语料库（知识库）的时候，往往会有多个语料库。

针对不同类型的问题，选择不同的知识库或不同的检索方式，实现多路检索策略。例如：

| 用户问题 | 路由策略说明 |
| --- | --- |
| “这款产品电池容量是多少？” | 路由到【产品参数知识库】 |
| “怎么退货？” | 路由到【客服 FAQ 知识库】 |
| “能再详细说明一下工作原理吗？” | 路由到【技术文档知识库】，或使用多跳检索 |

检索前处理的目的，是为后面的检索和检索后处理做必要的准备，以便提高检索阶段 **召回知识** 的精确度与最终生成的质量。

这里解释一下 **召回率** 和 **精确率** 这两个名词：

**召回率（Recall）**

指的是所有相关内容中被成功检索出来的比例。公式为：

```
召回率 = 检索到的相关内容数量 / 所有实际相关内容的总数
```

例如：实际相关文档有 10 个，系统只检索到其中 6 个，那么召回率 = 6 / 10 = 60%

**精确率（Precision）**

指的是检索出来的所有内容中，真正相关的占比。公式为：

```
精确率 = 检索到的相关内容数量 / 检索到的所有内容数量
```

例如：实际相关文档有 10 个，系统共返回 8 个文档，其中 6 个是相关的，那么精确率 = 6 / 8 = 75%

也就是说，召回率反映的是系统的**覆盖能力**，而精确率衡量的是系统的**准确性**。

另外，下面是检索前处理涉及到的你必须要理解的名词：

- Query Transformation
- Query Rewrite
- Multi-query
- Query Decomposition
- HyDE

这些技术名词各自的意思，我会放到具体介绍 pipeline 的时候来解释。

## 3\. 检索操作

检索阶段分为下面几个步骤：

1. 将 Query 转化为向量
2. 在向量数据库中进行相似度检索，有几种方式：
3. 余弦相似度：关注向量方向是否一致
4. 欧氏距离：衡量向量之间的绝对距离远近
5. 点积：综合体现方向一致性与向量大小（长度）。

这一阶段你需要掌握的技术名词：

- Vector Search
- Keyword Search
- Fusion
- RRF
- Small-to-Big Retrieval
- Hypothetical Retrieval
- CRG

这些技术名词各自的意思，我会放到具体介绍 pipeline 的时候来解释。

## 4\. 检索后处理

英语为 Post-Retrieval，顾名思义就是对检索出的相关知识块做必要的补充处理的阶段。

即使用了很优秀的向量搜索，检索回来的 Top-K chunks 仍然可能存在这些问题：

1. 内容相关性差：向量相似度高但语义上与用户问题不匹配
2. 信息冗余：多个 chunks 说的是同一件事，浪费词元空间
3. 有害内容：包含过时、不合法、敏感内容
4. 结构混乱：拼接后的上下文缺少逻辑、排序不合用户意图

因此需要对检索结果进行进一步处理，确保大模型接收到的上下文内容是「最相关 + 最高质量 + 最结构化」的。

常见的处理有：

1. 重排序（Reranking）
2. 过滤无关内容（Filtering）
3. 合并去重（Merging）
4. 精简摘要（Summarization）
5. 格式优化（Structuring）

经过了这些后处理之后，能够使得最需要、最合规的知识块处于上下文的最前端，从而有助于提高大模型的输出质量。

该阶段需要掌握的技术名词：

- Re-rank（核心）
- Context Enriched Retrieval
- RSC
- Context Compression
- 文档过滤 / threshold

这些技术名词各自的意思，我会放到具体介绍 pipeline 的时候来解释。

## 5\. 答案生成

答案生成，就是将检索到的内容和用户问题一起发送给 llm，然后由大模型生成答案：

![image-20250528134121574](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='[http://www.w3.org/2000/svg](http://www.w3.org/2000/svg)' xmlns:xlink='[http://www.w3.org/1999/xlink](http://www.w3.org/1999/xlink)'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

构造出来的提示词大致如下：

```
[系统提示]：
```

该阶段需要掌握的技术名词：

- Prompt Template
- Self-RAG
- Grounding
- Answer with citation
- LLM-as-Judge
- 多答案一致性
- Context Compression（部分也在这里）

这些技术名词各自的意思，我会放到具体介绍 pipeline 的时候来解释。

## 6\. 写在最后

通过对 **RAG Pipeline** 这五个阶段的拆解，相信你已经发现，一个工业级的 RAG 系统绝不仅仅是“向量检索 + Prompt”那么简单。从索引时的切片策略，到检索前的查询变换，再到检索后的重排序，每一个环节的细微优化，最终都会直接影响到模型生成的准确性和可靠性。

本文作为《RAG 彻底通关》系列的第一篇，旨在帮你从**流程视角**建立起全局观。有了这个地图，我们在后续章节中深入探讨 `HyDE`、`Rerank` 或 `Semantic Chunking` 等具体技术时，你就能清晰地知道它们在整个链路中的坐标与意义。

在下一篇文章中，我将转换视角，带你从**工程化**的角度去审视 RAG。

技术在不断演进，但底层逻辑始终如一。如果你在搭建 RAG 系统的过程中遇到了某些“坑”，或者对某个阶段的实现细节有疑问，欢迎在评论区留言，我们一起交流探讨。

我们下一篇见。

RECOMMEND

推荐阅读

[![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzI2NTQ5NTE4OA==&action=getalbum&album_id=4101026696059338761#wechat_redirect)[http://www.w3.org/2000/svg](http://www.w3.org/2000/svg)' xmlns:xlink='[http://www.w3.org/1999/xlink](http://www.w3.org/1999/xlink)'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

[![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzI2NTQ5NTE4OA==&action=getalbum&album_id=4101027889775034373#wechat_redirect)[http://www.w3.org/2000/svg](http://www.w3.org/2000/svg)' xmlns:xlink='[http://www.w3.org/1999/xlink](http://www.w3.org/1999/xlink)'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

[![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzI2NTQ5NTE4OA==&action=getalbum&album_id=4101072664272224259#wechat_redirect)[http://www.w3.org/2000/svg](http://www.w3.org/2000/svg)' xmlns:xlink='[http://www.w3.org/1999/xlink](http://www.w3.org/1999/xlink)'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

[![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzI2NTQ5NTE4OA==&action=getalbum&album_id=4287783787557404679#wechat_redirect)[http://www.w3.org/2000/svg](http://www.w3.org/2000/svg)' xmlns:xlink='[http://www.w3.org/1999/xlink](http://www.w3.org/1999/xlink)'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

![图片](data:image/svg+xml,%3C%3Fxml version='1.0' encoding='UTF-8'%3F%3E%3Csvg width='1px' height='1px' viewBox='0 0 1 1' version='1.1' xmlns='[http://www.w3.org/2000/svg](http://www.w3.org/2000/svg)' xmlns:xlink='[http://www.w3.org/1999/xlink](http://www.w3.org/1999/xlink)'%3E%3Ctitle%3E%3C/title%3E%3Cg stroke='none' stroke-width='1' fill='none' fill-rule='evenodd' fill-opacity='0'%3E%3Cg transform='translate(-249.000000, -126.000000)' fill='%23FFFFFF'%3E%3Crect x='249' y='126' width='1' height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)