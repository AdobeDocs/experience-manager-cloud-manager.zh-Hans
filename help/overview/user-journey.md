---
title: 用户载入
description: 了解不同的新用户引导场景并开始使用 Cloud Manager。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
TQID: https://experienceleague.adobe.com/EnNaMZzu5bLUD3Jjsp6ovqFvoFM30ju4FOQJfmySLEk
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2cd89edca1c1dfac7f1b7b68eccdf1416efb4724
workflow-type: tm+mt
source-wordcount: 567
ht-degree: 62%

---

# 用户载入 {#user-journey}

作为AEM (Adobe Experience Manager)用户，您可以适应以下场景之一：

* 您是 AEM 新手。
* 您现在正在使用 AEM 6.x。
* 您需要升级到 AEM 6.5 才能使用 [!UICONTROL Cloud Manager]。

本文档介绍了这三个场景，并解释了开始使用[!UICONTROL Cloud Manager]的过程。

>[!NOTE]
>
>[!UICONTROL Cloud Manager] 仅适用于使用 AEM 6.4 或更高版本的 Adobe Managed Services (AMS) 客户。

## 新用户引导 {#onboarding}

根据您是 AMS 新手还是现有 AMS 客户，新用户引导过程会有所不同。

### Adobe Managed Services 新手 {#new-to-ams}

作为新客户，在Adobe Managed Services新用户引导过程中，您已登录[!UICONTROL Cloud Manager]。

在新用户引导过程中，您将收到一封欢迎电子邮件，其中包括以下内容：

* 访问 [!UICONTROL Cloud Manager &#x200B;]的 URL。
* 登录 [!UICONTROL Experience Cloud] 的说明。
* 有关使用Admin Console管理您的用户及其相应权限以便他们能够访问Cloud Manager（如果需要）的说明。

### 当前 Adobe Managed Services 客户 {#existing-customer}

作为现有 AMS 客户，您必须首先将现有的生产环境和非生产环境升级到 AEM 6.4 或更高版本。

在进行升级期间，您会加入 Cloud Manager 并获得用于访问 [!UICONTROL Cloud Manager] 的 URL。 此外，对于那些需要访问 [!UICONTROL Cloud Manager] 的用户，您必须开始使用 Admin Console 来管理这些用户及其相应权限。

您现有的AEM项目还需要符合建议的做法，因为您开始使用[!UICONTROL Cloud Manager]将新的代码更改部署到AEM环境。

要获取有关升级到 AEM 6.5 的好处的其他信息，请参阅[升级到 AEM 6.5](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade)。

## 访问 [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

使用您的 Adobe Identity Management 凭据登录 [!UICONTROL Experience Cloud] 登录页面。 从解决方案切换器中选择AEM以访问[!UICONTROL Cloud Manager]和您的AEM环境。

在首次登录 [!UICONTROL Cloud Manager] 后，您将有权直接从 [!UICONTROL Cloud Manager] UI 访问 AEM 环境。 此时，您已准备就绪，可使用[!UICONTROL Cloud Manager]的所有功能，并准备好您的第一个代码分支以部署到暂存和生产环境。

要开始使用 [!UICONTROL Cloud Manager]，请参阅[首次登录](/help/getting-started/first-time-login.md)。

有关 AEM 的其他信息，请参阅[部署和维护](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/implementing/deploying/deploying/deploy)。

## 开始使用 [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

登录 [!UICONTROL Cloud Manager] 后，您可以通过执行以下操作开始使用 AEM 项目：

1. 设置您的代码存储库环境。
1. 设置您的团队和角色。 通过使用 Admin Console 将用户添加到 [!UICONTROL Cloud Manager] 配置文件来分配角色成员资格。
1. 在 Git 存储库中设置源代码分支。
1. 定义负载和性能KPI（关键绩效指标）。
1. 定义测试场景，以便在成功通过所有质量检查后将代码部署到暂存环境和生产环境。

## 流程概述 {#end-to-end-journey}

下图总结了使用[!UICONTROL Cloud Manager] CI/CD管道将代码更改部署到暂存环境和生产环境时的过程。

![加入Cloud Manager的客户历程，通过环境配置或升级、用户和角色管理、项目实施和CI/CD管道显示新客户和现有客户的路径。](/help/assets/screen_shot_2018-05-15at124004pm.png)
