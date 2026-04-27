# Trunk

## 所有开发都从 trunk

开发分支都是短期从 trunk 主分支牵出去的

## 开发分支变更提交都很小

## 频繁合并

## Feature Flag 控制

```
if (featureFlag.newLogin) {
   newLogin()
} else {
   oldLogin()
}
```

代码 merge 到 trunk 但是功能默认关闭，等到上线时再打开

## 需要 CI 强悍

例如通过 GitHub Actions

```
push -> CI -> test -> build -> deploy
```

# 工作流程

1. 创建 feature 短分支
2. 开发
3. 合并 trunk
4. 提 PR
5. CI 通过
6. CR
7. merge