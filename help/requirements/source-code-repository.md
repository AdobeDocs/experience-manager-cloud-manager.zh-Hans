---
title: 源代码存储库
description: 了解为 Cloud Manager 中的每个程序配置的 Git 存储库。
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '245'
ht-degree: 100%

---


# 源代码存储库 {#source-code-repository}

了解为 Cloud Manager 中的每个程序配置的 Git 存储库。

## Cloud Manager 存储库 {#cloud-manager-repository}

您的 [!UICONTROL AEM Managed Services] 订阅包括一个由 Adobe 配置和管理的源代码存储库。每个项目都分配有一个唯一的 Git 存储库，您的关联代码将会存储在其中并受到保护。

作为最佳实践，您应始终使用 Cloud Manager 的 Git 存储库，该存储库是空的，没有配置任何分支或示例项目。Cloud Manager 为其 Git 存储库提供了专用访问令牌，让您可以使用任何 Git 客户端创建分支、管理代码、检索提交历史记录等。

有关如何在 Git 中设置分支的更多信息，请参阅[配置版本分支](/help/getting-started/configuring-branches.md)。

有关如何将 Cloud Manager 的 Git 存储库与 CI/CD 管道结合使用的更多信息，请参阅[配置生产管道](/help/using/production-pipelines.md)和[配置非生产管道](/help/using/non-production-pipelines.md)，以了解详情。

## 内部部署存储库 {#on-premise-repository}

您可能有一个现有的 Git 存储库并希望继续使用它，在这种情况下，您可以将 Git 的功能用于多个远程存储库。 在您的 Git 存储库中会继续进行日常开发。 当版本分支准备好部署到生产环境中时，您可以将最新代码推送到 Cloud Manager 的 Git 存储库并触发 Cloud Manager CI/CD 管道。

要查看常见的 Git 命令，请参阅 [Git 备忘单](https://education.github.com/git-cheat-sheet-education.pdf)。
