# createFiber 节点

https://github.com/ceilf6/mini-react/commit/a48006861d688f1775ce55fd9ce0274794eb6464

# 1. vnode

用于描述UI
JSX => React.createElement => ReactElement(即vnode)

# 2. FiberNode

根据 vnode 创建而来，是 vnode 的运行时实例
是 Fiber 调度的工作单元