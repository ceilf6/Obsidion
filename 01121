# index

**PWA（Progressive Web App）架构**是一种把 **Web 应用做得像原生 App 一样** 的技术体系。

核心目标是：

```
让网页拥有类似原生 App 的能力
```

例如：

- 可安装到桌面 / 手机
- 离线可用
- 后台同步
- 推送通知
- 独立窗口运行

---

# **一、PWA 的整体架构**

PWA 一般由 **三大核心技术组成**：

```
PWA Architecture

        Web App
           │
           │
    ┌──────┴──────┐
    │             │
Service Worker   Web App Manifest
    │
    │
 Cache API / Push API / Sync API
```

核心三部分：

1️⃣ **Service Worker**

2️⃣ **Web App Manifest**

3️⃣ **HTTPS**

---

# **二、Service Worker（核心）**

Service Worker 是 PWA 的 **核心组件**。

可以理解为：

```
浏览器里的代理服务器
```

它运行在 **浏览器后台线程**，可以拦截网络请求。

结构：

```
Page
  │
  │ fetch
  ↓
Service Worker
  │
  ├── Cache
  └── Network
```

### **功能**

- 离线缓存
- 请求拦截
- 推送通知
- 后台同步

---

### **示例**

注册 Service Worker：

```
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('/sw.js')
}
```

---

### **拦截请求**

```
self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request)
  )
})
```

这意味着：

```
请求 → SW → Cache → 返回
```

即使离线也能打开页面。

---

# **三、Web App Manifest**

Manifest 是一个 **配置文件**，告诉浏览器：

```
这个网站可以像 App 一样安装
```

例如：

```
{
  "name": "My App",
  "short_name": "App",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#ffffff",
  "icons": [
    {
      "src": "/icon.png",
      "sizes": "192x192"
    }
  ]
}
```

作用：

- App 图标
- 启动页面
- 启动方式
- 主题颜色

---

### **安装后的效果**

用户可以：

```
Add to Home Screen
```

然后：

```
桌面图标
   ↓
独立窗口
```

没有浏览器地址栏。

---

# **四、HTTPS**

PWA 必须运行在：

```
HTTPS
```

原因：

Service Worker 能：

- 拦截请求
- 修改响应

这是高权限能力，所以必须 HTTPS。

---

# **五、PWA 架构能力**

PWA 可以使用很多浏览器 API：

| **能力** | **API** |
| --- | --- |
| 离线缓存 | Cache API |
| 推送通知 | Push API |
| 后台同步 | Background Sync |
| 安装应用 | Manifest |
| 请求拦截 | Service Worker |

---

# **六、PWA 请求流程**

PWA 的请求流程和普通网页不同。

普通网页：

```
Page → Network → Server
```

PWA：

```
Page
  │
  ↓
Service Worker
  │
  ├── Cache
  └── Network
```

也就是：

```
Cache-first
Network-first
Stale-while-revalidate
```

这些缓存策略。

---

# **七、常见缓存策略**

### **1️⃣ Cache First**

```
Cache → Network
```

适合：

```
静态资源
```

---

### **2️⃣ Network First**

```
Network → Cache
```

适合：

```
API数据
```

---

### **3️⃣ Stale While Revalidate**

```
Cache → 返回
   │
   └→ Network 更新缓存
```

兼顾：

```
速度 + 新数据
```

---

# **八、PWA 的能力**

PWA 可以实现：

```
离线访问
安装到桌面
推送通知
后台同步
独立窗口运行
```

效果接近：

```
Native App
```

例如：

- Twitter Lite
- Starbucks PWA
- Pinterest PWA

---

# **九、PWA 架构图**

完整结构：

```
                Server
                   │
                   │
                Network
                   │
                   ▼
            Service Worker
            /            \
        Cache            API
          │                │
          ▼                ▼
      Static Files      Dynamic Data
              │
              ▼
           Web App
              │
        Manifest.json
              │
         Install App
```

---

# **十、为什么 PWA 在架构上重要**

PWA 引入了一层：

```
Service Worker
```

这其实是：

```
Client-side Proxy
```

它让 Web 有了：

```
缓存层
网络控制层
推送层
```

这就是 **PWA 架构的本质**。

---

# **十一、总结**

PWA 架构的核心：

```
Service Worker + Manifest + HTTPS
```

架构：

```
Web App
   │
Service Worker
   │
Cache + Network
```

目标：

```
让 Web 应用具备 App 能力
```

---

如果你感兴趣，我可以再给你讲一个 **非常关键的 PWA 架构细节**：

> 为什么
> 
> 
> **Service Worker 可以拦截 fetch 请求，但不能访问 DOM？**
> 

这个涉及 **浏览器进程模型 + 安全设计**，其实非常有意思。