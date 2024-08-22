---
title: Git 与 Adobe Cloud Manager 的集成
description: 本视频系列介绍了客户管理的（内部部署）Git存储库的设置以及它与AdobeCloud Manager的集成。
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 17%

---


# Git与AdobeCloud Manager集成

AdobeCloud Manager附带了一个Git存储库，用于使用Cloud Manager的CI/CD管道部署代码。 您可以使用现成的Cloud Manager Git存储库，也可以选择将内部部署或客户管理的Git存储库与Cloud Manager集成。

## Git集成概述

>[!VIDEO](https://video.tv.adobe.com/v/28710/) （3分钟、11秒）

本视频系列探究了多个有关将客户管理的Git存储库与Cloud Manager集成的用例。

* [初始同步](#initial-sync)
* [基本分支策略](#branching-strategy)
* [功能分支开发](#feature-development)
* [生产部署](#production-deployment)
* [同步版本标记](#sync-tags)

本视频系列假定您具有Git和源代码控制管理的基本知识。 有关Git的更多详细信息，请参阅下面](#additional-resources)的[其他资源。

本视频系列中概述的步骤和命名惯例代表了有关使用客户管理的Git存储库和Cloud Manager的一些最佳实践。 预计所描述的惯例和工作流将适用于各个开发团队。

有关 Cloud Manager 的完整概述，请参阅 [Cloud Manager 简介](/help/introduction.md)。

## 初始同步 {#initial-sync}

将客户管理的Git存储库与Cloud Manager的Git存储库同步的第一步。

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12) （8分钟）

## 基本分支策略 {#branching-strategy}

设置基本分支策略以利用Cloud Manager的[生产](/help/using/production-pipelines.md)和[非生产管道](/help/using/non-production-pipelines.md)。

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12) （3分钟，48秒）

## 功能分支开发 {#feature-development}

使用功能分支隔离客户管理的Git存储库中的代码更改，并与Cloud Manager的Git存储库同步，以使用非生产管道进行代码质量和验证测试。

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12) （9分钟）

## 生产部署 {#production-deployment}

在客户管理的Git存储库中为生产版本准备代码，并与Cloud Manager的Git存储库同步，以部署到暂存和生产环境。

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12) （6分钟6秒）

## 同步版本标记 {#sync-tags}

您可以将Cloud Manager Git存储库中的版本标记同步到客户管理的Git存储库中。 此功能可让您了解已将哪些代码部署到暂存环境和生产环境。

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12) （2分钟，57秒）

## 其他资源 {#additional-resources}

* [Cloud Manager 简介](/help/introduction.md)
* [GitHub 资源](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Atlassian Git 教程](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git 备忘单](https://education.github.com/git-cheat-sheet-education.pdf)
