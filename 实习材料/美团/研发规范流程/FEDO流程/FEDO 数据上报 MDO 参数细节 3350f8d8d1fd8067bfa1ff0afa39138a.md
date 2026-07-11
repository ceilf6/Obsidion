# FEDO 数据上报 MDO 参数细节

C-3创建:李增辉(Claude Lee)最后修改:李增辉(Claude Lee)2023-05-26 11:45

### **FEDO 提供指标**

### **开发阶段阶段**

### **开始开发时间**

- 指标口径：用户在开发分支相对于主分支的首次提交 commit 时间
- 上报时机：FEDO 分支关联 Ones 需求后
- 对应阶段：PUST_TEST

### **集成阶段**

### **PR 创建时间**

- 指标口径：用户在 FEDO 创建 Feature-> Release PR 的时间点
- 上报时机：FEDO PR 创建节点运行成功后
- 对应阶段：PR_TEST

### **PR 合并时间**

- 指标口径：用户在 FEDO 操作 Feature -> Release 合并的时间点
- 上报时机：FEDO PR 合并节点运行成功后
- 对应阶段：PR_MERGE

### **发布阶段**

### **开始发布&发布完成**

- 指标口径：用户在 FEDO 完成全量发布的时间的时间点
- 上报时机：全量节点发布后
- 对应阶段：RELEASE、GRAY_RELEASE、DEPLOY_ROOLBACK

### **上报数据**

数据上报接口参考：[Matrix接入接口文档](https://km.sankuai.com/page/591095260)

各阶段上报信息如下：

**Push**

Typescript

`{`

    `"branch": "feature/SVLTC-2019-8296253/spec",  // 开发分支`

    `"endTime": 1610332467450,  // 首次commit的时间戳`  

    `"startTime": 1610332446376,// 本次commit的时间戳`

    `"firstCommitTime":1610331953000, // pr上第一个commit时间戳`

    `"user":"xx", // commit用户信息`

    `"mainBranch": "master",  // 业务仓库的主分支`

    `"repo": "ssh://git@git.dianpingoa.com/tuangou/price-display.git", // 仓库地址`

    `"commit": "xxx" ,// push时的最新commit`

    `"step": "PUSH_TEST"  //  PUSH_TEST`

    `"trigger":"" //`

    `"from": "FEDO" // 上报数据的来源： MCD、TALOS、NEST、FEDO 等`

`}`

**PR 创建**

Typescript

`{`

    `"startTime": 1610331775000, // pr创建时间`

    `"endTime": 1610331953000, // 当前时间`

    `"sourceBranch": "feature/xxx", // pr源分支`

    `"targetBranch": "master", // pr目标分支`

    `"commit": "dfaaf7ea3ed39159305eb279caba1ea47b1ba35b", // commitId`

    `"repo": "ssh://git@git.dianpingoa.com/home/chimera-server.git", // 仓库地址`

    `"step": "PR_TEST", // 上报数据的阶段`

    `"from": "FEDO" // 上报数据的来源`

    `"id": "123",  // 例如: talosId和ones创建应用页的发布项字段进行对应`

    `"commitId": "dfaaf7ea3ed39159305eb279caba1ea47b1ba35b",  // commitId`

    `"user": "dinghao09", // 操作人`

    `"prId":100 // pull request id`

    `"firstCommitTime":1610331953000 // pr上第一个commit时间戳`

    `"url":"xx" // 业务系统的url，例如talos的应用url`

    `"trigger":"" //`

`}`

**PR 合并**

Typescript

`{`

    `"startTime": 1610331775000,  // pr创建时间`

    `"endTime": 1610331953000,  // PR合并的时间`

    `"branch": "feature/xx", // pr源分支`

    `"targetBranch": "master", // pr目标分支`

    `"mainBranch":"master" // 仓库主分支`

    `"commit": "dfaaf7ea3ed39159305eb279caba1ea47b1ba35b",` 

    `"repo": "ssh://git@git.dianpingoa.com/home/chimera-server.git",`

    `"step": "PR_MERGE", // 上报数据的阶段`

    `"from": "FEDO" // 上报数据的来源`

    `"id": "123",  // 例如: talosId和ones创建应用页的发布项字段进行对应`

    `"user": "dinghao09", // 操作人`

    `"prId":100 // pull request id`

    `"firstCommitTime":1610331953000 // pr上第一个commit时间戳`

    `"url":"xx" // 业务系统的url，例如talos的应用url`

    `"trigger":""`

`}`

**发布**

Typescript

`{`

    `"startTime": 1610331775000, // 发布开始时间`

    `"endTime": 1610331953000, // 发布结束时间`

    `"branch": "master", // 发布分支或tag`

    `"commit": "dfaaf7ea3ed39159305eb279caba1ea47b1ba35b", // 发布的commit`

    `"repo": "ssh://git@git.dianpingoa.com/home/chimera-server.git", // 仓库地址`

    `"step": "RELEASE", // 数据类型 RELEASE、GRAY_RELEASE、DEPLOY_ROOLBACK`

    `"from": "TALOS" , // 数据上报系统`

    `"env": "prod", // 发布环节`

    `"id": "123", // FEDO  任务 ID`

    `"deployPercent": 33, // 中心发布占比 ? 对前端可能无用，直接传 100`

    `"commitId": "dfaaf7ea3ed39159305eb279caba1ea47b1ba35b", // 发布的commitId`

    `"user": "dinghao09", // 发布人员`

    `"deployUrl": "xx", // 发布链接`

    `"name": "com.sankuai.chimera.core", // 平台名称，appkey/gitRepo`

    `"url":"xx" // 业务系统的url，例如talos的应用url`

    `"trigger":"" //`

    `"deployType": "deploy" // Ï发布类型， 正常发布是deploy，回滚是rollback`

`}`

针对以上各阶段，明确各项上报指标口径及获取来源如下（标红为该上报节点重点关注字段）：

***评估添加技术栈信息***

Push

| 字段 | 来源/提供方 | 描述 | 获取逻辑 | 备注 | 上报阶段获取来源 |
| --- | --- | --- | --- | --- | --- |
| branch | FEDO | 开发分支 | 从工作流中获取开发分支信息 |  |  |
| endTime | Code | 首次 commit 的时间戳 | 通过 Code 接口获取 commit 信息 |  |  |
| startTime | Code | 本次 commit 的时间戳 | 通过 Code 接口获取 commit 信息 |  |  |
| **firstCommitTime** | Code | PR 上第一个 commit 时间戳 | 通过 Code 接口获取 commit 信息 |  |  |
| **mainBranch** | FEDO | 业务仓库的主分支 | 工作流配置当前项目主分支 |  |  |
| repo | FEDO | 仓库地址 | 通过 FEDO 项目信息获取 |  |  |
| commit | Code | push时的最新commit | 通过 Code 接口获取 commit 信息 |  |  |
| **通用字段** |  |  |  |  |  |
| user | FEDO | 操作人 | FEDO 当前工作流执行者 |  |  |
| step | FEDO | 数据上报阶段 | 固定值 PUSH_TEST |  |  |
| trigger | ? | ? | "" |  |  |
| from | FEDO | 上报数据的来源 | 固定值 FEDO |  |  |

PR 创建

| 字段 | 来源/提供方 | 描述 | 获取逻辑 | 备注 | 上报阶段获取来源 |
| --- | --- | --- | --- | --- | --- |
| startTime | FEDO | pr创建时间 | 在工作流中创建 PR 的时间 |  | 通过查询 featureBranch -> releaseBranch PR 信息获取 |
| endTime | FEDO | 当前时间 | 系统获取 |  | new Date() |
| **sourceBranch** | FEDO | pr源分支 | FEDO 工作流获取 |  | workflow.featureBranch |
| **targetBranch** | FEDO | pr目标分支 | FEDO 工作流获取 |  | workflow.releaseBranch |
| commit | Code | push时的最新commit | 通过 Code 接口获取 commit 信息 |  | 通过查询 featureBranch -> releaseBranch PR 信息获取 sourchBranch 最新 commit |
| repo | FEDO | 仓库地址 | 通过 FEDO 项目信息获取 |  | project.repo_url |
| id | FEDO | 上报系统对应事项 ID | FEDO 任务/工作流 ID |  | workflowId |
| **prId** | Code | pull request id | 通过 Code 接口创建 PR 后获取，保存在工作流内 |  | 通过查询 featureBranch -> releaseBranch PR 信息获取 |
| **firstCommitTime** | Code | pr上第一个commit时间戳 | 通过 Code 接口获取 commit 信息 | 需要关注 diff 哪个分支 | 通过查询 featureBranch & mainBranch 的 diff 信息，倒序获取 |
| url | FEDO | 业务系统地址 | FEDO 当前工作流访问地址 |  | env.executeInfo.workflowUrl |
| **通用字段** |  |  |  |  |  |
| user | FEDO | 操作人 | FEDO 当前工作流执行者 |  | task.designate_user |
| step | FEDO | 数据上报阶段 | 固定值 PR_TEST |  | 固定值 PR_TEST |
| trigger | ? | ? | ? |  | 固定值 '' |
| from | FEDO | 上报数据的来源 | 固定值 FEDO |  | 固定值 FEDO |

PR 合并

| 字段 | 来源/提供方 | 描述 | 获取逻辑 | 备注 | 上报阶段获取来源 |
| --- | --- | --- | --- | --- | --- |
| startTime | FEDO | pr创建时间 | 在工作流中创建 PR 的时间 |  | 通过查询 featureBranch -> releaseBranch PR 信息获取 |
| endTime | FEDO | PR合并时间 | 在工作流中合并 PR 的时间 |  | 通过查询 featureBranch -> releaseBranch PR 信息获取 |
| **sourceBranch** | FEDO | pr源分支 | FEDO 工作流获取 |  | workflow.featureBranch |
| **targetBranch** | FEDO | pr目标分支 | FEDO 工作流获取 |  | workflow.releaseBranch |
| commit | Code | push时的最新commit | 通过 Code 接口获取 commit 信息 |  | 通过查询 featureBranch -> releaseBranch PR 信息获取 sourchBranch 最新 commit |
| repo | FEDO | 仓库地址 | 通过 FEDO 项目信息获取 |  | project.repo_url |
| id | FEDO | 上报系统对应事项 ID | FEDO 任务/工作流 ID |  | worlkflowId |
| prId | Code | pull request id | 通过 Code 接口创建 PR 后获取 |  | 通过查询 featureBranch -> releaseBranch PR 信息获取 |
| **firstCommitTime** | Code | pr上第一个commit时间戳 | 通过 Code 接口获取 commit 信息 |  | 通过查询 featureBranch & mainBranch 的 diff 信息，倒序获取 |
| url | FEDO | 业务系统地址 | FEDO 当前工作流访问地址 |  | env.executeInfo.workflowUrl |
| **通用字段** |  |  |  |  |  |
| user | FEDO | 操作人 | FEDO 当前工作流执行者 |  | task.designate_user |
| step | FEDO | 数据上报阶段 | 固定值 PR_MERGE |  | 固定值 PR_TEST |
| trigger | ? | ? | ? |  | 固定值 '' |
| from | FEDO | 上报数据的来源 | 固定值 FEDO |  | 固定值 FEDO |

发布

| 字段 | 来源/提供方 | 描述 | 获取逻辑 | 备注 | 上报阶段获取来源 |
| --- | --- | --- | --- | --- | --- |
| startTime | FEDO | 开始发布时间 | FEDO 工作流触发对应发布平台操作成功的时间 | 能从 FEDO 上触发对应系统发布即可获取到 | 各个发布节点落点工作流变量
字段为 MDO_PUBLISH_PARAM
类型为 object[] (聚合发布场景可能有多个项目)
灰度单独上报：MDO_GREY_PARAM
**MDO_PUBLISH_PARAM.startTime** |
| endTime | 各发布平台 | 结束发布时间 | FEDO 获取到对应发布平台发布成功的时间 | Web: 由工作流节点调用 Talos 获取完成回调时间
MRN：由工作流节点获取
小程序：由工作流节点获取
Native：Sigma 或 HPX 发布完成后是否有对应回调或通知 | **MDO_PUBLISH_PARAM.endTime** |
| branch | FEDO | 发布分支或 tag | FEDO 工作流获取 |  | **MDO_PUBLISH_PARAM.branch**
workflow.releaseBranch |
| commit | Code&FEDO | push时的最新commit | 通过 Code 接口获取 commit 信息 | 需要和 PR Merge commit 一致（卡控）
**待确定，目前流程内均未对同步 master 代码添加流程，因此卡控另行讨论** | **MDO_PUBLISH_PARAM.commit** 
**可以由节点处理**
获取 releaseBranch 的最新 commit |
| repo | FEDO | 仓库地址 | 通过 FEDO 项目信息获取 |  | **MDO_PUBLISH_PARAM.repo**
project.repo_url |
| id | FEDO | appkey | 对应项目的 appkey |  | workflowId |
| **deployPercent** | - | 中心发布占比 | - | 对前端该字段可能无用，直接传 100 | 100 |
| commitId | Code&FEDO | push时的最新commit | 通过 Code 接口获取 commit 信息 |  | **MDO_PUBLISH_PARAM.commitId**
**可以由节点处理**
获取 releaseBranch 的最新 commit |
| **deployUrl** | 各发布系统 | 发布链接 | FEDO 工作流获取 | 原始发布系统地址 | **MDO_PUBLISH_PARAM.deployUrl**
如果没有对应发布系统地址，则使用 FEDO 工作流地址 |
| name | FEDO/各发布系统 | 平台名称，appkey/gitRepo | 通过 FEDO 项目信息获取 | web：仓库名称
mrn：bundle 名称
小程序：仓库名称
Native：app/组件名称 | **MDO_PUBLISH_PARAM.name**
web、小程序：project.repo_url
mrn：通过 mrn_config 获取 bundleName
Native：项目配置，字段待定 |
| **deployType** | FEDO | 发布类型， 正常发布是deploy，回滚是rollback | FEDO 工作流获取 |  | config |
| url | FEDO | FEDO 工作流地址 | FEDO 工作流获取 |  | env.executeInfo.workflowUrl |
| repoType | FEDO | 项目技术栈信息 | FEDO 工作流获取 |  | **MDO_PUBLISH_PARAM.repoType**
project.fedo_type // 可能需要转换 |
| **通用字段** |  |  |  |  |  |
| user | FEDO | 操作人 | FEDO 当前工作流执行者 |  | **MDO_PUBLISH_PARAM.user - 聚合发布需要** |
| step | - | 数据上报阶段 | 固定值 PR_MERGE |  | 固定值 PR_MERGE |
| trigger | ? | ? | ? |  | ? |
| from | - | 上报数据的来源 | 固定值 FEDO |  | 固定值 FEDO |

### **节点 or 工作流改造/适配方案**

1. PR 创建&PR 合并阶段不需要各工作流调整，由上报节点统一进行处理，工作流确保需要的分支信息提供正确（fetureBranch | hotfix、releaseBranch、mainBranch）
2. 在工作流配置/项目添加主分支 mainBranch 信息，使用固定分支发布的（release、master）必须在工作流模板配置增加 releaseBranch 且为只读
3. 聚合发布的场景，对多个研发任务进行遍历上报发布信息，在研发工作流变量建议落点 project 及 task 字段，希望工作流引擎能限制这两个字段不被其他节点作为出参使用

数据-落点 workflow variable，变量被覆盖 | 节点被摘除的问题

仅供内部使用，未经授权，切勿外传

评论(0)

浏览 121 次  共 22 人浏览

[](https://api.neixin.cn/xs/api/profile/image_2037334237942960140/2037334237963268177?t=THUMB_PROFILE)

写点你要说的

[](https://km.sankuai.com/api-wm/image/visible/custombyid?r=0&g=0&b=0&a=30&deg=-15&fontSize=90&customStr=C-3)