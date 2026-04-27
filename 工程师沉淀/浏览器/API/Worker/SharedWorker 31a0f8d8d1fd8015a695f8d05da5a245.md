# SharedWorker

一般 Worker 是一个页面一个 worker

```jsx
const worker = new Worker("worker.js")
```

而 SharedWorker 可以被多个页面共享

```jsx
const worker = new SharedWorker("shared-worker.js")
```

使用 MessagePort 进行通信

```jsx
const worker = new SharedWorker("shared-worker.js")

worker.port.start()

worker.port.postMessage("hello")

worker.port.onmessage = (e) => {
  console.log(e.data)
}
```

```jsx
const ports = []

onconnect = function (e) {
  const port = e.ports[0]

  ports.push(port)

  port.onmessage = function (event) {
    const msg = event.data

    // 广播给所有页面
    ports.forEach(p => p.postMessage(msg))
  }
}
```

SharedWorker 类似于 BroadcastChannel 的拓展版，不仅支持跨tab页广播，还能共享计算、共享缓存

像 多tab页的WebSocket ，如果每个页面都开 WebSocket 服务器压力会很大，于是可以通过

SharedWorker 实现 多tab页共享WebSocket