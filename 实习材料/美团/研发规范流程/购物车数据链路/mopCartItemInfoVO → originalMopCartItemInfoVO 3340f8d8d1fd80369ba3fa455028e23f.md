# mopCartItemInfoVO → originalMopCartItemInfoVO

```tsx
  const {
    mopCartItemInfoVO: originalMopCartItemInfoVO,
  } = props;
```

解构 将mopCartItemInfoVO用originalMopCartItemInfoVO变量存储

**结论**

这个文件里的“购物车数据”不是自己主动请求拿到的，而是上层通过 `props` 传进来的。`ShopCartModify` 更像一个“购物车规格修改浮层”，它做的是消费购物车项数据、补拉规格详情、做算价，然后把修改结果再抛回上层。

最关键的入口在 [packages/ka-mop-shop-cart-modify/src/index.tsx:25](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/index.tsx) 和 [packages/ka-mop-shop-cart-modify/description.json:15](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/description.json)：

- `mopCartItemInfoVO` 是必传 prop，说明里写的就是“购物车子项商品信息”
- `cartItemId` 虽然也定义了，但这个文件内部并没有用它去请求数据

**数据流**

在 [packages/ka-mop-shop-cart-modify/src/index.tsx:40](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/index.tsx) 开始，组件把 `props.mopCartItemInfoVO` 解构成 `originalMopCartItemInfoVO`。

然后在 [packages/ka-mop-shop-cart-modify/src/index.tsx:85](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/index.tsx) 的 `useEffect` 里监听它变化：

- 先经过 [packages/ka-mop-shop-cart-modify/src/utils/normalizeCartItemInfoVO.ts:10](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/utils/normalizeCartItemInfoVO.ts) 做一次规范化，把后端的 `dealIdStr` 转成前端还在用的 `dealId`
- 如果数据里有 `cartItemId` 或 `purchaseItemType`，就 `setMopCartItemInfoVO(normalized)` 存到本地 state，并打开浮层
- 如果上层把数据清空了，它只会关闭浮层，不会立刻清掉本地 state，目的是避免动画关闭阶段点击事件访问空数据时报错

所以，这个文件里真正“使用中的购物车项数据”来自：
`props.mopCartItemInfoVO -> normalize -> 本地 state mopCartItemInfoVO`

**它自己会发什么请求**

它不会请求“购物车列表/购物车项详情”，但会请求“修改浮层需要的附加数据”：

- [packages/ka-mop-shop-cart-modify/src/index.tsx:108](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/index.tsx) 先通过 `baseQueryParams` 或 `__duo__.getCommonParams()` 组装通用请求参数，具体字段在 [packages/ka-mop-shop-cart-modify/src/dataSource/index.ts:20](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/dataSource/index.ts)
- [packages/ka-mop-shop-cart-modify/src/index.tsx:116](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/index.tsx) 调 `queryProductDetailForPoiShelfFunc`，底层接口是 [packages/ka-mop-shop-cart-modify/src/dataSource/request.ts:70](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/dataSource/request.ts) 的 `/mop/api/menu/productDetailForPoiShelf`
- [packages/ka-mop-shop-cart-modify/src/index.tsx:129](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/index.tsx) 调组合子商品算价，底层是 [packages/ka-mop-shop-cart-modify/src/dataSource/request.ts:103](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/dataSource/request.ts)
- [packages/ka-mop-shop-cart-modify/src/index.tsx:168](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/index.tsx) 在用户改规格时，会根据场景调用 `/mop/api/menu/productCalculatorForPoiShelf` 或 `/mop/api/menu/dealCalculatorForGroupTrade` 做重新算价，并把结果写到 `calPriceVO`

最后在 [packages/ka-mop-shop-cart-modify/src/index.tsx:140](https://www.notion.so/Users/ceilf6/Desktop/ka-mop-max-duo/packages/ka-mop-shop-cart-modify/src/index.tsx) 的 `confirmModifyChoose` 里，它会把当前 `mopCartItemInfoVO` 和用户新选择组装成 `mopOperateCartParam`，再调用 `modifyConfirm` 抛给上层。代码注释也明确写了：接口成功后会由上层 `update` 自动刷新数据。

补一句实话：我在当前仓库里没有找到这个组件在真实业务中的上游接入点，所以“最初是谁把 `mopCartItemInfoVO` 传进来”的逻辑不在这个包内部。如果你愿意，我可以继续帮你往 `modifyConfirm` 或宿主容器那一层追，定位真正的购物车查询接口。