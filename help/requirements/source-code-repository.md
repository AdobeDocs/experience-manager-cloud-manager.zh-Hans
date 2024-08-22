---
title: 源代码存储库
description: 了解为您在Cloud Manager中拥有的每个项目配置的Git存储库。
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 7%

---


# Source代码存储库 {#source-code-repository}

了解为您在Cloud Manager中拥有的每个项目配置的Git存储库。

## Cloud Manager存储库 {#cloud-manager-repository}

您的 [!UICONTROL AEM Managed Services] 订阅包括由 Adobe 配置和管理的源代码存储库。每个项目都分配有一个唯一的Git存储库，可在其中存储和保护您的关联代码。

作为最佳实践，您应始终使用Cloud Manager的Git存储库，该存储库是空的，没有任何配置的分支或示例项目。 Cloud Manager为其Git存储库提供了一个专用访问令牌，允许您使用任何Git客户端创建分支、管理代码、检索提交历史记录等。

有关如何在Git中设置分支的更多信息，请参阅[配置版本分支](/help/getting-started/configuring-branches.md)。

有关如何将Cloud Manager的Git存储库与CI/CD管道一起使用的更多信息，请参阅[配置生产管道](/help/using/production-pipelines.md)和[配置非生产管道](/help/using/non-production-pipelines.md)以了解更多信息。

## 内部部署存储库 {#on-premise-repository}

您可能有一个现有的Git存储库并希望继续使用它，在这种情况下，您可以将Git的功能用于多个远程存储库。 将继续在您的Git存储库中进行日常开发。 当版本分支已准备好部署到生产环境时，您可以将最新代码推送到Cloud Manager的Git存储库并触发Cloud Manager CI/CD管道。

要查看常见的Git命令，请参阅[Git备忘单](https://education.github.com/git-cheat-sheet-education.pdf)。
