---
title: Cloud Manager 2025.6.0 版的发行说明
description: 了解 Adobe Managed Services 上有关 Cloud Manager 2025.5.0 版本的信息。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 38d398caf2323b603afd293aa9152308fefd323f
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 68%

---

# Adobe Managed Services 上 Cloud Manager 2025.6.0 版的发行说明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解 Adobe Managed Services 上有关 [!UICONTROL Cloud Manager] 2025.6.0 版本的信息。

另请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.6.0的发布日期是2025年6月5日星期四。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一个版本计划于 2025 年 7 月 10 日星期四发布。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## 新增功能 {#what-is-new}

* **仅暂存管道和仅生产管道**

  Cloud Manager现在支持仅暂存管道和仅生产管道。 通过此功能，您可以将全栈生产部署拆分为更小的、特定于用途的管道。<!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![选择“全栈代码”单选按钮并选择暂存环境的情况下添加非生产管道对话框](/help/release-notes/assets/add-non-production-pipeline.png)

  查看[仅暂存和仅生产管道](/help/using/stage-prod-only.md)。

* **管道收藏夹**

  在此版本中，Cloud Manager引入了固定收藏管道的功能，可让您将特定管道标记为收藏夹，以便它们显示在&#x200B;**管道**&#x200B;页面上的列表顶部。 此项增强功能可帮助您更轻松地查找并运行常用的管道。<!-- CMGR-68293 -->

  ![标记为收藏的管道](/help/release-notes/assets/pipeline-favorites.png) *已标记为收藏的两个管道。*

  请参阅[将管道标记为收藏](/help/using/managing-pipelines.md#pipeline-favorites)。


## 私人Beta计划 {#beta-program}

参与Cloud Manager的私人测试版计划，在即将发布的功能正式发布之前获得独家访问权。

目前提供以下私人测试版机会：


### 自带 Git：现支持 GitLab 和 Bitbucket {#gitlab-bitbucket}

**自带Git** (BYOG)功能已扩展到包括对外部存储库（如GitLab和Bitbucket）的支持。 这项新的支持是对专用和企业 GitHub 存储库现有支持的补充。添加这些新的存储库时，您还可以将它们直接链接到管道。您可以在公共云平台、专用云平台或基础架构中托管这些存储库。这种集成还消除了与 Adobe 存储库持续同步代码的需要，并提供了在提取请求合并到主分支之前对其进行验证的功能。

使用外部存储库（不包括 GitHub 托管的存储库）和&#x200B;**部署触发器**&#x200B;设置为&#x200B;**在 Git 发生更改时**&#x200B;的管道现在会自动启动。

请参阅[在 Cloud Manager 中添加外部存储库](/help/managing-code/external-repositories.md)。

![添加“存储库”对话框](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>目前，开箱即用的提取请求代码质量检查仅限于 GitHub 托管的存储库，但正在计划将此功能扩展到其他 Git 供应商的更新。

如果您有兴趣测试此新功能并分享您的反馈，请从与您的 Adobe ID 关联的电子邮件地址发送电子邮件至 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)。请务必注明您想要使用的 Git 平台以及您是处于专用/公共还是企业存储库结构中。

#### 管理访问令牌{#access-tokens}

结合使用&#x200B;**管理访问令牌**&#x200B;功能和BYOG可查看、重命名和删除与外部自带Git存储库（例如GitHub Enterprise、GitLab、Bitbucket和Azure DevOps）关联的访问令牌。

请参阅[管理访问令牌](/help/managing-code/manage-access-tokens.md)。

如果您有兴趣测试此新功能并分享您的反馈，请从与您的 Adobe ID 关联的电子邮件地址发送电子邮件至 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)。请务必注明您想要使用的 Git 平台以及您是处于专用/公共还是企业存储库结构中。


## 错误修复 {#bug-fixes}

* AEM Cloud Manager 现在能够正确地将由于在获取客户工件时发生 409 错误（冲突）导致的 Maven 构建失败，映射为客户导致的失败。这一变更通过区分内部错误和与客户环境设置相关的问题，改进了错误消息的显示方式。<!-- CMGR-66673 -->

<!--
Known Issues {#known-issues}

* A -->
