# 深入认识setState

setState，它对状态的改变，**可能**是异步的

> 如果改变状态的代码处于某个HTML元素的**事件**中，则其是**异步的**，否则是同步
> 

[状态同步更新](../../TS/TS+React+vite%203200f8d8d1fd80b9b5c4f71b46c5cfe3.md) 

因为 React 考虑到事件中可能会对状态进行多次更新，如果不 异步、合并的话，那么会多次渲染导致性能耗散

像 setState(newState) 直接覆盖的合并是调度层的合并，是 lanes+Scheduler 的作用，与遍历updateQueue无关

而像 setState(state+1) 这种才是遍历updateQueue后合并

如果遇到某个事件中，需要同步调用多次，需要使用函数的方式得到最新状态

最佳实践：

1. 把所有的setState当作是异步的
2. 永远不要信任setState调用之后的状态
3. 如果要使用**改变之后的状态**，需要使用**回调函数**（**setState的第二个参数**）
    
    ```jsx
    this.setState(
        {
            num: this.state.num - 1
        }
        , // setState的第二个参数：状态完成之后的回调函数
        () => {
            console.log("=== num 状态完成之后的回调函数", this.state.num)
        })
    ```
    
4. 如果新的状态要根据之前的状态进行运算、链式作用，需要**使用函数的方式**改变状态（setState的第一个参数）
    
    React 内部会维护一个任务队列
    
    ```jsx
    this.setState(prev => {
        // setState 第一个参数也可以是一个函数
        // 参数prev表示当前的状态
        // 该函数的返回结果，会混合（覆盖）掉之前的状态
        // 该函数是异步执行
        return {
            num: prev.num - 1
        }
    })
    this.setState(prev => {
        return {
            num: prev.num - 1
        }
    })
    // 并且 React会对异步的setState进行优化，将多次setState进行合并
    // 所以一次点击虽然事件中有三次 setState ，但是只会有一次 render
    ```
    

React会对**异步**的setState进行优化，将多次setState进行**合并**（将**多次状态改变完成后，再统一对state进行改变**，然后触发render）

所以一次点击虽然事件中有三次 setState ，但是只会有一次 render