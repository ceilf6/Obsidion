# vue/cli

> vue-cli: https://cli.vuejs.org/zh/
> 

# vue-cli

`vue-cli`是一个脚手架工具，用于搭建`vue`工程，本质是

**webpack**，并**预置了诸多插件（`plugin`）和加载器（`loader`）**，以达到开箱即用的效果

除了基本的插件和加载器外，`vue-cli`还预置了：

- babel
- webpack-dev-server
- eslint
- postcss
- less-loader

![image.png](工程师沉淀/Vue/Vue2/vue%20cli/image.png)

# SFC

单文件组件，Single File Component，即**一个文件就包含了一个组件所需的全部代码**

```html
<template>
	<!-- 组件模板代码 -->
</template>

<script>
export default {
  // 组件配置
}
</script>

<style>
	/* 组件样式 */
</style>

```

# 预编译

当`vue-cli`进行**打包**时，会通过 **template compiler 直接把组件中的模板转换为`render`函数**，这叫做模板预编译

这样做的好处在于：

1. 运行时就**不再需要编译模板**了，提高了运行效率
2. 打包结果中**不再需要vue的 template compiler ，减少了打包体积**

![image.png](工程师沉淀/Vue/Vue2/vue%20cli/image%201.png)

# 全局样式实现

创建 src/styles/global.less

然后在 main.js 导入

## 全局主题色

src/styles/var.less 存储颜色变量

# 补装less-loader

```jsx
cd /Users/a86198/Desktop/Lab/vue2/pager
```

```jsx
npm install less less-loader@7 --save-dev
```

# 手动模拟

![image.png](工程师沉淀/Vue/Vue2/vue%20cli/image%202.png)

![image.png](工程师沉淀/Vue/Vue2/vue%20cli/image%203.png)

![image.png](工程师沉淀/Vue/Vue2/vue%20cli/image%204.png)

![image.png](工程师沉淀/Vue/Vue2/vue%20cli/image%205.png)