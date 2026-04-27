# plugin和loader区别

loader 用于转换**单个**模块文件

其本质是一个用于**转换**内容、输入输出都是字符串的**函数**

```jsx
module.exports = function(source) {
  return transformedSource
}
```

plugin 会**跟随**整个打包流程，在适当时机执行操作

其本质是一个带有apply方法的对象

通过在 apply方法中接入了webpack**钩子**函数

一般会写成一个 类 然后去实例化

```jsx
class MyPlugin {
  apply(compiler) {
    compiler.hooks.emit.tap("MyPlugin", (compilation) => {
      // 在打包输出前做点事
    })
  }
}

var plugin = new MyPlugin();
```

webpack内部流程

```jsx
1. 解析模块依赖图
2. 调用 loader 转换模块文件
3. 生成 chunk
4. 优化
5. 输出资源
```

loader 只参与了第二步转换模块文件，而 plugin 会参与所有流程