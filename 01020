# net模块

传输层面

**进程间通信 IPC**

网络 TCP/IP

![回顾http请求.png](net%E6%A8%A1%E5%9D%97/%E5%9B%9E%E9%A1%BEhttp%E8%AF%B7%E6%B1%82.png)

![image.png](net%E6%A8%A1%E5%9D%97/image.png)

# 创建客户端

![创建客户端.png](net%E6%A8%A1%E5%9D%97/%E5%88%9B%E5%BB%BA%E5%AE%A2%E6%88%B7%E7%AB%AF.png)

**socket 是操作系统提供给应用程序操作网络通信的“接口对象”**

双工流

net.createConnection( ) 内部会自动建立TCP连接通道

https://github.com/ceilf6/Lab/commit/1ffeba2bc1b14c6b81a127c11ff8fd4659a27754

```jsx
const net = require("net")

// 网路接口对象（双工流：服务器 <=> 客户端，写入内容发送、监听内容接收
const socket = net.createConnection({
    host: "localhost", // 要连接到的主机
    port: 80
}, () => {
    // 连接的回调函数
    console.log("连接成功")
})

// socket.write(`GET /path HTTP/1.1
// 请求头
// Host: localhost
// Connection: keep-alive

// `)
socket.write(
    "GET /path HTTP/1.1\r\n" +
    "Host: localhost\r\n" +
    "Connection: close\r\n" +
    "\r\n"
)
// 必须要有两个换行，防止服务器认为你还没有传完
// GET 无请求体

function parseRes(res) {
    const idx = res.indexOf("\r\n\r\n")
    const head = res.slice(0, idx)
    const headArr = head.split('\r\n')
    const headers = headArr.map(str => str.split(":").map(it => it.trim()))
        .reduce((s, it) => {
            if (it.length === 2) // 排除请求行
                s[it[0]] = it[1]
            return s
        }, {})

    const body = res.slice(idx + 4,).trimStart()
    return { headers, body }
}

let maxSize
let curSize = 0
let headers = null
let body = ""
socket.on("data", chunk => {
    const res = chunk.toString("utf-8")
    if (!headers) {
        // 如果不是声明新变量，而是给外部变量赋值，必须加括号
        ({ headers, body } = parseRes(res))
        // todo: 不一定在一次传输中就传完响应头
        maxSize = +headers["Content-Length"]
        curSize += Buffer.from(body, "utf-8").byteLength
    } else
        curSize += Buffer.from(res, "utf-8").byteLength

    console.log("来自服务器的消息", res)
    if (curSize >= maxSize)
        socket.end() // 客户端主动挂断
})

socket.on("close", () => {
    console.log("连接结束")
})
```

# 创建服务器

https://github.com/ceilf6/Lab/commit/0282185b3a1d1923365daa6bb3f6147440c35f51

![创建服务器.png](net%E6%A8%A1%E5%9D%97/%E5%88%9B%E5%BB%BA%E6%9C%8D%E5%8A%A1%E5%99%A8.png)

```jsx
const net = require("net")
const path = require("path")
const fs = require("fs")

const server = net.createServer()

server.listen(80) // 监听端口

server.on("listening", () => {
    console.log("日志记录", Date.now())
})

// 每一个客户端连接 服务器都会产生一个socket
server.on("connection", socket => {
    console.log("有客户端连接到服务")

    socket.on("data", async chunk => {
        console.log("服务器接收到", chunk.toString("utf-8"))

        const testFilePath = path.resolve(__dirname, "../testFiles/copyPic.jpg")
        const testFileBuffer = await fs.promises.readFile(testFilePath)

        // 头 Content-type 会影响浏览器的解析
        const headBuffer = Buffer.from( // must be an instance of Buffer or Uint8Array
            `HTTP/1.1 200 OK
Content-Type: image/jpeg

`)

        const totalBuffer = Buffer.concat([headBuffer, testFileBuffer]);
        socket.write(totalBuffer);
        socket.end()
    })

    socket.on("end", () => console.log("连接关闭"))
})
```