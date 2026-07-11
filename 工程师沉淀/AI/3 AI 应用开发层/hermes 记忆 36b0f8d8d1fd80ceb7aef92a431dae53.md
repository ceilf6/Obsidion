# hermes 记忆

上下文

```jsx
默认：头尾保留 + 中间结构化摘要 + 清理旧工具输出 + 递归更新 summary
兜底：gateway 85% 自动 hygiene
优化：Anthropic prompt caching 降低重复上下文成本
扩展：ContextEngine 插件机制，可替换成 LCM 等更“无损”的方案
```