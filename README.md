# surge-rules

这是 `kukubob` 自用的 Surge 规则发布仓库。规则由 GitHub Actions 从
[`SukkaW/Surge`](https://github.com/SukkaW/Surge) 的 `master` 分支构建，
每天自动更新两次，也可以在 Actions 页面手工触发。

本仓库只托管生成后的 `List/` 规则，不包含代理节点、订阅地址或 Surge
完整配置。`UPSTREAM_COMMIT` 记录当前规则对应的上游提交。

## Surge 引用

```ini
RULE-SET,https://raw.githubusercontent.com/kukubob/surge-rules/main/List/non_ip/apple_intelligence.conf,AI,no-resolve
RULE-SET,https://raw.githubusercontent.com/kukubob/surge-rules/main/List/non_ip/ai.conf,AI,no-resolve
RULE-SET,https://raw.githubusercontent.com/kukubob/surge-rules/main/List/ip/ai.conf,AI,no-resolve
```

## 更新策略

- 定时任务：每天 UTC 06:47、18:47，即上游计划构建约 90 分钟后。
- 更新过程：检出上游源码，安装上游锁定的依赖，重新生成完整 `List/`，
  验证关键 AI 规则非空后才提交。
- 构建阶段没有仓库写入凭据；只有最终发布步骤获得短时 `GITHUB_TOKEN`。
- 没有内容变化时不会产生空提交。

## 来源与许可

规则来源、构建代码及许可归 [`SukkaW/Surge`](https://github.com/SukkaW/Surge)
项目及其贡献者所有。本仓库保留上游许可证与生成文件中的来源信息。

