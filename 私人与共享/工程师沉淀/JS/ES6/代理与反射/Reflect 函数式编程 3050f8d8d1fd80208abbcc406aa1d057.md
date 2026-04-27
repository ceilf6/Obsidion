# Reflect 函数式编程

https://github.com/ceilf6/Lab/commit/19d0ecd467ecac47565c7aa47c0990b6cab7a9d7

1. Reflect是什么？

ES6新增 Reflect是一个**内置的JS对象**，它提供了一系列方法，可以让开发者通过调用这些方法，访问一些JS底层功能

由于它类似于其他语言的**反射**，因此取名为Reflect

1. 它可以做什么？

使用Reflect可以实现诸如 属性的赋值与取值、调用普通函数、调用构造函数、判断属性是否存在与对象中  等等功能

1. 这些功能不是已经存在了吗？为什么还需要用Reflect实现一次？

有一个重要的理念，在ES5就被提出：**减少魔法、让代码更加纯粹**

以 **API** 出现，**而不是特殊的语法**

```jsx
plus(add(3)(2)(1))(100)
```

这种理念很大程度上是受到**函数式编程**的影响

ES6进一步贯彻了这种理念，它认为，对属性内存的控制、原型链的修改、函数的调用等等，这些都属于底层实现，属于一种魔法，因此，需要将它们提取出来，**形成一个正常的API，并高度聚合到某个对象中**，于是，就造就了Reflect对象

因此，你可以看到Reflect对象中有很多的API都可以使用过去的某种语法或其他API实现。

1. 它里面到底提供了哪些API呢？
- Reflect.set(target, propertyKey, value): 设置对象target的属性propertyKey的值为value，等同于给对象的属性赋值
- Reflect.get(target, propertyKey): 读取对象target的属性propertyKey，等同于读取对象的属性值
- Reflect.apply(func, thisArgument, argumentsList)：调用一个指定的函数，并绑定this和参数列表。等同于**函数调用**
    
    找到函数的对象内存空间，然后建立上下文…
    
- Reflect.deleteProperty(target, propertyKey)：删除一个对象的属性
- Reflect.defineProperty(target, propertyKey, attributes)：类似于Object.defineProperty，不同的是如果配置出现问题，返回false而不是报错
- Reflect.construct(target, argumentsList)：用构造函数的方式创建一个对象
    
    即 **new**
    
- Reflect.has(target, propertyKey): 判断一个对象是否拥有一个属性
    
    即 **in** 
    

其他API：[https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect)