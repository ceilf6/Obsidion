# 优先任务队列 lazyman

实现

```jsx
Hardman ("jack"). rest (10).learn ("computer")
/*打印：
I am jack
/等十秒
Learning computer */
Hardman ("jack"). Firstrest (10).learn("computer")
/* 打印：
/等十秒
I am jack
Learning computer */
```

注意

1. 为实现链式调用、装饰器模式，中间过程函数需要 return this
2. 因为有 First **优先级**存在，所以需**要延迟启动**：将第一个任务（打印名字）包在一个 setTimeout( ,0 ) 中，确保链式调用全部完成后，再开始执行任务

1. 维护任务队列 task, next()

```jsx
// 通过 任务队列task,next() 进行管理
function LazyMan(name) {
    this.name = name
    this.task = [() => {
        console.log(`I am ${this.name}`)
        this.next() // 执行完后继续下一个任务
    }]

    // 延迟启动，确保链式调用形成后再执行
    setTimeout(() => {
        this.next()
    }, 0)
}

// 执行下一个任务
LazyMan.prototype.next = function () {
    const task = this.task.shift()
    task && task.call(this) // 使用 call 绑定 this
}

LazyMan.prototype.rest = function (time) {
    this.task.push(() => {
        setTimeout(() => {
            console.log(`Wake up after ${time}s`)
            this.next() // 休息结束后继续执行
        }, time * 1000)
    })
    return this // 返回this进而支持装饰器模式链式调用，例如 .rest(time).rest()/.learn
}

LazyMan.prototype.firstRest = function (time) {
    this.task.unshift(() => {
        setTimeout(() => {
            console.log(`Wake up after ${time}s`)
            this.next()
        }, time * 1000)
    })
    return this
}

LazyMan.prototype.learn = function (what) {
    this.task.push(() => {
        console.log(`Learning ${what}`)
        this.next() // 执行完后继续
    })
    return this
}

// 工厂函数
function Hardman(name) {
    return new LazyMan(name)
}
```

1. 维护Promise

```jsx
// Promise 链实现：通过维护一个 promise 链，每次调用方法追加 .then()

function LazyManPromise(name) {
    this.name = name
    // 延迟启动的 Promise 作为链的起点
    this.promise = new Promise(resolve => {
        setTimeout(() => {
            console.log(`I am ${this.name}`)
            resolve()
        }, 0)
    })
}

LazyManPromise.prototype.rest = function (time) {
    // 在现有 Promise 链后追加新的异步操作
    this.promise = this.promise.then(() => {
        return new Promise(resolve => {
            setTimeout(() => {
                console.log(`Wake up after ${time}s`)
                resolve()
            }, time * 1000)
        })
    })
    return this
}

LazyManPromise.prototype.firstRest = function (time) {
    // 创建新的 Promise 链，将原链追加到后面
    const oldPromise = this.promise
    this.promise = new Promise(resolve => {
        setTimeout(() => {
            console.log(`Wake up after ${time}s`)
            resolve()
        }, time * 1000)
    }).then(() => oldPromise)
    return this
}

LazyManPromise.prototype.learn = function (what) {
    this.promise = this.promise.then(() => {
        console.log(`Learning ${what}`)
    })
    return this
}

function HardmanPromise(name) {
    return new LazyManPromise(name)
}

console.log('=== Promise 链实现 ===')
HardmanPromise("Tom").rest(1).learn("Math")

setTimeout(() => {
    console.log('\n=== Promise firstRest 测试 ===')
    HardmanPromise("Jack").firstRest(1).learn("English")
}, 3000)
```