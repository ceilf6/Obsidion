# index

- 用 function***** 定义生成器函数
- 用 yield 暂停执行并返回一个值
- 调用后不会立刻执行函数体，而是返回一个迭代器对象
- 可以通过 next() 一步步恢复执行

**迭代器协议**要求的是：

1. 对象有 **next()** 方法
2. next() 返回一个对象
3. 这个返回对象里至少有：
    - **value**
    - **done**

## 场景

- 实现迭代器模式[    // function*
    // Generator 作为具体迭代器：按顺序逐个产出集合元素
    *createIterator(): Generator<Book, void, unknown> {
        for (const book of this.books) {
            yield book;
        }
    }
    
    
    const iterator = collection.createIterator();
    let result = iterator.next();
    while (!result.done) { // 迭代器对象还没有 done
        console.log(result.value);
        result = iterator.next();
    }](../../../%E6%A8%A1%E5%BC%8F/%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F/%E8%A1%8C%E4%B8%BA%E5%9E%8B%E6%A8%A1%E5%BC%8F/%E8%BF%AD%E4%BB%A3%E5%99%A8%E6%A8%A1%E5%BC%8F%2032a0f8d8d1fd8006ae0be409c358b8a4.md)
- 在 co 库中通过 generator 实现异步的等待