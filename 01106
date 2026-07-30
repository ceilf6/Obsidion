# React.createContext

组件树，数据需要自顶向下流动，那么上面的组件会创建上下文，存储流动的数据

数据来源

1. 状态：自己管理
2. 属性
3. 上下文

上下文：Context，表示做某一些事情的**环境**

React中的上下文特点：

1. 当某个组件创建了上下文后，上下文中的数据，会被**其所有后代组件共享**
2. 如果某个组件依赖了上下文，会导致该组件**不再纯粹**（纯粹：外部数据仅来源于属性props）
3. 一般情况下，用于第三方组件（**通用**组件）

## 旧的API

https://github.com/ceilf6/Lab/commit/ef0729e6273c145bc97274df641a477404f95531

16 之前

**创建上下文**

只有类组件才可以创建上下文

1. 给类组件书写**静态属性 childContextTypes，使用该属性对上下文中的数据类型进行约束**
2. 添加实例方法 **getChildContext**，**该方法返回的对象，即为上下文中的数据**，该数据必须满足类型约束，**该方法会在每次render之后运行**。

**拿到上下文中的数据**

要求：如果要使用上下文中的数据，组件必须有一个**静态属性 contextTypes，该属性描述了需要获取的上下文中的数据类型**

这样就能在不纯粹的时候理清思路

1. 可以在组件的构造函数中，通过**第二个参数**，获取上下文数据
2. **从组件的context属性中获取**
    
    this.content 取的是来自上层的、自身的上下文取不到
    
3. 在函数组件中，通过**第二个参数**，获取上下文数据

**上下文的数据变化**

上下文中的数据**不可以直接变化，最终都是通过状态改变**

在上下文中加入一个处理函数，可以用于后代组件更改上下文的数据

## 新版API

https://github.com/ceilf6/Lab/commit/350f5333144244f0f57539847bf2950c27ad263e

旧版API存在严重的**效率**问题，并且容易导致**滥用**

**创建上下文**

上下文是一个**独立于组件**的**对象**，该对象通过 **React.createContext**(默认值) 创建

返回的是一个**包含两个属性**的对象

生产者消费者模式

> 一个或多个“**生产者**”负责生产数据
> 
> 
> 一个或多个“**消费者**”负责消费数据
> 
> 中间通过“缓冲区”解耦
> 
1. Provider属性：生产者。一个组件，该**组件会创建一个上下文**，该组件有一个value属性，通过该属性，可以为其数据赋值
    
    ```jsx
    import React from 'react'
    
    const ctx = React.createContext() // {
    //     name: 'ceilf6',
    //     num: 100
    // })
    
    console.log(ctx)
    
    // NewContext -> Provider -> ...
    // 由上下文对象的 Provider 属性组件提供
    export default class NewContext extends React.Component {
        state = {
            name: 'ceilf6',
            num: 100
        }
        render() {
            // const Provider = ctx.Provider
            return (
                <ctx.Provider value={this.state}>
                    {/* {{ name: 'ceilf7' }}> */}
                    <div></div>
                </ctx.Provider>
            )
        }
    }
    ```
    
    **同一个Provider，不要用到多个组件**中，如果需要在其他组件中使用该数据，应该考虑将数据提**升到更高**的层次
    
2. Consumer属性：后续讲解

**使用上下文中的数据**

1. 在**类**组件中，直接使用**this.context**获取上下文数据
    
    要求：必须拥有静态属性 **contextType** , **应赋值为目标数据源上下文**
    
    ```jsx
    class Grandson extends React.Component {
        static contextType = ctx
    ```
    
2. 在**函数组件**中，需要使用**Consumer**来获取上下文数据（显式使用 ctx1.Comsumer ，不再是旧版的就近原则）
    1. Consumer是一个**组件**
    2. 它的子节点，是一个函数（它的props.children即写在中间需要传递一个函数）

**注意细节**

https://github.com/ceilf6/Lab/commit/22ff1e07f6ba64fbccc8489418dc2eae83bd2367

setState 被调用时，创建的是一个新对象（即使什么都没有变），那么上下文在比较时（通过Object.is比较引用内存地址）会判断二者不一致、导致该上下文Context 数据变化时，所有消费者强制更新直接不运行 shouldComponentUpdate 、性能优化失败

解决方案：包一层 ctx 后，后面更新 setState({}) => 只影响了 state 但是内部的 ctx 的地址没有变化