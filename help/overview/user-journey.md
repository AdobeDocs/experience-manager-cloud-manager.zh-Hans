---
title: 用户历程
description: 了解不同的新用户引导场景并开始使用 Cloud Manager。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '532'
ht-degree: 100%

---


# 用户历程 {#user-journey}

作为 AEM (Adobe Experience Manager) 用户，您可能符合以下场景之一：

* 您是 AEM 新手。
* 您现在正在使用 AEM 6.x。
* 您需要升级到 AEM 6.5 才能使用 [!UICONTROL Cloud Manager]。

本文档列出了这三种场景，并解释如何开始使用 [!UICONTROL Cloud Manager]。

>[!NOTE]
>
>[!UICONTROL Cloud Manager] 仅适用于使用 AEM 6.4 或更高版本的 Adobe Managed Services (AMS) 客户。

## 新用户引导 {#onboarding}

根据您是 AMS 新手还是现有 AMS 客户，新用户引导过程会有所不同。

### Adobe Managed Services 新手 {#new-to-ams}

作为新客户，在 Adobe Managed Services 新用户引导过程中，您将会登录 [!UICONTROL Cloud Manager]。

在新用户引导过程中，您将收到一封欢迎电子邮件，其中包括以下内容：

* 访问 [!UICONTROL Cloud Manager ]的 URL。
* 登录 [!UICONTROL Experience Cloud] 的说明。
* 有关使用 Admin Console 管理您的用户及其相应权限以便他们能够访问 [!UICONTROL Cloud Manager]（如果需要）的说明。

### 当前 Adobe Managed Services 客户 {#existing-customer}

作为现有 AMS 客户，您必须首先将现有的生产环境和非生产环境升级到 AEM 6.4 或更高版本。

在进行升级期间，您会加入 Cloud Manager 并获得用于访问 [!UICONTROL Cloud Manager] 的 URL。 此外，对于那些需要访问 [!UICONTROL Cloud Manager] 的用户，您必须开始使用 Admin Console 来管理这些用户及其相应权限。

您现有的 AEM 项目还需要符合推荐的最佳实践，因为您会开始使用 [!UICONTROL Cloud Manager] 将新的代码更改部署到 AEM 环境。

要获取有关升级到 AEM 6.5 的好处的其他信息，请参阅[升级到 AEM 6.5](https://experienceleague.adobe.com/zh-hans/docs/ experience-manager-65/content/implementing/deploying/upgrading/upgrade)。

## 访问 [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

使用您的 Adobe Identity Management 凭据登录 [!UICONTROL Experience Cloud] 登录页面。 然后，从解决方案切换器中选择 AEM，以访问 [!UICONTROL Cloud Manager] 和您的 AEM 环境。

在首次登录 [!UICONTROL Cloud Manager] 后，您将有权直接从 [!UICONTROL Cloud Manager] UI 访问 AEM 环境。此时，您已能开始探索 [!UICONTROL Cloud Manager] 的所有可能性，并准备将您的第一个代码分支部署到您的暂存和生产环境中。

要开始使用 [!UICONTROL Cloud Manager]，请参阅[首次登录](/help/getting-started/first-time-login.md)。

有关 AEM 的其他信息，请参阅[部署和维护](https://experienceleague.adobe.com/zh-hans/docs/ experience-manager-65/content/implementing/deploying/deploying/deploy)。

## 开始使用 [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

登录 [!UICONTROL Cloud Manager] 后，您可以通过执行以下操作开始使用 AEM 项目：

1. 设置您的代码存储库环境。
1. 设置您的团队和角色。 通过使用 Admin Console 将用户添加到 [!UICONTROL Cloud Manager] 配置文件来分配角色成员资格。
1. 在 Git 存储库中设置源代码分支。
1. 根据负载和性能 KPI（关键绩效指标）定义您的目标。
1. 定义测试场景，以便在成功通过所有质量检查后将代码部署到暂存环境和生产环境。

## 端到端历程 {#end-to-end-journey}

此图从较高层面说明了使用 [!UICONTROL Cloud Manager] CI/CD 管道将代码更改部署到暂存环境和生产环境时的客户历程。

![端到端历程](/help/assets/screen_shot_2018-05-15at124004pm.png)
