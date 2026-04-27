# splice, slice

**slice 不会影响原数组**

**splice 会直接修改原数组**

# splice

## **1️⃣ 基本语法**

```
array.splice(start, deleteCount, item1, item2, ...)
```

参数：

| **参数** | **含义** |
| --- | --- |
| start | **开始操作的索引** |
| deleteCount | 要**删除**的元素个数 |
| item1,item2... | 要插入的元素 |

返回值：

- 返回 **被删除的元素数组**

---

# **2️⃣ 删除元素**

```
const arr = [1,2,3,4,5]

arr.splice(1,2)

console.log(arr)
```

结果

```
[1,4,5]
```

解释：

```
index:  0 1 2 3 4
array: [1 2 3 4 5]

从 index=1 开始删除2个
删除：2,3
```

返回值：

```
[2,3]
```

---

# **3️⃣ 插入元素**

删除个数设为 **0**

```
const arr = [1,2,3]

arr.splice(1,0,"a","b")

console.log(arr)
```

结果

```
[1,"a","b",2,3]
```

解释

```
index: 0 1 2
原数组: [1 2 3]

在 index=1 插入
```

---

# **4️⃣ 替换元素**

```
const arr = [1,2,3,4]

arr.splice(1,2,"a","b")

console.log(arr)
```

结果

```
[1,"a","b",4]
```

解释

```
删除 2,3
插入 a,b
```

---

# **5️⃣ 常见用法总结**

### **删除**

```
arr.splice(index,1)
```

删除指定位置元素

---

### **删除到末尾**

```
arr.splice(index)
```

---

### **插入**

```
arr.splice(index,0,item)
```

---

### **替换**

```
arr.splice(index,1,newItem)
```

---

# slice

slice 是 **JavaScript 数组（Array）的一个方法**，用于 **截取数组的一部分**。

和 splice 最大的区别是：

> **slice 不会修改原数组（非破坏性 API）**
> 

---

# **1️⃣ 基本语法**

```
array.slice(start, end)
```

参数：

| **参数** | **含义** |
| --- | --- |
| start | 开始索引（包含） |
| end | 结束索引（不包含） |

返回值：

- 返回 **一个新数组**

---

# **2️⃣ 基本示例**

```
const arr = [1,2,3,4,5]

const result = arr.slice(1,4)

console.log(result)
```

结果

```
[2,3,4]
```

解释

```
index: 0 1 2 3 4
array: 1 2 3 4 5

slice(1,4)
取 index 1 ~ 3
```

---

# **3️⃣ 不传参数**

```
const arr = [1,2,3]

const copy = arr.slice()

console.log(copy)
```

结果

```
[1,2,3]
```

常见用途：

> **浅拷贝数组**
> 

---

# **4️⃣ 只传 start**

```
const arr = [1,2,3,4,5]

arr.slice(2)
```

结果

```
[3,4,5]
```

等价于

```
index >= 2
```

---

# **5️⃣ 负数索引**

slice 支持 **负数索引**

```
const arr = [1,2,3,4,5]

arr.slice(-2)
```

结果

```
[4,5]
```

解释

```
-1 = 最后一个
-2 = 倒数第二个
```

---

# **6️⃣ 不会修改原数组**

```
const arr = [1,2,3,4]

arr.slice(1,3)

console.log(arr)
```

结果

```
[1,2,3,4]
```

---

# **7️⃣ 常见用途**

### **复制数组**

```
const copy = arr.slice()
```

---

### **取前 n 个**

```
arr.slice(0,n)
```

---

### **取后 n 个**

```
arr.slice(-n)
```

---

# **8️⃣ 和 splice 对比（面试必问）**

| **API** | **是否修改原数组** | **功能** |
| --- | --- | --- |
| splice | ✅ 修改 | 删除 / 插入 / 替换 |
| slice | ❌ 不修改 | 截取 |

示例：

```
arr.splice(1,2)
```

删除元素

```
arr.slice(1,3)
```

截取元素

---

# **9️⃣ 底层复杂度**

slice 时间复杂度：

```
O(n)
```

原因：

- 需要 **复制一段数组**

---

💡 一个很多人不知道的点：

slice **不仅是 Array API**，

它还是 **String API**。

```
const str = "hello"

str.slice(1,4)
```

结果

```
"ell"
```

---

如果你愿意，我可以再给你讲一个 **非常重要但很多人不知道的技巧：**

```
Array.prototype.slice.call(arguments)
```

这个是很多框架源码里常见的写法（React / Vue / lodash 都出现过）。