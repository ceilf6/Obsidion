# Promise链式处理

![image-20210618161125894](http://mdrs.yuanjin.tech/img/20210618161125.png)

# catch方法

语法糖

`.catch(onRejected)` = `.then(null, onRejected)`

# 链式调用

![image-20210621103501094](http://mdrs.yuanjin.tech/img/20210621103501.png)

**then**方法必定会**返回一个新的Promise**

可理解为**`后续处理也是一个任务`**

后续处理：传给 .then, .catch, .finally 的函数

**新任务的状态取决于后续处理函数**：（then中的函数）

1. 没有任务：若**没有相关的后续处理，新任务的状态和前任务一致**，数据为前任务的数据
    
    例如 **pro1 是 rejected 但是 pro2 是 pro1的onFulfilled 那么就是没有后续处理**，那么 pro2 的状态和 pro1 完全一致；同理 成功后面的.catch 也是一样的
    
    还有像 .then() 没有传入后续任务
    
    但是像 .then(()⇒{}) 就不是空的
    
2. 有任务但是还没有执行：若**有后续处理但还未执行**，新任务**挂起**pending。
3. 有任务且执行：若后续处理执行了，则**根据后续处理的情况确定新任务的状态**
    
    Promise 传入函数的参数为状态改变函数resolve 和reject
    在链中没有状态改变函数，得通过
    
    **return** => fulfilled
    
    **throw** => rejected
    
    ```css
    const pro1 = new Promise((resolve, reject) => {
        resolve(1);
        reject(1);
    })
    const pro2 = pro1.then(res => {
        throw res + 1;
    })
    const pro3 = pro2.catch(e => {
        return e + 1;
    })
    // Promise { 1 } 
    // Promise { <rejected> 2 } 
    // Promise { 3 }
    ```
    
    **若 return new Promise**
    
    那么就会**完全跟随新任务的状态和数据**
    
    ```css
    const pro1 = new Promise((resolve, reject) => {
        resolve();
    });
    
    let pro3;
    
    const pro2 = pro1.then(() => {
        pro3 = new Promise((resolve, reject) => { });
        return pro3;
    });
    
    setTimeout(() => {
        console.log(pro2);
        /*
        由于 pro2 返回的新任务 pro3没有结束
        那么 pro2 跟随 pro3 状态都是
        Promise { <pending> }
        */
        console.log(pro3);
    }, 1000);
    ```
    

像 A.b().c().d() 看的是 d 的结果，所以如果给一个Promise链赋值，看的是链尾的结果

平时的链式使用

```jsx
// 常见任务处理代码

/*
 * 任务成功后，执行处理1，失败则执行处理2
 */
pro.then(处理1).catch(处理2)

/*
 * 任务成功后，依次执行处理1、处理2
 */
pro.then(处理1).then(处理2)

/*
 * 前面有很多处理，最后统一用一个**catch兜底**
 */
pro.then(处理1).then(处理2).catch(处理3)

```

# 邓哥的解决方案

```jsx
// 向某位女生发送一则表白短信
// name: 女神的姓名
// onFulffiled: 成功后的回调
// onRejected: 失败后的回调
function sendMessage(name) {
  return new Promise((resolve, reject) => {
    // 模拟 发送表白短信
    console.log(
      `邓哥 -> ${name}：最近有谣言说我喜欢你，我要澄清一下，那不是谣言😘`
    );
    console.log(`等待${name}回复......`);
    // 模拟 女神回复需要一段时间
    setTimeout(() => {
      // 模拟 有10%的几率成功
      if (Math.random() <= 0.1) {
        // 成功，调用 onFuffiled，并传递女神的回复
        resolve(`${name} -> 邓哥：我是九，你是三，除了你还是你😘`);
      } else {
        // 失败，调用 onRejected，并传递女神的回复
        reject(`${name} -> 邓哥：你是个好人😜`);
      }
    }, 1000);
  });
}

sendMessage('李建国')
  .catch((reply) => {
    // 失败，继续
    console.log(reply);
    return sendMessage('王富贵'); // 返回新的Promise，那么就跟随
  })
  .catch((reply) => {
    // 失败，继续
    console.log(reply);
    return sendMessage('周聚财');
  })
  .catch((reply) => {
    // 失败，继续
    console.log(reply);
    return sendMessage('刘人勇');
  })
  .then(
    (reply) => {
      // 成功，结束
      console.log(reply);
      console.log('邓哥终于找到了自己的伴侣');
    },
    (reply) => {
      // 最后一个也失败了
      console.log(reply);
      console.log('邓哥命犯天煞孤星，无伴终老，孤独一生');
    }
  );

```