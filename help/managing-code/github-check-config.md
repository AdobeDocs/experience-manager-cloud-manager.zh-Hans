---
title: GitHub 检查专用存储库的配置
description: 了解如何控制自动创建的管道以验证对专用存储库的每个拉取请求。
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 94%

---

# GitHub 检查专用存储库的配置 {#github-check-config}

了解如何控制自动创建的管道以验证对专用存储库的每个拉取请求。

## GitHub 检查的配置 {#configuration}

使用[专用存储库](private-repositories.md#using)时，将自动创建[全栈栈代码质量管道](/help/overview/ci-cd-pipelines.md)。 每次更新提取请求时，此管道将启动。

您可以通过在专用存储库的默认分支中创建一份 `.cloudmanager/pr_pipelines.yml` 文件来控制这些检查。

```yaml
github:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR 
    importantMetricsFailureBehavior: CONTINUE
```

| 参数 | 可能的值 | 默认 | 描述 |
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` 或 `false` | `false` | 是仅保留此 GitHub 拉取请求的代码扫描结果中的最后一条评论，还是保留所有评论 |
| `type` | `CI_CD` | 不适用 | 定义 CI/CD 管道的行为 |
| `template.programID` | 整数 | 没有重复使用管道变量 | 可用于重用在每个 PR 自动创建的现有管道之一上设置的[管道变量](/help/getting-started/build-environment.md#pipeline-variables)。 |
| `template.pipelineID` | 整数 | 没有重复使用管道变量 | 可用于重用在每个 PR 自动创建的现有管道之一上设置的[管道变量](/help/getting-started/build-environment.md#pipeline-variables)。 |
| `namePrefix` | 字符串 | `Full Stack Code Quality Pipeline for PR` | 用于设置自动创建的管道的名称 |
| `importantMetricsFailureBehavior` | `CONTINUE` 或者 `FAIL` 或者 `PAUSE` | `CONTINUE` | 设置管道的重要量度行为<br>`CONTINUE` = 如果重要量度失败，管道将自动向前推进<br>`FAIL` = 如果重要量度失败，管道将以失败状态结束<br>`PAUSE` = 当重要量度失败且必须手动恢复时，代码扫描步骤将收到等待状态 |
