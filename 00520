# 13 TD5 tr useradd

# tr

tr 命令用于字符处理

```bash
tr from to
```

按照 from 到 to 的规则，逐个字符处理

例如

```bash
tr ':' '|'
```

大小写转换

```bash
tr 'A-Z' 'a-z'
```

# useradd

```bash
useradd -u UID \
        -g GID \
        -d dir-home目录 \
        -c comment注释评论 \
        -s shell \
        -p passwd \
        用户名
```

可以先

```bash
useradd -m login
```

创建名为 login 的用户

然后通过

```bash
usermod -.. ... login
```

user modify: 修改 login 用户的对应字段

```bash
userdel
```

删除用户

```bash
chage
```

change age 设置用户的有效期限

> 最好这些权限都在 sudo 后运行，防止当前用户没有权限
>