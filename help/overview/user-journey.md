---
title: 用户历程
description: 了解各种载入场景和Cloud Manager快速入门。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 6a5615c0db91c62fc8858b967021b46c7b383aa0
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 21%

---


# 用户历程 {#user-journey}

作为AEM (Adobe Experience Manager)用户，您可能适合以下场景之一：

* 您是AEM的新用户。
* 您当前使用的是AEM 6.x。
* 您需要升级到AEM 6.5才能使用[!UICONTROL Cloud Manager]。

本文档列出了这三种场景，并解释了您的[!UICONTROL Cloud Manager]入门历程。

>[!NOTE]
>
>[!UICONTROL Cloud Manager] 仅适用于使用 AEM 6.4 或更高版本的 Adobe Managed Services (AMS) 客户。

## 新用户引导 {#onboarding}

根据您是 AMS 新手还是现有 AMS 客户，新用户引导过程会有所不同。

### Adobe Managed Services 新手 {#new-to-ams}

作为新客户，您将加入[!UICONTROL Cloud Manager]，这是AdobeManaged Services的新用户引导过程的一部分。

在新用户引导过程中，您将收到一封欢迎电子邮件，其中包括：

* 用于访问[!UICONTROL Cloud Manager]的URL。
* 登录[!UICONTROL Experience Cloud]的说明。
* 有关使用 Admin Console 管理您的用户及其相应权限以便他们能够访问 [!UICONTROL Cloud Manager]（如果需要）的说明。

### 当前AdobeManaged Services客户 {#existing-customer}

作为现有AMS客户，您必须首先将现有的生产环境和非生产环境升级到AEM 6.4或更高版本。

在升级过程中，您将登记到Cloud Manager并获得用于访问[!UICONTROL Cloud Manager]的URL。 此外，对于那些需要访问[!UICONTROL Cloud Manager]的用户，您必须开始使用该Admin Console来管理这些用户及其相应权限。

您现有的AEM项目还需要符合推荐的最佳实践，因为您已开始使用[!UICONTROL Cloud Manager]将新的代码更改部署到AEM环境。

要获取有关升级到AEM 6.5的好处的其他信息，请参阅[升级到AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade)。

## 访问[!UICONTROL Cloud Manager] {#accessing-cloud-manager}

使用您的AdobeIdentity Management凭据登录[!UICONTROL Experience Cloud]登录页面。 从该位置，从解决方案切换器中选择AEM以访问[!UICONTROL Cloud Manager]和您的AEM环境。

在首次登录[!UICONTROL Cloud Manager]后，您将有权直接从[!UICONTROL Cloud Manager] UI访问AEM环境。 此时，您已能开始探索 [!UICONTROL Cloud Manager] 的所有可能性，并准备好您的第一个代码分支以部署到暂存和生产环境。

若要开始使用[!UICONTROL Cloud Manager]，请参阅[首次登录](/help/getting-started/first-time-login.md)。

有关AEM的其他信息，请参阅[部署和维护](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/implementing/deploying/deploying/deploy)。

## 开始使用[!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

登录[!UICONTROL Cloud Manager]后，可通过以下操作开始使用AEM项目：

1. 设置您的代码存储库环境。
1. 设置您的团队和角色。 通过使用 Admin Console 将用户添加到 [!UICONTROL Cloud Manager] 配置文件来分配角色成员资格。
1. 在Git存储库中设置源代码分支。
1. 根据负载和性能KPI（关键绩效指标）定义您的目标。
1. 定义测试场景，以便在通过所有质量检查后将代码成功部署到暂存环境和生产环境。

## 端到端历程 {#end-to-end-journey}

此图从较高层面说明了使用[!UICONTROL Cloud Manager] CI/CD管道将代码更改部署到暂存环境和生产环境时的客户历程。

![端到端历程](/help/assets/screen_shot_2018-05-15at124004pm.png)
