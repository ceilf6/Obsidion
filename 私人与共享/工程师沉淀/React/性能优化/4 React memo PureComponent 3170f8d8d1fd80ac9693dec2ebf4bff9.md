# 4. React.memo / PureComponent

```jsx
if (shallowEqual(prevProps, nextProps)) {
  return bailoutOnAlreadyFinishedWork(...)
}
```

本质是**主动控制 didReciveUpdate 为 false 避免深度递归子树更新**

是否 收到 更新