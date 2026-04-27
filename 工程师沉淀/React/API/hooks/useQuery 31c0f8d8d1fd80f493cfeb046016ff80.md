# useQuery

是 React-Query 库中最核心的钩子，用于**管理服务器状态数据**

```jsx
const { data, isLoading, error } = useQuery({
  queryKey: ['user'], // 缓存key
  queryFn: fetchUser // 获取数据的函数(AJAX)
})
```

有缓存机制，如果两个组件都请求user，那么实际发出请求只有一次，第二个用第一个的缓存值