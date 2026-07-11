# DOM事件基本概念

## 术语

- 事件：发生一件事
- 事件类型：发生什么事情；点击、鼠标按下、鼠标抬起、鼠标移入、鼠标移出、键盘按下、键盘抬起...
- 事件处理程序：一个函数，当某件事情**发生时运行**。
- 事件注册：将一个**事件处理程序，挂载到某个事件上**。

## 事件流

事件流：当某个事件发生的时候，**哪些元素会监听到该事件发生**，这些元素发生该事件的顺序。

**当一个元素发生了某个事件时，那该元素的所有祖先元素都发生了该事件**

1. 事件捕获：先触发**外层**的元素，然后再依次触发里面元素
2. 事件目标处理阶段
3. 事件冒泡：先触发**最里层**的元素，然后再依次触发外层元素

![image.png](DOM%E4%BA%8B%E4%BB%B6%E5%9F%BA%E6%9C%AC%E6%A6%82%E5%BF%B5/image.png)

![image.png](DOM%E4%BA%8B%E4%BB%B6%E5%9F%BA%E6%9C%AC%E6%A6%82%E5%BF%B5/image%201.png)

目前，标准规定，**默认**情况下，事件是**冒泡**的方式触发（监听）

可以通过设置 **capture** 为 true 声明用捕获的方式

```jsx
element.addEventListener('click', handler, {
  capture: true
});
```

事件源、事件目标：事件目标阶段的元素

同时不同层级事件通过原型链串通，实现方法复用

```jsx
document.addEventListener('click', function (e) {
    let cur = e
    while (cur) {
        console.log(cur)
        cur = Object.getPrototypeOf(cur)
    }
})

PointerEvent
→ MouseEvent
→ UIEvent
→ Event
→ Object
→ null
```