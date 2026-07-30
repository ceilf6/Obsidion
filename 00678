# useForm

默认情况下，Form 对在里面的所有的 Input 都传递了 handleChange, 当其中一个变化时，直接修改了 Form 的 state, 那么整个 Form 、 Form 中所有的 Input 都会 re-rende

useForm 内部维护了两个对象，一个是字段值存储 **_formValues** ，还有一个是表单状态存储 **_formState**

1. **字段级**UI（例如输入框）：当用户 input 的时候，会引发 **register** 返回的 **onChange** 事件，其内部更新了 _formValues ， **subjects** **广播**字段级变更（类似于React主动调度），仅订阅了相关字段的组件会调用其内部对应字段的 setState ，从而触发最小范围的 **Fiber调度**
2. **表单状态级**UI（例如loading态、错误提示等）：当用户提交表单等等 _formState 变化的时候，**subjects 广播**表单状态变更，在 **useFormState** 的**订阅回调即观察者的update**（类似于Vue的细粒度）中检查组件的**依赖收集**是否访问过该表单状态，如有则调用 setState ，从而只渲染真正用到该属性的组件。
    
    其中依赖收集是来自 _formState 上的 **Proxy** 包装挟持，对应组件在访问 _formStates 的属性时候被其记录了
    

上面两者结合实现大表单的最小限度的 re-render