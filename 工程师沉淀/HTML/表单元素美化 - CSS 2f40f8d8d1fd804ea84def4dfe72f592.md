# 表单元素美化 - CSS

# outline

在 **:focus 伪类**状态下默认有 outline 变蓝 *-webkit-focus-ring-color auto 1px*

进行覆盖 outline: <width> <style> <color>;

```css
input:focus {
    /* outline: <width> <style> <color>; */
    outline: #bf91f3 auto 2px;
    /* 默认样式还有 offset 偏移量 */
    outline-offset: 0;
}
```

还需要覆盖偏移量

# :checked

单选或多选框**被选中**的样式，配合 + 选中 label

# 常见用法

## 1. 重置和覆盖

```css
input,
textarea,
button,
select {
    border: none;
}

input:focus,
textarea:focus,
button:focus,
select:focus {
    border: none;
    outline-offset: 0;
}
```

```css
input[type="text"],
textarea {
    border: 1px solid #bf91f3;
}

input[type="text"]:focus,
textarea:focus {
    border: none;
    outline: 1px solid #70A5FE;
}
```

## 2. 设置 textarea 是否允许调整尺寸

resize 属性

- both：默认值，两个方向都可以调整尺寸
- none：不能调整尺寸
- horizontal: 水平方向可以调整尺寸
- vertical：垂直方向可以调整尺寸

## 内容到文本框边缘的距离

```css
input,
textarea {
    /* 1. padding */
    padding: 10px;

    /* 2. text-indent 首行缩进 */
    /* text-indent: 1em; */
}
```

## 控制单选和多选的样式

由于不能改变系统固定的input:radio的样式，所以就自己搓一个

```css
.radio {
    width: 12px;
    height: 12px;
    border: 1px solid #bf91f3;
    /* 圆形 */
    border-radius: 50%;

    cursor: pointer;
}

.radio.checked {
    border-color: #70A5FE;
    position: relative;
}

.radio.checked::after {
    content: "";
    position: absolute;
    width: 6px;
    height: 6px;
    background-color: #70A5FE;
    /* (12-6)/2 */
    left: 3px;
    top: 3px;
    border-radius: 50%;
}
```