---
title: Cloud Manager 2025.8.0 版的发行说明
description: 了解 Adobe Managed Services 上有关 Cloud Manager 2025.8.0 版本的信息。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 5df4852716a608c7497e93eef030b4b5bd27d42b
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 75%

---

# Adobe Managed Services 上 Cloud Manager 2025.8.0 版的发行说明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解 Adobe Managed Services 上有关 [!UICONTROL Cloud Manager] 2025.8.0 版本的信息。

另请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.8.0的发布日期是2025年8月7日星期四。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一个版本计划于 2025 年 9 月 4 日星期四发布。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## 新增功能 {#what-is-new}

* **Adobe Experience Hub 即将推出**

  从 2025 年 8 月 19 日开始，Adobe 开始分阶段向所有 Adobe Experience Manager 用户推出新的 Experience Hub。

  Experience Hub 是一个统一的起点，提供个性化的上下文体验，帮助用户更快地实现目标。推出过程于 2025 年 8 月 26 日结束，届时所有用户均可使用。新的 Experience Hub 可直接在 [experience.adobe.com](https://experience.adobe.com/) 上访问。更多信息请参阅 [Adobe Experience Hub](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/experience-hub/experience-hub)。

* **仅暂存管道和仅生产管道**

  Cloud Manager现在支持仅暂存管道和仅生产管道。 通过此功能，您可以将全栈生产部署拆分为更小的、特定于用途的管道。<!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![选择“全栈代码”单选按钮并选择暂存环境的情况下添加非生产管道对话框](/help/release-notes/assets/add-non-production-pipeline.png)

  查看[仅暂存和仅生产管道](/help/using/stage-prod-only.md)。

* **管道收藏功能**

  在此版本中，Cloud Manager引入了固定收藏管道的功能，可让您将特定管道标记为收藏夹，以便它们显示在&#x200B;**管道**&#x200B;页面上的列表顶部。 此项增强功能可帮助您更轻松地查找并运行常用的管道。<!-- CMGR-68293 -->

  ![标记为收藏的管道](/help/release-notes/assets/pipeline-favorites.png) *已标记为收藏的两个管道。*

  请参阅[将管道标记为收藏](/help/using/managing-pipelines.md#pipeline-favorites)。


## Beta 计划 {#beta-program}

参与Cloud Manager的Beta计划，在即将发布的功能正式发布之前以独占方式访问这些功能。

目前提供以下机会：


### 使用您自己的 Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

客户现在可以将他们的 Azure DevOps Git 存储库加入到 Cloud Manager 中，同时支持现代 Azure DevOps 和旧版 VSTS（Visual Studio Team Services）两种存储库。

* Edge Delivery Services 用户可以使用已加入的存储库来同步和部署网站代码。
* 对于 AEM as a Cloud Service 和 Adobe Managed Services (AMS) 用户，该存储库可以链接到全栈和前端两种管道。

对其他管道类型以及通过代码质量管道进行提取请求验证的支持即将推出。

请参阅[在 Cloud Manager 中添加外部存储库](/help/managing-code/external-repositories.md)。

![添加“存储库”对话框](/help/release-notes/assets/azure-repo.png)

如果您有兴趣测试此新功能并分享您的反馈，请从与您的 Adobe ID 关联的电子邮件地址发送电子邮件至 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)。请务必注明您想要使用的 Git 平台以及您是处于专用/公共还是企业存储库结构中。

#### 管理访问令牌{#manage-access-tokens}

在 Cloud Manager 中使用&#x200B;**管理访问令牌**&#x200B;功能，可查看、重命名并删除与外部自带 Git 存储库（如 GitHub Enterprise、GitLab、Bitbucket 和 Azure DevOps）关联的访问令牌。

请参阅[管理访问令牌](/help/managing-code/manage-access-tokens.md)。

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## 错误修复 {#bug-fixes}

8月份的Cloud Manager版本中没有重大的错误修复。

<!--
Known Issues {#known-issues}

* A -->
