# 纯组件 PureComponent React.memo()

[4. React.memo / PureComponent](../%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96/4%20React%20memo%20PureComponent%203170f8d8d1fd80ac9693dec2ebf4bff9.md) 

在默认情况下，只要上层组件发生了变化，其**所有后代组件都需要重新渲染**

extends React.PureComponent

纯组件，用于**避免不必要的渲染**（**渲染-运行render函数**），从而提升效率

优化：如果一个组件的**属性和状态**，都没有发生变化，重新渲染组件是没有必要的

PureComponent是一个组件，如果某个组件继承自该组件，则该组件的**shouldComponentUpdate会进行优化，对属性和状态进行浅比较，如果相等则不会重新渲染**

**注意**

1. PureComponent进行浅比较
    1. 为了效率， 应该尽量使用PureComponent
    2. 要求不要改动之前的状态，永远是创建新的状态来覆盖之前的状态（Immutable，不可变对象）
    3. 有一个第三方JS库，Immutable.js, 它专门用于制作不可变对象
2. 函数组件，使用 **React.memo** 函数制作纯组件