# composition api

> 面试题：composition api相比于option api有哪些优势？
> 

不同于reactivity api，composition api提供的函数很多是与组件深度绑定的，不能脱离组件而存在。

# setup

一个组件运行一次，在挂载之前、this都是undefined

```jsx
// component
export default {
  setup(props, context){
    // 该函数在组件属性被赋值后立即执行，早于所有生命周期钩子函数
    // props 是一个对象，包含了所有的组件属性值
    // context 是一个对象，提供了组件所需的上下文信息
  }
}
```

context对象的成员

| 成员 | 类型 | 说明 |
| --- | --- | --- |
| attrs | 对象 | 同`vue2`的`this.$attrs` |
| slots | 对象 | 同`vue2`的`this.$slots` |
| emit | 方法 | 同`vue2`的`this.$emit` |

# 生命周期函数

| vue2 option api | vue3 option api | vue 3 composition api |
| --- | --- | --- |
| beforeCreate | beforeCreate | 不再需要，**代码可直接置于setup中** |
| created | created | 不再需要，**代码可直接置于setup中** |
| beforeMount | beforeMount | onBeforeMount |
| mounted | mounted | onMounted |
| beforeUpdate | beforeUpdate | onBeforeUpdate |
| updated | updated | onUpdated |
| beforeDestroy | ==改== beforeUnmount | onBefore**Unmount** |
| destroyed | ==改==unmounted | on**Unmount**ed |
| errorCaptured | errorCaptured | onErrorCaptured |
| - | ==新==renderTracked | onRenderTracked |
| - | ==新==renderTriggered | onRenderTriggered |

新增钩子函数说明： 

在 template ⇒ render 中渲染虚拟节点的时候会对响应式数据收集依赖

```jsx
render(){
	return createVNode(...)
}
```

在每收集到一个依赖就会触发一次 renderTracked

而 renderTriggered 在响应数据每变化一次就会触发一次

这两个生命周期钩子一般用于开发排查

| 钩子函数 | 参数 | 执行时机 |
| --- | --- | --- |
| renderTracked | DebuggerEvent | 渲染vdom收集到的每一次依赖时 |
| renderTriggered | DebuggerEvent | 某个依赖变化导致组件重新渲染时 |

DebuggerEvent:

- target: 跟踪或触发渲染的对象
- key: 跟踪或触发渲染的属性
- type: 跟踪或触发渲染的方式

# 面试题参考答案

面试题：composition api相比于option api有哪些优势？

> 从两个方面回答：
> 
> 1. 为了更好的**逻辑复用**和**代码组织**
>     
>     **开发粒度从组件级别 ⇒ 功能实现级别**，方便复用
>     
> 2. 更好的**类型推导**
>     
>     TS 的类型推导需要可预测性，但是 Vue2 有很多魔法、例如 this 在 methods 里面却指向了组件实例等等
>     
>     而 Vue3 是函数式编程思想，暴露了很多 API 输入输出更明确
>     

```
有了composition api，配合reactivity api，可以在组件内部进行更加细粒度的控制，使得组件中不同的功能高度聚合，提升了代码的可维护性。对于不同组件的相同功能，也能够更好的复用。
相比于option api，composition api中没有了指向奇怪的this，所有的api变得更加函数式，这有利于和类型推断系统比如TS深度配合。
```