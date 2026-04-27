# useSyncExternalStore (cc源码)

是，`useSyncExternalStore` 是 **React 官方内置 Hook**，从 `react` 包直接导出：

```tsx
import { useSyncExternalStore } from 'react'
```

React 官方文档当前也把它列在 Hooks API 里，并把它定义为“用于订阅外部 store 的 Hook”。来源：[React 官方文档 `useSyncExternalStore`](https://react.dev/reference/react/useSyncExternalStore)

你可以这样理解它的定位：

1. `useState` / `useReducer` 管 React 内部状态。
2. `useSyncExternalStore` 管 React 外部状态源。
3. 它要求你提供两个核心函数：`subscribe` 和 `getSnapshot`。
4. React 再用这两个函数安全地把外部 store 接进渲染流程。

所以 Claude Code 里像命令队列、`QueryGuard`、任务 watcher 这种“状态不住在 React 里”的东西，用它是很标准的。官方也明确说了：如果能用 `useState` / `useReducer`，优先用它们；`useSyncExternalStore` 主要是给“现有非 React 状态”接入 React 用的。来源：[React 官方文档 `useSyncExternalStore`](https://react.dev/reference/react/useSyncExternalStore)

如果你愿意，我下一条可以继续讲它**为什么叫 Sync External Store**，以及这个 `Sync` 到底在防什么问题。