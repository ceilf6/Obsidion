# weaviate实践

https://github.com/ceilf6/FrontAgent/commit/8dce4138c3c3ec8d1c6e6d6944583b4af07c0af5

1. 通过 brew install weaviate 进行本地启动

但是我发现磁盘空间不足导致只跑了 96 就中断了

1. 通过 docker 直接在本地启动weaviate的官方镜像

```tsx
docker run -d \
  --name weaviate \
  -p 8080:8080 \
  -p 50051:50051 \
  cr.weaviate.io/semitechnologies/weaviate:1.36.2
```

然后服务启动在本地端口上，第一次的时候可能会比较慢因为需要将嵌入模型生成的向量录入数据库，后面就会快了因为是**增量更新**的

**向量检索算法解决“怎么找得快”，向量数据库解决“怎么把这件事变成可运营、可扩展、可维护的系统”**