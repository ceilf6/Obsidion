# chunk分块

[嵌入模型输出结果](嵌入模型输出结果%203260f8d8d1fd800490bfc1014724b239.md)

报错 429 是因为嵌入模型的输入限制

当前实现里分两类向量：

1. 文档向量
存到 `.frontagent/rag-cache/embeddings.json`，对应 `Lab` 仓库切块后的内容。这个部分通常是“跑一次后复用”的。代码在 [rag.ts](https://www.notion.so/Users/a86198/Desktop/Lab/AI/3-Application/FrontAgent-app/packages/mcp-memory/src/rag.ts#L440)。
只有这些情况会重跑一部分或全部：
- `Lab` 仓库有新提交，导致 chunk 内容变了
- 你改了 embedding `model`
- 你改了 embedding `baseURL`
- 你改了 `dimensions`
- 你改了分块参数，导致 chunk 重新切分

现在实现是按 `chunk.contentHash` 增量更新，不是每次全量重算。[rag.ts](https://www.notion.so/Users/a86198/Desktop/Lab/AI/3-Application/FrontAgent-app/packages/mcp-memory/src/rag.ts#L466)

1. **查询向量
这个不是长期缓存的。每次你搜一个新问题，都会先把“当前 query”再做一次 embedding**，然后拿去和本地已存的文档向量做相似度计算。[rag.ts](https://www.notion.so/Users/a86198/Desktop/Lab/AI/3-Application/FrontAgent-app/packages/mcp-memory/src/rag.ts#L1032)

所以准确说法是：

- `文档向量`：大部分情况下只算一次，后续复用
- `查询向量`：每次查询都要重新算
- `BM25 索引`：也会缓存到 `.frontagent/rag-cache/index.json`

还有一个你要知道的点：
当前 CLI 默认 `syncOnQuery=true`，所以每次查询前会先检查远程 `Lab` 有没有新提交；如果没变，就直接复用已有索引和向量，不会重新全量嵌入。[rag.ts](https://www.notion.so/Users/a86198/Desktop/Lab/AI/3-Application/FrontAgent-app/packages/mcp-memory/src/rag.ts#L369)

一句话总结：
你理解对了一半。`知识库文档向量` 不需要每次重跑，但 `用户查询本身的向量` 每次都要跑一次。