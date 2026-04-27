# useEffectEvent

https://zh-hans.react.dev/reference/react/useEffectEvent

Q: React19.2的useEffectEvent和useMemoizedFn、useCallback是什么关系

三者解决的是**同一个问题**（稳定引用 + 读取最新值），但使用范围不同：

---

**`useEffectEvent`（React 实验性 API）**

```jsx
function Chat({ roomId, theme }) {
    const onConnected = useEffectEvent(() => {
        showNotification('Connected!', theme)  // 总读取最新 theme
    })

    useEffect(() => {
        const conn = createConnection(roomId)
        conn.on('connected', onConnected)  // 稳定引用，不需要加 theme 为依赖
        return () => conn.disconnect()
    }, [roomId])  // ← 不需要写 theme
}
```

---

**三者对比：**

|  | `useCallback` | `useMemoizedFn` | `useEffectEvent` |
| --- | --- | --- | --- |
| 引用是否稳定 | 依赖不变才稳定 | ✅ 永远稳定 | ✅ 永远稳定 |
| 是否读取最新值 | 需要把依赖写全 | ✅ 始终最新 | ✅ 始终最新 |
| 能否传给子组件 | ✅ | ✅ | ❌ 禁止 |
| 能否在事件处理器中调用 | ✅ | ✅ | ❌ 禁止 |
| 只能在 Effect 内调用 | ❌ | ❌ | ✅ 强制 |
| 来源 | React 官方 | ahooks 社区 | React 官方（实验性） |

---

**`useEffectEvent` 为什么限制只能在 Effect 内调用？**

因为它的设计语义是**"Effect 的事件"**——副作用执行时触发的回调，React 可以保证此时渲染已完成、值是最新的。

如果允许在任意地方调用（如子组件的点击事件），React 无法保证执行时机，可能读到中间状态，语义不清晰。

---

**本质关系：**

```
useEffectEvent  ≈  useMemoizedFn 的 Effect 专用受限版
```

`useMemoizedFn` 是社区在 `useEffectEvent` 尚未正式发布前的通用解决方案，功能更广但需要开发者自己保证调用时机的正确性。