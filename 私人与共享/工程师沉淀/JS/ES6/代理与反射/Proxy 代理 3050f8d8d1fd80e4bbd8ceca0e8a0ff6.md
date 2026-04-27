# Proxy 代理

https://github.com/ceilf6/Lab/commit/030ed37fc99142ab4e611f3ad3523df2daa3514a

外界 <=> 代理对象 <= **Reflect & …** => 目标对象

代理：提供了 在**底层能力基础上做额外事情** 的方式

```jsx
//代理一个目标对象
//target：目标对象
//handler：是一个普通对象，其中可以重写底层实现
//返回一个代理对象
const proxyObj = new Proxy(target, handler)
```

外界的操作必须经过代理，那么代理就可以先做一些事情，然后再调用 Reflect. 去影响委托人

```jsx
const targetObj = {
    name: 'ceilf6',
    age: 20
}

const proxyObj = new Proxy(targetObj, {
    **set**(target, propertyKey, value, receiver) {
        console.log(target, propertyKey, value)
        // { name: 'ceilf6', age: 20 } name ceilf7

        // 代理做的事情

				// 在代理内部通过 Reflect 和委托人沟通
        // target[propertyKey] = value
        Reflect.set(target, propertyKey, value)

        return true // set 不返回 true 会报错
    },
    **get**(target, propertyKey) {
        if (Reflect.has(target, propertyKey)) {
            return Reflect.get(target, propertyKey);
        } else {
            return -1;
        }
    },
    apply() {

    },
})

console.log(proxyObj)

// targetObj.name = 'ceilf7'
proxyObj.name = 'ceilf7' // 注意外界只应该和代理打交道

// console.log(targetObj.name)
```