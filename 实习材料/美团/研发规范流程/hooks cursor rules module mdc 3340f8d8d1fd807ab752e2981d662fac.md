# hooks/.cursor/rules/module.mdc

```markdown
---
alwaysApply: true
---

# 本文件维护指南

- 当模块下的内容更新时，必须检查是否需要更新本文件以适配最新更改。
- 本文件在维护迭代时应**力求简洁**，只有较大的变更才需要更新本文件。
- 当 cursor 更改本模块下的文件时，应检查本文件与当前模块的适配性。

# Hooks 模块说明

本目录包含从 `ka-mop-duo-shelf-mix/src/index.tsx` 拆分出的自定义 hooks，用于管理「可囤可点」(团购秒提) 业务的核心逻辑。

## 架构设计

采用「主组件聚合 + hooks 纯函数化」的模式：

- 主组件 (`index.tsx`) 集中持有状态与上下文，负责状态定义、hooks 调用和 JSX 渲染
- 各 hook 通过显式参数注入依赖，不直接互调，避免循环依赖
- hook 之间通过主组件转发数据，保持单向数据流

```
┌─────────────────────────────────────────────────────────────┐
│                    ShelfCardComponent                        │
│  (状态定义 + hooks 组装 + JSX 渲染)                           │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│   useInitData ──→ useActionParams ──→ useActions            │
│        │                │                  │                 │
│        │                │                  │                 │
│        └────────────────┴──────────────────┘                 │
│                         │                                    │
│              useSubmitSync    useLx    useRequestTime         │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

## Hooks 职责

### useInitData

- **职责**：初始化数据同步、预加载
- **功能**：
  - 监听 `onlineOrderPropsVo` 变化，同步门店/商品/价格/提单信息到本地状态
  - 从 `frontParamMap` 恢复用户选择、备注、必选菜等暂存数据
  - 预加载门店选择页和订单详情页 bundle
  - 处理切换门店后的 toast 提示
- **入参**：`UseInitDataParams` + `UseInitDataSetters`
- **出参**：无（纯副作用 hook）

### useActionParams

- **职责**：生成用户交互/请求所需的参数
- **功能**：
  - `requestCommonParams`: 构建请求公共参数（用户 ID、城市、位置、平台等）
  - `getMopPurchaseItemList`: 获取当前选中商品列表（含数量、dealTag 等）
  - `getKaParams`: 根据场景（修改规格/切换门店/提单/加购等）生成 DUO 通信参数
- **入参**：`UseActionParamsInput`
- **出参**：`UseActionParamsOutput`

### useActions

- **职责**：收敛所有用户操作 handler
- **功能**：
  - 门店切换：`onSwitchShop`, `onJumpToPoiSelect`, `onSwitchShopInSubmit`
  - 规格选择：`onSelectedItemChange`, `onSkuModify`, `onQuantityModify`
  - 确认/加购：`onConfirmChoose`
  - 商品懒加载：`getProductInfo`
  - 提醒状态：`onRemindStatusChange`
  - 门店切换事件监听（KA_MOP_HOME_SWITCH_SHOP）
  - 算价逻辑（区分团购算价 vs 仅秒提算价）
- **入参**：`UseActionsInput` + `UseActionsSetters`
- **出参**：各类 handler 函数 + `showAddShopCart`（是否展示加入购物车按钮）+ `isAfterPurchaseJumpPoi`（购后链路只展示购物车/选好了按钮）

### useSubmitSync

- **职责**：提单页数据同步与状态管理
- **功能**：
  - 实时向 DUO 暂存提单数据（切 tab、支付时需要）
  - 区分「可囤可点」和「随心配」两种场景的参数构建
  - 管理 remark/fulfillment/mustChooseDish 状态修改
- **入参**：`UseSubmitSyncInput` + `UseSubmitSyncSetters`
- **出参**：`onRemarkModify`, `onCurrentFulfillMentModify`, `mustChooseDishModify`

### useLx

- **职责**：埋点 valLab 计算、曝光与点击事件
- **功能**：
  - `commonValLab`: 通用埋点参数（deal_id、poi_id、status、source 等）
  - `exposeSkuViewLx`: 选规格页曝光埋点
  - `onMoreShop` / `onMoreShopInErrorPage`: 切换门店点击埋点
  - `customLxConfig` / `submitCommonLxConfig`: 选规格页/提单页埋点配置
- **入参**：`UseLxInput`
- **出参**：`UseLxOutput`

### useRequestTime

- **职责**：性能监控，统计商品懒加载端到端耗时 + 首屏渲染/跳出率等关键指标
- **功能**：
  - 监听 `UPDATE_QUERY_PRODUCT_INFO` 事件，记录商品懒加载请求发起时间（带 `groupId/spuId` 校验）
  - 监听 `onlineOrderPropsVo` 变化，在 update 数据返回时计算耗时并上报 `mop-update-query-product-info`
  - 使用请求队列处理并发场景（DUO 一次只能执行一次 update）
  - 监听 `PAGE_FIRST_SCREEN_RENDER_COMPLETE` 事件，上报首屏渲染完成耗时 `mop-page-first-screen-render-complete`
  - 上报页面跳出率指标 `mop-page-jump-out`（进入页面上报 0，加载成功上报 2）
- **入参**：`UseRequestTimeParams`（`onlineOrderPropsVo` + `performanceStat` + `rootTag`，其中 `rootTag` 用于引擎复用时重置首屏上报状态）
- **出参**：无（纯副作用 hook）

## 数据流向

1. **DUO 下发数据** → `useInitData` → 同步到各状态
2. **用户操作** → `useActions` 中的 handler → 调用 `getKaParams` 生成参数 → 通过 `onChange` 通知 DUO
3. **DUO 返回更新** → `useInitData` 再次同步 → 触发 UI 更新
4. **提单页** → `useSubmitSync` 持续向 DUO 暂存数据

## 业务场景

本 hooks 模块支持以下业务场景：

- **可囤可点**：普通团购 + 秒提点单
- **随心配**：随心配套餐下单
- **购物车**：从购物车进入的选规格/提单
- **团购核销**：已购券核销场景（POI 核销、特团核销）
- **特团**：特价团购场景

## 注意事项

1. hooks 之间不要直接互调，所有依赖通过参数传入
2. `onChange` 用于触发 DUO 更新，`onUserAction` 用于暂存数据（切 tab 时保留）
3. 算价逻辑需区分「团购算价」和「仅秒提算价」，由 `dealTag` 和 `isPurchasedDeal` 决定
4. 门店切换在不同场景有不同行为（跳 POI 页 vs 停留当前页）

```