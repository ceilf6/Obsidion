# util-pr-experience-analyzer skill

Source: [KM 2762886164](https://km.sankuai.com/collabpage/2762886164)

1. 接收 Code webhook 或 CatDesk 手动触发，读取 PR 编号、仓库、作者、分支、标题、描述等信息。
2. 通过 code-cli skill 拉取 PR 元信息、变更文件列表和逐文件 diff。
3. 基于 diff 生成业务向的变更摘要，包括一句话总结和最多 8 条核心变更。
4. 用核心变更点检索体验链路知识库，主要面向 ka/knowledge-base / OpenViking。
5. 判断 PR 是否会影响用户可感知的体验链路，例如下单、支付、核销、领券、凑单等。
6. 对每条受影响链路输出风险等级、风险分类、影响描述、修复方案、残余风险、测试点和证据来源。
7. 如果知识库检索失败，也会降级为仅基于代码 diff 的分析，但要标注置信度较低。
8. 如果没有用户可感知风险，则不生成 risk_chains，只记录本次 PR “未检测到体验链路影响”。
9. 将结果写入 NoCode Supabase DB：pr_records 存 PR 总记录，risk_chains 存每条风险链路。
10. 最后输出一份结构化分析摘要，并指向体验风险看板。

边界也写得比较明确：它不适合“纯代码质量 Review”，也不适合与体验链路无关的基础设施变更；这类应该走其他 skill。