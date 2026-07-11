# Node.js 与 React 服务端渲染入门

你将从「完全不了解」到「能独立搭建一个最小可运行的 React SSR 示例」。用直白的方式讲清楚：什么是 Node.js、什么是 SSR（Server Side Rendering, SSR）、与 CSR（Client Side Rendering, CSR）、SSG（Static Site Generation, SSG） 的差异；再一步步实现一个「可复制即可跑」的最小项目，并理解何时与为何使用 SSR。

从第一性原理理解 Node.js

Node.js 是什么

Node.js：JavaScript 运行时。JavaScript（简称 JS）原本只能在浏览器里跑；Node.js 把 JS 带到服务器上，让你用 JS 写后端代码。它的底层依赖 V8 引擎（Chrome 同款）、用 事件循环（event loop）来处理大量并发请求。

可以把 Node.js 想象成一个乐团指挥：它并不自己演奏每件乐器（不是每个请求都开一条重乐器的线程），而是通过事件通知把任务交给合适的「乐手」（系统调用、线程池、I/O），自己快速调度与响应，这让它特别适合网络 I/O 密集的任务（比如处理网页请求）。

对比与选型：Node.js 与其他后端语言

下面用简明视角对比常见后端技术的并发模型、生态、学习门槛与性能特点，帮助你建立选型直觉。

Node.js

- 

并发模型：事件循环 + 非阻塞 I/O (Non-blocking I/O)，适合 I/O 密集任务。

- 

生态：与前端共享 JavaScript，npm 包生态极其丰富。

- 

学习门槛：前端同学上手快，统一语言栈降低沟通成本。

34%

Java / Python

- 

Java：多线程 + JVM，性能稳健，生态成熟（Spring）。

- 

Python：单线程为主（有 GIL），擅长业务脚本与数据处理（Django/Flask 生态良好）。

- 

学习门槛：Java 体系完整但起步较重；Python 语法简洁友好。

33%

Go / PHP

- 

Go：goroutine 并发，内置并发原语，编译后性能好，部署简单。

- 

PHP：以同步请求/响应为主，常用于模板渲染与传统 Web。

- 

学习门槛：Go 简洁；PHP 入门快，托管环境普及。

33%

CSR

客户端渲染（Client Side Rendering, CSR）：服务器主要返回一个“空壳” HTML + 大量 JS，首屏需等待 JS 下载与执行，页面才真正渲染出来。

- 

首屏：较慢，依赖 JS；

- 

SEO（Search Engine Optimization, SEO）：搜索引擎抓取不稳定；

- 

复杂度：实现简单，前端为主；

- 

适用：重交互、内网系统，SEO 不敏感。

33%

SSR

服务端渲染（Server Side Rendering, SSR）：服务器返回已经渲染好的 HTML，首屏更快；随后在浏览器进行 hydration（水合），让页面恢复/获得交互。

- 

首屏：更快、可渐进；

- 

SEO：更友好；

- 

复杂度：需要“服务端 + 客户端”协作；

- 

适用：内容型页面、需要首屏与 SEO 的业务。

34%

SSG

静态站点生成（Static Site Generation, SSG）：构建时就把页面生成好，部署为静态文件，访问时读取现成 HTML。

- 

首屏：最快（纯静态）；

- 

SEO：最佳（直出 HTML）；

- 

复杂度：依赖构建流程与预生成；

- 

适用：文档、博客、很少变化的内容。

33%