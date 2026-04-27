# 事件对象

事件**对象**封装了事件的相关**信息**

## 获取事件对象

- 通过事件处理函数的参数获取
- 旧版本的IE浏览器通过window.event获取

## 事件对象的通用成员

### **target** 或 srcElement

事件目标（事件源）：目标阶段的元素

```jsx
const container = document.getElementsByClassName('container');
container[0].onclick = function (e) {
    e = e || window.event;
    const source = e.target || e.srcElement
    console.log('事件目标', source);
};
```

事件委托：通过**给祖先元素注册**事件，在程序处理程序中**判断事件源进行不同的处理**。

通常，事件委托用于**动态**生成元素的区域。

```jsx
container[0].onclick = function (e) {
    // 根据事件源进行分流处理
    **if (e.target.tagName === "BUTTON")** {
        // 元素名称
        e.target.parentElement.remove();
    }
};
```

如果结构复杂就不适合

### currentTarget

当前目标：获取**绑定事件的元素，等效于 this**

### type

字符串，得到事件的类型

### preventDefault & returnValue

preventDefault方法

**阻止浏览器默认行为**。

dom0的方式：在事件处理程序中返回false

针对a元素，可以设置为功能性链接解决跳转问题

### stopPropagation方法

**阻止**事件**冒泡**

### eventPhase

得到事件所处的阶段

1： 事件捕获
2： 事件目标
3： 事件冒泡