# 自定义指令

本质就是导出一个对象

# 定义指令

## 全局定义

```jsx
// 指令名称为：mydirec1
Vue.directive('mydirec1', {
  // 指令配置
})

// 指令名称为：mydirec2
Vue.directive('mydirec2', {
  // 指令配置
})
```

之后，所有的组件均可以使用`mydirec1`和`mydirec2`指令

```
<template>
  <!-- 某个组件代码 -->
  <div>
    <MyComp v-mydirec1="js表达式" />
    <div v-mydirec2="js表达式">
      ...
    </div>
    <img v-mydirec1="js表达式" />
  </div>
</template>

```

注意：注册全局指令，必须**在创建 Vue 实例之前**

```jsx
import vLoading from './directives/loading/index'
Vue.directive("loading", vLoading)

new Vue({
  router: router,
  render: h => h(App),
}).$mount('#app')
```

## 局部定义

局部定义是指在某个组件中定义指令，和局部注册组件类似。

定义的指令仅在该组件中有效。

```
<template>
  <!-- 某个组件代码 -->
  <div>
    <MyComp v-mydirec1="js表达式" />
    <div v-mydirec2="js表达式">
      ...
    </div>
    <img v-mydirec1="js表达式" />
  </div>
</template>

<script>
export default {
  // 定义指令
  directives: {
    // 指令名称：mydirec1
    mydirec1: {
      // 指令配置
    },
    // 指令名称：mydirec2
    mydirec2: {
      // 指令配置
    }
  }
}
</script>

```

和局部注册组件一样，为了让指令更加通用，通常我们会把指令的配置提取导入到其他模块。

```
<template>
  <!-- 某个组件代码 -->
  <div>
    <MyComp v-mydirec1="js表达式" />
    <div v-mydirec2="js表达式">
      ...
    </div>
    <img v-mydirec1="js表达式" />
  </div>
</template>

<script>
  // 导入当前组件需要用到的指令配置对象
  import mydirec1 from "@/directives/mydirec1";
  import mydirec2 from "@/directives/mydirec2";
	export default {
    // 定义指令
    directives: {
      mydirec1,
      mydirec2
    }
  }
</script>

```

# 指令配置对象

没有配置的指令，就像没有配置的组件一样，毫无意义

`vue`支持在指令中配置一些**钩子函数**，在适当的时机，`vue`会调用这些钩子函数并传入适当的参数，以便开发者完成自己想做的事情。

常用的钩子函数：

```jsx
// 指令配置对象
{
  bind(){
    // 只调用一次，指令第一次绑定到元素时调用。在这里可以进行一次性的初始化设置。
  },
  inserted(){
    // 被绑定元素插入父节点时调用。
  },
  update(){
    // 所在组件的 VNode 更新时调用
  }
}

```

> [查看更多的钩子函数](https://cn.vuejs.org/v2/guide/custom-directive.html#%E9%92%A9%E5%AD%90%E5%87%BD%E6%95%B0)
> 

每个钩子函数在调用时，`vue`都会向其传递一些参数，其中最重要的是前两个参数

```jsx
// 指令配置对象
{
  bind(el, binding){
    // el 是被绑定元素对应的真实DOM
    // binding 是一个对象，描述了指令中提供的信息
  }
}

```

## bingding 对象

![image.png](工程师沉淀/Vue/Vue2/自定义指令/image.png)

![image.png](工程师沉淀/Vue/Vue2/自定义指令/image%201.png)

> [查看更多bingding对象的属性](https://cn.vuejs.org/v2/guide/custom-directive.html#%E9%92%A9%E5%AD%90%E5%87%BD%E6%95%B0%E5%8F%82%E6%95%B0)
> 

# 配置简化

比较多的时候，在配置自定义指令时，我们都会配置两个钩子函数

```jsx
{
  bind(el, bingding){
		// 初始化
  },
  update(el, bingding){
		// 更新
  }
}

```

这样，在元素绑定和更新时，都能运行到钩子函数

如果这两个钩子函数实现的功能相同，可以直接把指令配置简化为一个单独的函数：

```jsx
function(el, bingding){
  // 该函数会被同时设置到bind和update中
}
```

> 利用上述知识，可满足大部分自定义指令的需求
> 
> 
> 更多的自定义指令用法见[官网](https://cn.vuejs.org/v2/guide/custom-directive.html)
> 

# 实践

## v-loading

添加 loading 图片

```jsx
import loadingUrl from '@/assets/loading.svg'
import styles from "./loading.module.less";

// 导出指令的配置对象

export default function (el, binding) {
    // 根据 binding.value 值决定 Loading 元素的创建和删除
    const curImg = getLoadingImg(el);
    if (binding.value) {
        if (!curImg) {
            const img = createLoadingImg()
            el.appendChild(img)
        }
    } else {
        if (curImg) {  // 添加空值检查
            curImg.remove();
        }
    }
}

function getLoadingImg(el) {
    return el.querySelector("img[data-role=loading]")
}

function createLoadingImg() {
    const img = document.createElement("img")
    img.dataset.role = "loading"
    img.src = loadingUrl
    img.className = styles.loading;
    return img;
}
```

## v-lazy

懒加载图片

```jsx
import eventBus from "@/eventBus";
import debounce from "../../utils/debounce";
import defaultImg from '@/assets/defaultImg.gif'

let imgs = [];

function setImage(img) {
    img.dom.src = defaultImg // 设置默认图片（浏览器会缓存，能极大提高性能）

    // 懒加载图片处理
    // 判断图片是否在视口范围内
    const rect = img.dom.getBoundingClientRect();
    const height = rect.height || 150; // 当图片没有加载时高度是 0 
    const clientHeight = document.documentElement.clientHeight
    if (rect.top >= -height && rect.top <= clientHeight) {
        // 在视口范围内
        const newImg = new Image()
        // 等图片加载完之后再进行替换掉默认图片
        newImg.onload = () => img.dom.src = img.src
        newImg.src = img.src // 开始加载

        // img.flag = true // 移除图片
        imgs = imgs.filter(i => i !== img)
    }
}
// 随着滚动条滚动，显示视口中的、需要显示的图片
function handleScroll() {
    for (const img of imgs) {
        setImage(img)
    }
}

// 作为滚动事件的监听者加入到事件总线中（因为只有滚轮才会移动视图）
// 注意 mixins/mainScroll 上抛的事件名称是 mainScroll
eventBus.$on("mainScroll", debounce(handleScroll, 30))

export default {
    // 得是 inserted 加到父元素中去之后，否则像 bind 绑定时候就调用的话，无法拿到视口信息
    inserted(el, bindings) {
        const nowImg = ({
            src: bindings.value,
            dom: el,
            // flag: false, // 标记是否已经处理过 // 当前最新方案直接移除
        })
        imgs.push(nowImg) // 在使用指令的时候，说明该图片需要纳入懒加载图片范围
        setImage(nowImg) // 当绑定指令时需要立即处理
    },
    unbind(el) {
        imgs = imgs.filter(img => img.dom != el) // 当 el 卸载时需要析构对应资源
    }
}
```

[mixins/mainScroll 滚动事件](%E4%BA%8B%E4%BB%B6%E6%80%BB%E7%BA%BF%20%E5%8F%91%E5%B8%83%E8%AE%A2%E9%98%85%E6%A8%A1%E5%BC%8F%203020f8d8d1fd80d2909ffe2d4c0abb0c.md)