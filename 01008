# Vue实例成员属性

只有Vue实例有，Vue构造函数是没有的

# $mount

和设置 el 配置一样，用于挂载 Vue 实例

# $emit

在组件中抛出一个事件

# $el

组件渲染出来的DOM根元素

# $refs

当前组件持有的引用，来自于 ref 属性指定的引用

[ref](%E5%AE%9E%E8%B7%B5%20toast%E6%B6%88%E6%81%AF%E6%8F%90%E7%A4%BA%202fd0f8d8d1fd80009334d154ca460007.md) 

# $listeners

[父组件异步处理返回子组件](组件通信%202fc0f8d8d1fd8054999fedb48cb0dad9.md) 

`$listeners`是`vue`的一个实例属性，它用于**获取父组件传过来的所有事件函数**

```html
<!-- 父组件 -->
<Child @event1="handleEvent1" @event2="handleEvent2" />
```

```jsx
// 子组件
this.$listeners // { event1: handleEvent1, event2: handleEvent2 }
```

> `$emit`和`$listeners`通信的异同
> 
> 
> 相同点：均可实现子组件向父组件传递消息
> 
> 差异点：
> 
> - `$emit`更加符合单向数据流，子组件仅发出通知，由父组件监听做出改变；而`$listeners`则是在子组件中直接使用了父组件的方法。
>     
>     $listeners 类似于 React父组件下放权力一样
>     
> - 调试工具可以监听到子组件`$emit`的事件，但无法监听到`$listeners`中的方法调用
>     
>     因为 emit 是有上报的，但是 listeners 是直接调用的方法
>     
> - 由于`$listeners`中可以获得传递过来的方法，因此调用方法可以得到其返回值。但`$emit`仅仅是向父组件发出通知，无法知晓父组件处理的结果

> 对于上述中的第三点，可以在`$emit`中传递回调函数来解决
> 
> 
> 父组件：
> 
> ```
> <template>
> 	<Child @click="handleClick" />
> </template>
> 
> <script>
>   import Child from "./Child"
> 	export default {
>     components:{
>       Child
>     },
>     methods:{
>       handleClick(data, callback){
>         console.log(data); // 得到子组件事件中的数据
>         setTimeout(()=>{
>           callback(1); // 一段时间后，调用子组件传递的回调函数
>         }, 3000)
>       }
>     }
>   }
> </script>
> ```
> 
> 子组件：
> 
> ```
> <template>
> 	<button @click="handleClick">
>     click
>   </button>
> </template>
> 
> <script>
> 	export default {
>     methods:{
>       handleClick(){
>         this.$emit("click", 123, (data)=>{
>           console.log(data); // data为父组件处理完成后得到的数据
>         })
>       }
>     }
>   }
> </script>
> ```
> 

# $event

拿到事件参数

例如 $event.target.value 拿到表单新的输入

[v-model 受控组件](%E6%A8%A1%E7%89%88%202f90f8d8d1fd801a843bc6987ad31546.md) 

# $on

监听事件

# $off

取消监听器

```jsx
// 观察者列表
// 事件: [回调函数] 如 { "event1": Set(handler1,handler2) }
const listeners = {};

export default {
    // 监听某一个事件
    $on(eventName, handler) {
        if (!listeners[eventName]) listeners[eventName] = new Set(); // 内部通过 Set 防止重复
        listeners[eventName].add(handler)
    },
    // 取消 handler 对 eventName 事件的监听
    $off(eventName, handler) {
        if (!listeners[eventName]) return
        listeners[eventName].delete(handler)
    },
    // 触发事件
    $emit(eventName, ...args) { // 往事件总线上抛事件相关的数据
        if (!listeners[eventName]) return
        for (const handler of listeners[eventName]) handler(...args)
    }
}
```