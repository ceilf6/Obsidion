# ka-skills

Source: [KM 2759290975](https://km.sankuai.com/collabpage/2759290975)

用于 秒提 等业务提供 AI 点餐等服务

## 困难

像瑞星中选择商品后规格等选择需要根据 appmock 中的数据格式进行规范进而实现点餐 => 待付款页面

秒提点单

## 梳理

这个仓库 `ka-skills` 是一个给 AI Agent 使用的“业务 Skill + CLI 工具” monorepo，核心目标是把大客/秒提这类业务操作沉淀成可触发、可执行、可测试、可发布的能力包。

整体可以这样理解：

- [skills](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/skills)：Skill 定义层，主要是 `SKILL.md`、测试说明和参考资料。这里不放 npm 依赖，偏“给 Agent 读的操作手册”。
- [cli](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/cli)：CLI 实现层，真正执行 API 请求、登录、查询、下单等动作。
- [cli/shared/cli-shared](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/cli/shared/cli-shared)：CLI 公共库，封装日志、结构化错误、API 调用等 Agent 友好的基础能力。
- [scripts](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/scripts)：脚手架、打包、发布脚本，比如创建 Skill、创建 CLI、打包上传 Friday Skills 广场。
- [templates](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/templates)：CLI/Skill 测试模板。
- [website](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/website)：一个技能目录/展示页的数据和构建脚本。

当前仓库里有 3 个 Skill、1 个 CLI：

- [user-mop-order](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/skills/user-mop-order/SKILL.md)：秒提 C 端点单助手，走 `food-mop-order` CLI，覆盖查门店货架、查规格、预提单、提交下单。
- [operator-mop-ops](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/skills/operator-mop-ops/SKILL.md)：秒提运营端助手，走 `food-mop-ops` CLI，覆盖门店、品牌、商品、促销、订单查询和部分修改。
- [user-mop-tt-analysis](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/skills/user-mop-tt-analysis/SKILL.md)：秒提 C 端 TT 工单分析，拉取工单并生成分类、根因、体验痛点和优化建议。
- [@meishi/food-mop-order](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/package.json)：秒提点单 CLI，bin 是 `food-mop-order`，版本当前是 `0.4.4`。

开发方式上，它用 `pnpm` workspace，范围是 `cli/*/*`，根目录脚本通过 `lerna` 批量构建、测试、发布。常用入口包括：

```
// 代码块
pnpm build
pnpm test
pnpm test:cases
pnpm create-skill
pnpm create-cli
pnpm zip-skill
pnpm deploy-skill
```

仓库最重要的规范文件是这两个：

- [CONVENTIONS.md](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/CONVENTIONS.md)：Skill/CLI 的目录、命名、frontmatter、测试和发布规范。
- [CLI-CONVENTIONS.md](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/CLI-CONVENTIONS.md)：CLI 设计约束，尤其是 stdout/stderr 分离、退出码、结构化 JSON 错误、路径安全和 `-dry-run`。

一句话版：这是一个“把美团秒提相关操作产品化给 Agent 用”的仓库，Skill 负责告诉 Agent 什么时候用、怎么用，CLI 负责稳定执行真实业务动作，脚本负责批量创建、测试、打包和发布。

我还看到一个小提醒：`food-mop-order` 的 [README](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/README.md) 里安装包名看起来有点旧，写的是 `@meishi/food-mop-ai-order`，但实际 package 和 Skill 都指向 `@meishi/food-mop-order`。后续改文档或发布前可以顺手核一下。

### 当前实现程度

▎ [🟠 阿里味] 结论先摆出来：点单代码已经做到“可真实走下单链路”的实现阶段，但当前仓库测试只验到查询和无登录分支，真实 `order/submit` 还没有自动化验收闭环。

**当前实现程度**

`food-mop-order` 已注册完整命令链路：[login/poi/deal/order/submit](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/bin/cli.js:14)。

已实现：

- 登录：扫码登录、手动 token、状态查询、token 校验、清缓存。
- 查门店货架：`poi <poiId>`，解析秒提支持、营业状态、轮播文案、分类商品。
- 查商品规格：`deal <poiId> <dealId>`，能解析门店、商品、价格、SKU、售卖/非售卖属性。
- 预提单：`order <poiId> <dealId>`，已经实现 `precreate/update`，支持 `-sku`、多 `-attr`，并兼容 `dealMappingType=10` 单品和 `20` 套餐：[order.ts](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/order.ts:26)。
- 提交下单：`submit <poiId> <dealId>`，已经实现 `deal preview → precreate/update → precreate/submit` 全流程，也支持 `-from-order` 复用预提单 JSON：[submit.ts](https://app.notion.com/Users/ceilf6/Desktop/ka-skills/cli/mop/mop-order/src/command/submit.ts:38)。
- 成功后会输出订单号、流水号、是否需支付、payToken、支付结果页、订单详情中转链接。

**还没完全闭环的点**

- 没有 token，所以我这里没跑真实 `poi/deal/order/submit` 在线链路；真实查询用例被跳过。
- 自动化测试目前只覆盖无登录错误分支和登录态下 `poi/deal` 查询，不覆盖 `order/submit`。
- `submit` 是写操作，但目前没有 `-dry-run`，这和仓库 CLI 规范里的写操作要求不完全一致。
- Skill 文档提到 `~/.food-mop-order/history.json` 历史门店/商品读写，但 CLI 代码里目前没看到实际读写历史的实现。
- `submit --from-order` 重建 purchase list 时硬编码 `dealMappingType: 20`，对单品 `type=10` 的复用模式有风险；全流程模式已单独处理 type=10。

我顺手修了一个测试假失败：`tests/cases.json` 里还在断言旧命令 `food-mop login`，实际 CLI 已是 `food-mop-order login`，现在已改成正确断言。

**验证结果**

已跑：

```
// 代码块
pnpm --filter @meishi/food-mop-order typecheck
pnpm --filter @meishi/food-mop-order build
pnpm --filter @meishi/food-mop-order test:cases
```

结果：typecheck 通过，build 通过，cases 为 `2 通过，0 失败，2 跳过`。跳过原因是当前本机没有 `~/.food-mop-order/session.json` token。

> food-mop-order login 显示账号被风控了 [https://km.sankuai.com/collabpage/584251798](https://km.sankuai.com/collabpage/584251798)
> 

[image.png](https://km.sankuai.com/api/file/cdn/2759290975/234185454382?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2759290975/234190333690?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2759290975/234191930419?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2759290975/234195257081?contentType=1&isNewContent=false)

[打通 mop-order 联名套餐](ka-skills/%E6%89%93%E9%80%9A%20mop-order%20%E8%81%94%E5%90%8D%E5%A5%97%E9%A4%90%203760f8d8d1fd81979dbaf1e878d6fd91.md)