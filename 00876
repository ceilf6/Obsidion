# React架构

Q: 为什么转成Fiber架构之后就能实现打断了？Scheduler维护的最小堆任务队列和FiberTree、FiberNode中的hook链、hook中的UpdateQueue是什么关系

首先，明确需要的能力是 打断render渲染过程，这依赖 FiberTree 的指针链式结构 以及 Scheduler 的 shouldYield

这是因为在 Stack 老架构中，React diff 是一路递归下去的，JS调用栈一旦跑起来就很难中止；而新版架构能打断是因为 每个FiberNode就是一段工作单元 ，React 不再依赖递归走完整颗树，而是 **Scheduler中**一个**循环** - 在保证优先级的情况下去尽量利用时间片
**performUnitOfWork → shouldYield? → 继续/暂停**

如果有更高优先级，直接插入到 Scheduler 中的小顶堆优先任务队列中，然后 通过MessageChannel 包裹成一个宏任务 由 事件循环 机制调度，接着通过每一帧剩余的时间片切割执行

[Vue渲染](Vue渲染%203180f8d8d1fd80d4bebcc13094fb39ae.md) 

[就业.二](就业%20二%2030a0f8d8d1fd802faa52f5233d6fdf9f.md)

[虚拟 DOM](虚拟%20DOM%2030a0f8d8d1fd8086a9fdd3c5b428933e.md)

[React 整体架构](React%20整体架构%2030a0f8d8d1fd809ab1c6eab6ed78ad9d.md)

[React 渲染流程](React%20渲染流程%2030b0f8d8d1fd80139c38c2ef2d9b00a4.md)

[Fiber双缓冲](Fiber双缓冲%2030c0f8d8d1fd805b8a7dc0323f37f32b.md)

[MessageChannel](MessageChannel%2030c0f8d8d1fd805c99bbdf9081a61e9d.md)

[Scheduler](Scheduler%2030d0f8d8d1fd806cbfa9d64af39bd0c6.md)

[最小堆](最小堆%2030d0f8d8d1fd80dcb3b8cdc795d1c733.md)

[React 中的位运算](React%20中的位运算%2030d0f8d8d1fd80e7b2baef0b281d454d.md)

[**Reconciler**](Reconciler%2030d0f8d8d1fd802894c7d09fa174498f.md)

[diff 算法](diff%20算法%2030d0f8d8d1fd805f8c3ad77a03e9f3d5.md)

[commit 工作流程](commit%20工作流程%2030e0f8d8d1fd807faa4ddaa3672f12b9.md)

[lane模型](lane模型%2030f0f8d8d1fd80b9af51c3659244b5b4.md)

[React 中的事件](React%20中的事件%2030f0f8d8d1fd8032be48fe0e093838c0.md)

[Hooks原理](Hooks原理%2030f0f8d8d1fd80e3b7a5e6941b334591.md)

[effect相关hook](effect相关hook%2030f0f8d8d1fd80e0b55ef64a99bfb681.md)

[useCallback和useMemo](useCallback和useMemo%203100f8d8d1fd80b88bb0e0a0fc8ede58.md)

[useRef](useRef%203100f8d8d1fd806291d8d21de91d8e2e.md)

[Update](Update%203100f8d8d1fd8097aff9da11f16602b0.md)