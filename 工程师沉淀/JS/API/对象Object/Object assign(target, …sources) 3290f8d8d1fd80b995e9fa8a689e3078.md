# Object.assign(target, …sources)

![image.png](Object%20assign(target,%20%E2%80%A6sources)/image.png)

**把一个或多个源对象的可枚举自有属性，复制到目标对象上**，并返回目标对象。

---

# **1. 基本语法**

```
Object.assign(target, ...sources)
```

- target：目标对象
- sources：一个或多个源对象
- 返回值：target 本身

示例：

```
const target = { a: 1 };
const source = { b: 2 };

const result = Object.assign(target, source);

console.log(result); // { a: 1, b: 2 }
console.log(target); // { a: 1, b: 2 }
console.log(result === target); // true
```

这说明它会**直接修改目标对象**，不是生成一个全新的独立对象再返回。

---

# **2. 最常见的用途**

## **2.1 合并对象**

```
const obj1 = { a: 1 };
const obj2 = { b: 2 };
const obj3 = { c: 3 };

const merged = Object.assign({}, obj1, obj2, obj3);

console.log(merged); // { a: 1, b: 2, c: 3 }
```

这里用 {} 作为目标对象，避免修改原对象。

---

## **2.2 覆盖同名属性**

后面的源对象会覆盖前面的属性：

```
const result = Object.assign(
  {},
  { a: 1, b: 2 },
  { b: 20, c: 30 }
);

console.log(result); // { a: 1, b: 20, c: 30 }
```

规则是：**后写覆盖前写**。

---

## **2.3 克隆对象（浅拷贝）**

```
const obj = { name: "Alice", age: 18 };
const copy = Object.assign({}, obj);

console.log(copy); // { name: "Alice", age: 18 }
```

但这里要特别注意：它只是**浅拷贝**。

---

# **3. 浅拷贝是什么意思**

如果对象里有嵌套对象，Object.assign() 不会递归复制内部对象，只会复制引用。

```
const obj = {
  name: "Alice",
  info: {
    city: "Beijing"
  }
};

const copy = Object.assign({}, obj);

copy.info.city = "Shanghai";

console.log(obj.info.city);  // Shanghai
console.log(copy.info.city); // Shanghai
```

原因是：

- 第一层属性被复制了
- info 这个属性的值是一个对象
- 复制的是这个对象的**引用地址**
- 所以两边指向同一个内部对象

---

# **4. 它复制哪些属性**

Object.assign() 只复制：

- **源对象自身的属性**
- **可枚举属性（enumerable）**

不会复制：

- 原型链上的属性
- 不可枚举属性

示例：

```
const proto = { inherited: 1 };
const obj = Object.create(proto);

obj.own = 2;

const result = Object.assign({}, obj);

console.log(result); // { own: 2 }
```

这里 inherited 在原型上，所以不会被复制。

---

# **5. Symbol 属性会不会复制**

会。只要是 **可枚举的 Symbol 属性**，也会被复制。

```
const sym = Symbol("id");

const source = {
  name: "Tom",
  [sym]: 123
};

const target = Object.assign({}, source);

console.log(target.name);   // Tom
console.log(target[sym]);   // 123
```

---

# **6. 对 getter / setter 的影响**

Object.assign() 复制的是**取值后的结果**，不是完整的属性描述符。

看这个例子：

```
const source = {
  get name() {
    return "Alice";
  }
};

const target = Object.assign({}, source);

console.log(target.name); // Alice
```

这里并不是把 getter 本身复制过去了，而是：

1. 读取 source.name
2. 得到 "Alice"
3. 再把 "Alice" 作为普通属性赋给 target

所以 target.name 变成了一个普通数据属性。

如果你想连属性描述符一起复制，要用：

```
Object.getOwnPropertyDescriptors()
Object.defineProperties()
```

例如：

```
const source = {
  get name() {
    return "Alice";
  }
};

const target = {};
Object.defineProperties(target, Object.getOwnPropertyDescriptors(source));

console.log(target.name); // Alice
```

这样 getter 才会被完整保留。

---

# **7. 和展开运算符**

# **...**

# **的区别**

很多时候你会看到：

```
const newObj = { ...obj1, ...obj2 };
```

它和 Object.assign({}, obj1, obj2) 很像。

## **相同点**

- 都能合并对象
- 都是浅拷贝
- 后面的属性会覆盖前面的属性

## **常见理解**

```
const a = { x: 1 };
const b = { y: 2 };

const r1 = Object.assign({}, a, b);
const r2 = { ...a, ...b };

console.log(r1); // { x: 1, y: 2 }
console.log(r2); // { x: 1, y: 2 }
```

## **实际开发中怎么选**

- 想表达“合并对象”，通常更常用 ...
- 想明确“把属性拷贝到某个已有对象上”，可以用 Object.assign()

例如：

```
Object.assign(existingObject, updates);
```

这个语义很直接：**把更新项打到已有对象上**。

---

# **8. 参数不是对象时会怎样**

## **8.1**

## **target**

## **不能是**

## **null**

## **或**

## **undefined**

```
Object.assign(null, { a: 1 });      // 报错
Object.assign(undefined, { a: 1 }); // 报错
```

因为目标对象必须可转换为对象。

---

## **8.2 源对象是**

## **null**

## **或**

## **undefined**

## **会被跳过**

```
const result = Object.assign({}, null, undefined, { a: 1 });

console.log(result); // { a: 1 }
```

这不会报错。

---

## **8.3 基本类型会被装箱**

```
const result = Object.assign({}, "abc");

console.log(result); // { '0': 'a', '1': 'b', '2': 'c' }
```

字符串会被当成类数组对象处理，因为它有可枚举的索引属性。

而数字、布尔值通常没什么可复制的可枚举属性：

```
console.log(Object.assign({}, 123));   // {}
console.log(Object.assign({}, true));  // {}
```

---

# **9. 常见坑点**

## **9.1 会修改目标对象**

```
const target = { a: 1 };
Object.assign(target, { b: 2 });

console.log(target); // { a: 1, b: 2 }
```

很多人以为它不改原对象，这是误区。

---

## **9.2 不是深拷贝**

```
const obj = { nested: { x: 1 } };
const copy = Object.assign({}, obj);

copy.nested.x = 999;
console.log(obj.nested.x); // 999
```

---

## **9.3 遇到异常时可能只复制一部分**

如果复制过程中报错，前面成功复制的属性不会回滚。

```
const target = {};

const source1 = { a: 1 };

const source2 = {
  get b() {
    throw new Error("boom");
  }
};

try {
  Object.assign(target, source1, source2);
} catch (e) {
  console.log(e.message); // boom
}

console.log(target); // { a: 1 }
```

说明它不是“事务式”的，不会失败就全撤销。

---

# **10. 实战场景**

## **10.1 给配置项设置默认值**

```
const defaults = {
  host: "localhost",
  port: 3000,
  debug: false
};

const options = {
  port: 8080
};

const config = Object.assign({}, defaults, options);

console.log(config);
// { host: 'localhost', port: 8080, debug: false }
```

---

## **10.2 在已有对象上打补丁**

```
const user = {
  name: "Tom",
  age: 20
};

Object.assign(user, { age: 21, city: "Shanghai" });

console.log(user);
// { name: 'Tom', age: 21, city: 'Shanghai' }
```

---

## **10.3 React/前端状态处理中的老写法**

```
const newState = Object.assign({}, prevState, {
  loading: true
});
```

现在更常写成：

```
const newState = {
  ...prevState,
  loading: true
};
```

---

# **11. 和深拷贝方案的区别**

如果你真正需要深拷贝，不应使用 Object.assign()。

可考虑：

## **structuredClone()**

现代环境推荐：

```
const deepCopy = structuredClone(original);
```

它适合多数普通深拷贝场景。

## **JSON.parse(JSON.stringify(obj))**

老办法，但有局限：

- 丢失 undefined
- 丢失函数
- 丢失 Symbol
- Date 会变字符串
- 循环引用会报错

---

# **12. 一句话总结**

Object.assign() 的核心特点：

- 用来把源对象属性复制到目标对象
- **浅拷贝**
- **会修改目标对象**
- 只复制**自身可枚举属性**
- 后面的同名属性会覆盖前面的

---

# **13. 推荐记忆版**

可以记成这句：

> Object.assign() = “把几个对象的第一层属性，依次拷贝到目标对象里”
> 

---

# **14. 面试高频回答模板**

如果面试官问你 Object.assign()，你可以这样答：

```
Object.assign(target, ...sources)
```

它用于把多个源对象的可枚举自有属性复制到目标对象，并返回目标对象。

它是浅拷贝，不会递归复制嵌套对象；如果属性同名，后面的会覆盖前面的；它会直接修改 target。

常用于对象合并、默认配置、对象克隆（浅拷贝）。

---

如果你愿意，我也可以继续给你讲：

**Object.assign() 和对象展开运算符 ... 的底层区别**，或者 **出几道面试题带解析**。