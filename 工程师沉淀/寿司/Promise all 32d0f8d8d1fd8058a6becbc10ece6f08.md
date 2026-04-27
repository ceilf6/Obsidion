# Promise.all

Promise.all 返回的是一个 Promise

和任务队列一样需要维护一个 todos 判断是否都完成

逐个 await 会导致串行阻塞，得 Promise.resolve(todo).then()

```jsx
function myPromiseAll(promises) {
    // Promise.all 返回的是一个 Promise
    return new Promise((resolve, reject) => {
        const LP = promises.length
        if (LP === 0) {
            // 注意特殊情况 Promise.all([]) => []
            resolve([])
            return
        }

        const res = new Array(LP).fill(null)
        let todos = LP
        for (let i = 0; i < LP; i++) {
            // try {
            // 逐个 await 会导致串行阻塞
            // const curRes = await promises[i]
            // res[i] = curRes
            Promise.resolve(promises[i])
                .then(value => {
                    res[i] = value
                    todos--

                    if (todos === 0) {
                        resolve(res)
                    }
                })
                .catch(reject)
            // await 如果报错的话会自动抛出，无需 catch
            // } catch (e) {
            //     throw e
            // }
        }
        return res
    })
}
```