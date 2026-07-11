# Playwright

Source: [KM 2765360999](https://km.sankuai.com/collabpage/2765360999)

> 一个能真实打开浏览器、模拟用户操作、并验证页面结果的自动化测试工具。
> 
- 普通单元测试 Vitest / Jest 是在 Node.js 中跑
- Playwright 直接真的启动浏览器 -> 打开网页，进行 e2e 测试

[https://github.com/microsoft/playwright](https://github.com/microsoft/playwright)

### 常用对象

### page

自动化控制的浏览器标签页

### Locator

Playwright 不推荐你大量使用脆弱的 CSS 选择器

更推荐使用贴近用户视角的 locator：

`page.getByRole('button', { name: '登录' })page.getByLabel('用户名')page.getByText('欢迎回来')page.getByPlaceholder('请输入手机号')`

```
// 代码块
测试文件 login.spec.ts
  ↓
@playwright/test 测试运行器
  ↓
启动浏览器 Chromium / Firefox / WebKit
  ↓
创建 browser context 隔离环境
  ↓
打开 page
  ↓
执行 goto / click / fill 等操作
  ↓
执行 expect 断言
  ↓
生成报告 / trace / screenshot / video
```

```
// 代码块
browser：浏览器实例
context：隔离的浏览器环境，类似独立用户会话
page：一个标签页
locator：页面元素定位方式
expect：断言结果
```