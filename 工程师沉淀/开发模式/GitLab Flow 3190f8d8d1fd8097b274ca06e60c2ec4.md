# GitLab Flow

Git Flow 太复杂

GitLab Flow 不支持多环境 / 版本发布

GitLab Flow 本质就是 GitHub Flow + 环境分支/发布分支

```tsx
main = 开发主干
feature branch = 功能开发
environment branch = 部署环境
```

```tsx
feature branch
      ↓
Merge Request
      ↓
main
      ↓
staging
      ↓
production
```

**代码合并到 main 后，再逐步推进到不同环境**

## GitLab Flow with Environment Branches

```
feature/* 开发功能
   │
   ▼
main 集成代码
   │
   ▼
staging 测试环境
   │
   ▼
production 生产环境
```

1. 开发新功能时创建 feature 分支

```
git checkout main
git checkout -b feature/login
```

1. 创建 Merge Request

向 main 提交 MR

```
feature/login
      ↓
Merge Request
      ↓
main
```

在 MR 中进行

- CR
- CI pipeline
- 自动测试

1. 部署到 staging 测试环境

在 main 稳定后

```
git checkout staging
git merge main
```

CI会自动部署

```
staging server
```

进行 QA测试、集成测试、UAT

1. 发布到 production

```
git checkout production
git merge staging
```

CI 自动部署

```
production server
```

## Hotfix

如果线上出现 bug

那么从 production 中牵出 hotfix branch

```
git checkout production
git checkout -b hotfix/payment-bug
```

修复后再合过去

```
hotfix
   ↓
production
   ↓
main
```

## 版本发布 release

```
feature → main → release → production
```

## 通过 feature flag 控制

```
if (featureFlag('new-ui')) {
  renderNewUI()
}
```