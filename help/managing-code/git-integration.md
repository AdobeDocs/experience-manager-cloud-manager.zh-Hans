---
title: Git 与 Adobe Cloud Manager 的集成
description: 本视频系列介绍了客户管理的（内部部署）Git 存储库的设置以及它与 Adobe Cloud Manager 的集成。
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 3671772a1369273d89fde101ba084a6e2f8ce8dc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Git 与 Adobe Cloud Manager 的集成

Adobe Cloud Manager 附带了一个 Git 存储库，用于使用 Cloud Manager 的 CI/CD 管道部署代码。您可以使用现成的 Cloud Manager 的 Git 存储库，也可以选择将内部部署或客户管理的 Git 存储库与 Cloud Manager 集成。

## Git 集成概述

>[!VIDEO](https://video.tv.adobe.com/v/28710/)（3 分钟，11 秒钟）

本视频系列探究了多个有关将客户管理的 Git 存储库与 Cloud Manager 集成的用例。

* [初始同步](#initial-sync)
* [基本分支策略](#branching-strategy)
* [功能分支开发](#feature-development)
* [生产部署](#production-deployment)
* [同步版本标记](#sync-tags)

本视频系列假定您掌握 Git 和源代码控制管理的基本知识。有关 Git 的更多详细信息，请参阅[以下附加资源](#additional-resources)。

本视频系列中概述的步骤和命名惯例代表了有关使用客户管理的 Git 存储库和 Cloud Manager 的一些最佳实践。预计所描述的惯例和工作流将适用于各个开发团队。

有关 Cloud Manager 的完整概述，请参阅 [Cloud Manager 简介](/help/introduction.md)。

## 初始同步 {#initial-sync}

将客户管理的 Git 存储库与 Cloud Manager 的 Git 存储库同步的首要步骤。

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)（8 分钟）

## 基本分支策略 {#branching-strategy}

设置基本分支策略以利用 Cloud Manager 的[生产管道](/help/using/production-pipelines.md)和[非生产管道](/help/using/non-production-pipelines.md)。

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)（3 分钟，48 秒钟）

## 功能分支开发 {#feature-development}

使用功能分支隔离客户管理的 Git 存储库中的代码更改，并与 Cloud Manager 的 Git 存储库同步，以便使用非生产管道进行代码质量和验证测试。

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)（9 分钟）

## 生产部署 {#production-deployment}

在客户管理的 Git 存储库中为生产版本准备代码，并与 Cloud Manager 的 Git 存储库同步，以便部署到暂存和生产环境。

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)（6 分钟，6 秒钟）

## 同步版本标记 {#sync-tags}

您可以将版本标记从 Cloud Manager Git 存储库同步到客户管理的 Git 存储库。此功能可让您查看已部署到暂存和生产环境的代码。

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)（2 分钟，57 秒钟）

## 其他资源 {#additional-resources}

* [Cloud Manager 简介](/help/introduction.md)
* [GitHub 资源](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Atlassian Git 教程](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git 备忘单](https://education.github.com/git-cheat-sheet-education.pdf)
