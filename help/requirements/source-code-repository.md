---
title: 源代码存储库
description: 了解为 Cloud Manager 中的每个程序配置的 Git 存储库。
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b24e9550f11486e7ed8da31d5da27f85ad5acaf2
workflow-type: tm+mt
source-wordcount: 236
ht-degree: 44%

---

# 源代码存储库 {#source-code-repository}

了解为 Cloud Manager 中的每个程序配置的 Git 存储库。

## Cloud Manager 存储库 {#cloud-manager-repository}

您的 [!UICONTROL AEM Managed Services] 订阅包括一个由 Adobe 配置和管理的源代码存储库。 每个项目都分配有一个唯一的Git存储库，可在其中存储和保护您的关联代码。

作为最佳实践，请始终使用Cloud Manager Git存储库，该存储库为空，没有配置任何分支或示例项目。 Cloud Manager 为其 Git 存储库提供了专用访问令牌，让您可以使用任何 Git 客户端创建分支、管理代码、检索提交历史记录等。

有关如何在 Git 中设置分支的更多信息，请参阅[配置版本分支](/help/getting-started/configuring-branches.md)。

要详细了解如何将Cloud Manager Git存储库与CI/CD管道一起使用，请参阅[配置生产管道](/help/using/production-pipelines.md)和[配置非生产管道](/help/using/non-production-pipelines.md)。

## 内部部署存储库 {#on-premise-repository}

如果您现有Git存储库并希望继续使用它，请将Git的功能用于多个远程存储库。 开发将继续在您的Git存储库中进行。 当版本分支已准备好部署到生产环境时，您可以将最新代码推送到Cloud Manager Git存储库并触发Cloud Manager CI/CD管道。

要查看常见的Git命令，请参阅[Git参考指南](https://education.github.com/git-cheat-sheet-education.pdf)。
