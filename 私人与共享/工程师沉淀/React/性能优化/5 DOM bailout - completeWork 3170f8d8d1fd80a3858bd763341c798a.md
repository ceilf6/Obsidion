# 5. DOM bailout - completeWork

即使 render 了也不一定会 commit

在 diffProps 中有

```jsx
if (oldProps === newProps) {
  return null;
}
```

那么就不生成 effect tag

所以 render ≠ DOM 更新