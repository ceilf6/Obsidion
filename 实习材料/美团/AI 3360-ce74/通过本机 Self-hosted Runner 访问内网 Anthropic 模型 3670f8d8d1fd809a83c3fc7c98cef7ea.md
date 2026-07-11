# 通过本机 Self-hosted Runner 访问内网 Anthropic 模型

## Summary

- 采用 **GitHub Actions self-hosted runner 跑在你的电脑上**：工作流仍由 GitHub 触发，但 job 实际在本机执行，因此能访问 `http://10.233.132.37:3000`。
- repo-guard 已支持自定义 `provider/model/api-key/base-url`，无需改核心代码；`provider=anthropic` 会调用 `/v1/messages`。
- 不建议把内网模型通过公网反代暴露给 GitHub-hosted runner，除非有企业级鉴权、TLS、审计和访问控制。

## Key Changes

- 在目标仓库的 GitHub 页面添加一个 repository-level self-hosted runner，安装到你的电脑，使用专用 label：`repo-guard-intranet`。
- workflow 的 job 改为：

```yaml
jobs:
  guard:
    runs-on: [self-hosted, macOS, repo-guard-intranet]
    permissions:
      contents: read
      pull-requests: write
      issues: write
    steps:
      - uses: ceilf6/repo-guard@main
        with:
          provider: anthropic
          model: claude-opus-4-7-thinking
          api-key: ${{ secrets.LLM_API_KEY }}
          base-url: ${{ vars.LLM_BASE_URL }}
```

- GitHub Secrets/Variables：
    - `LLM_API_KEY`: 使用新生成或轮换后的 key，不要写进 YAML。
    - `LLM_BASE_URL`: `http://10.233.132.37:3000`
- 安全边界：
    - 这个 runner label 只给 repo-guard workflow 用。
    - 不在同一个 runner 上跑会 checkout 并执行 PR 代码的 CI。
    - 如果仓库可能收到外部 fork PR，默认跳过 fork PR，改用维护者手动评论触发或手动 dispatch。
    - runner 尽量用单独 macOS 用户运行，避免读取你的个人 SSH key、浏览器凭据等本机敏感数据。
    - 你刚刚贴出的 key 建议轮换后再放进 GitHub Secrets。

## Test Plan

- 本机先用 Anthropic 格式探测：

```bash
curl -sS "<http://10.233.132.37:3000/v1/messages>" \\
  -H "content-type: application/json" \\
  -H "x-api-key: $LLM_API_KEY" \\
  -H "anthropic-version: 2023-06-01" \\
  -d '{"model":"claude-opus-4-7-thinking","max_tokens":32,"messages":[{"role":"user","content":"ping"}]}'
```

- 启动本机 runner 后，先用 `workflow_dispatch` 跑一次最小 repo-guard 测试。
- 再用一个测试 PR 或 issue comment 触发真实 review，确认：
    - job 被分配到 `repo-guard-intranet` runner；
    - LLM 请求成功；
    - repo-guard 正常发布 issue/PR 评论。

## Assumptions And References

- 已确认该内网模型要用 **Anthropic API 格式**。
- 你的电脑需要在线，并保持能访问公司内网/VPN。
- repo-guard 现有实现已支持这些参数：[action.yml](https://www.notion.so/Users/ceilf6/Desktop/myrepos/Wiki/AI/3-Application/repo-guard-app/action.yml:55)、[scripts/llm-client.mjs](https://www.notion.so/Users/ceilf6/Desktop/myrepos/Wiki/AI/3-Application/repo-guard-app/scripts/llm-client.mjs:77)。
- GitHub 官方说明：workflow 可用 labels 路由到 self-hosted runner；自定义 label 会累积匹配；self-hosted runner 不应暴露给不可信 workflow，因为可能被持久化 compromise。参考 [Using self-hosted runners](https://docs.github.com/en/actions/how-tos/manage-runners/self-hosted-runners/use-in-a-workflow)、[Choosing the runner](https://docs.github.com/en/actions/how-tos/write-workflows/choose-where-workflows-run/choose-the-runner-for-a-job)、[Secure use reference](https://docs.github.com/en/actions/reference/security/secure-use)。