# React

- 许多 FiberNode对象 通过链表串联用于表示 虚拟树
    
    **child 指向子元素，sibling 指向兄弟元素，return 指向父元素**
    
    - hook对象串联成的 链表用于实现一个 FiberNode函数组件 的**状态变更**
        
        **FiberNode.memoizedState** 存储其 hook链表 的头节点
        
        - 每一个 hook 又有自己的一个 updateQueue 链表队列，在遍历更新队列后 ⇒ state

在状态更新时，对应 hook 的 updateQueue 入队一个 update对象（数据层：发生了什么更新） ，然后对应优先级 lane 标记到 hook 对应的 FiberNode 上，然后在 Reconciler 的 归阶段即在completeWork 冒泡到根上（标记层：哪些地方脏了，优先级是什么），接着请求调度，那么 Scheduler 会根据 root 上的 lanes 决定要不要创建 / 更新一个 Scheduler task 到 MessageChannel 驱动宏任务循环

memoize 计算机缓存结果

memo ize

[React核心概念](React/React%E6%A0%B8%E5%BF%83%E6%A6%82%E5%BF%B5%202ff0f8d8d1fd80299d06ce91c0033245.md)

> 官网：[https://react.docschina.org/](https://react.docschina.org/)
> 

## 什么是React？

React是由**Facebook**研发的、用于**解决UI复杂度**的开源**JavaScript库**，目前由React联合社区维护。

> 它不是框架，只是为了解决UI复杂度而诞生的一个库
> 

像 Vue 框架带有侵入性，限定了开发规则

React 作为库侵入性小，灵活、和第三方融合方便，所以生态相对更好

## React的特点

- 轻量：React的开发版所有源码（包含注释）仅3000多行
- 原生：所有的React的代码都是用原生JS书写而成的，不依赖其他任何库
- 易扩展：React对代码的封装程度较低，也没有过多的使用魔法（像Vue就用了defineProperty），所以React中的很多功能都可以扩展。
- 不依赖宿主环境：React只依赖原生JS语言，**不依赖任何其他东西，包括运行环境**。因此，它可以被轻松的**移植**到浏览器、桌面应用、移动端。
- 渐近式：React并非框架，对整个工程没有强制约束力。这对与那些已存在的工程，可以逐步的将其改造为React，而不需要全盘重写。
- 单向数据流：所有的数据**自顶而下的流动**
- 用**JS代码声明**界面
- 组件化

## 对比Vue

| 对比项 | Vue | React |
| --- | --- | --- |
| 全球使用量 |  | ✔ |
| 国内使用量 | ✔ |  |
| 性能 | ✔ | ✔ |
| 易上手 | ✔ |  |
| 灵活度 |  | ✔ |
| 大型企业 |  | ✔ |
| 中小型企业 | ✔ |  |
| 生态 |  | ✔ |

## 学习路径

整体原则：熟悉API --> 深入理解原理

1. React
    1. 基础：掌握React的基本使用方法，有能力制作各种组件，并理解其基本运作原理
    2. 进阶：掌握React中的一些黑科技，提高代码质量
2. React-Router：相当于vue-router
3. Redux：相当于Vuex
    1. Redux本身
    2. 各种中间件
4. 第三方脚手架：umi
5. UI库：Ant Design，相当于Vue的Element-UI 或 IView
6. 源码部分
    1. React源码分析
    2. Redux源码分析

## 关于课程

- demo关键字：课程名称前有**demo**字样的，为一个小练习，需要同学听完讲解后自行独立完成
- 扩展关键字：课程名称前有**扩展**字样的，为选修内容，没有掌握不会影响后面的学习
- 关于源代码：本门课所有源代码均使用git管理，每节课的代码为独立分支，但某些文件夹和文件不属于源代码管理范畴。
- 关于npm：本门课所有的第三方库安装，均使用yarn

yarn 有缓存

# Hello world

## ReactDOM.render(显示内容, 容器)

## React.createElement

来自于核心库

创建一个**React元素**，称作虚拟DOM，本质上是一个**对象**

1. 参数1：元素类型，如果是字符串，一个普通的HTML元素；也可以传递组件
2. 参数2：元素的**属性**，一个**对象 { att: val }**
3. 后续参数：元素的子节点

## JSX

JS的扩展语法，需要使用babel进行转义。

```jsx
<body>
    <div id="root"></div>
    <div id="app"></div>

    <!-- 跨域了，虽然 script,img... 限制较小，加上 crossorigin 查看详细报错 -->
    <!-- React的核心库，与宿主环境无关 -->
    <script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
    <!-- 依赖核心库，将核心的功能与页面结合 -->
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
    <script>
        // 显示内容, 容器
        ReactDOM.render("nihao", document.getElementById("app"))

        // 创建元素 - 核心库
        var span = React.createElement("span", {}, "一个span元素");
        var h1 = React.createElement("h1", {
            shuxing: "value"
        }, "Hello", "World", span);
        console.log("=== React vDOMnode", h1)
        ReactDOM.render(h1, document.getElementById("root"));
    </script>

    <!-- Babel => 编译JSX -->
    <script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
    <div id="root2"></div>
    <script type="text/babel">
        const ele = <h1 title="第一个React元素">Hello World <span>一个span元素</span></h1>
        ReactDOM.render(ele, document.getElementById("root2"));
    </script>
</body>
```

# 开发环境配置

## VSCode配置

emmet配置：HTML, CSS 插件

```json
"javascript": "javascriptreact"
```

## VSCode插件安装

- ESLint：代码风格检查
- ES7 React/Redux/GraphQL/React-Native snippets：快速代码编写

## Chrome插件安装

React Developer Tools

[React进阶（零散、16前](React/React%E8%BF%9B%E9%98%B6%EF%BC%88%E9%9B%B6%E6%95%A3%E3%80%8116%E5%89%8D%203070f8d8d1fd806d8b26f1b5fc38b37c.md)

[React架构](React/React%E6%9E%B6%E6%9E%84%203180f8d8d1fd80e4ab52ec9c02f23ec6.md)

[性能优化](React/%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96%203170f8d8d1fd8023a866f5dfab7fd749.md)

[React源码](React/React%E6%BA%90%E7%A0%81%203180f8d8d1fd80b990eae3838c2040de.md)

[API](React/API%2031f0f8d8d1fd80ffaa5ecbf763968de4.md)