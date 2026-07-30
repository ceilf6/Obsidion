# 3. childLanes 剪枝

FiberNode 有个字段 **childLanes** 表示 **子树是否有更新**

如果当前 fiberNode 没有 update, 而且 childLanes 也没有匹配当前 renderLanes

那么直接 return null 整颗子树跳过