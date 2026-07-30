# 函数的本质就是对象

**函数的本质就是对象**

> 某些教程中，将构造函数称之为**构造器**
**所有的对象都是通过关键字new出来的，new 构造函数()**
> 
> 
> ```jsx
> // {} 语法糖
> const obj = { x: valX };
> 
> const obj = new Object();
> 
> const obj = Object.create(Object.prototype);
> obj.x = valX
> 
> // [] 语法糖
> const arr = [ 'hello' ];
> 
> const arr = new Array();
> 
> const arr = Object.create(Array.prototype);
> arr[0] = 'hello';
> arr.length = 1;
> ```
> 

**所有的函数，作为对象，都是通过`new Function`创建**。

```jsx
var sum = new Function("a", "b", "return a+b");
console.log(typeof sum); // function
console.log(sum(3, 5));
```

> **Function → 产生函数对象 → 创造普通对象**
> 

由 V8引擎 在一开始就创建Function构造函数，挂载到global上，把所有后续函数 Map 的 constructor 指向它

https://github.com/ceilf6/Lab/commit/4d158024688aaf793b98ae4136445d96623bcb71

```css
V8 启动
  ↓
Genesis::InitializeGlobal()
  ↓
InstallFunction(global, "Function", ..., Builtin::kFunctionConstructor)
  ├─ CreateFunction() → 分配一个 JSFunction 堆对象
  ├─ JSObject::AddProperty(global, "Function", fn)  ← 写入全局
  ↓
InstallWithIntrinsicDefaultProto(fn, FUNCTION_FUNCTION_INDEX)
  └─ NativeContext[FUNCTION_FUNCTION_INDEX] = fn    ← 写入固定 slot

所有函数 Map 的 constructor = fn                    ← SetConstructor
Function.prototype.apply/bind/call = 内置函数        ← SimpleInstallFunction

──────────────
运行时 new Function('body')
  ↓ Builtin::kFunctionConstructor
  ↓ CreateDynamicFunction → 字符串拼接 → Compiler::GetFunctionFromString
  ↓ 编译 → 分配 JSFunction(kYoung) → 返回
```

由于函数本身就是对象，因此函数中，可以拥有各种属性。

## 包装类

JS**为了增强原始类型的功能，为boolean、string、number分别创建了一个构造函数**：

1. Boolean
2. String
3. Number

如果语法上，将原始类型**当作对象使用时**（一般是在使用属性时），JS会自动在该位置利用对应的构造函数，**创建对象来访问原始类型的属性**。

```jsx
let num = new Number(3.14159);
num = num.toFixed(2);
console.log(num)
// number 不是原始类型吗，为什么可以使用方法
// 本质就是包装类中的方法
// 还有像 string的 .length 
这些都被称为 成员方法 或 实例方法
```

> 成员属性（方法）、实例属性（方法）：表示该属性是**通过构造函数创建的实例对象调用的**。

**静态**属性（方法）、类属性（方法）：表示该属性是**通过构造函数本身调用**的，例如 Number.isNaN( ) ，Array.isArray( ) ，call ，apply ，bind
是挂载在 **构造函数 这个对象**上的方法
> 
> 
> ![image.png](工程师沉淀/JS/函数的本质就是对象/image.png)
> 

```jsx
const a1 = 123;
const a2 = new Number(123);
console.log('a1 == a2', a1 == a2)
// 包装类会自动隐式转换
console.log('a1 === a2', a1 === a2)
console.log('a1', typeof a1)
console.log('a2', typeof a2)
```

![image.png](工程师沉淀/JS/函数的本质就是对象/image%201.png)

> 类：在JS中，可以认为，**类就是构造函数 + 原型**
>