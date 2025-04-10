---
title: Cloud Manager 2025.4.0 版的发行说明
description: 了解 Adobe Managed Services 上有关 Cloud Manager 2025.4.0 版本的信息。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 40d093ce7d6839fff4ba16f790c61b96cb88dda5
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 88%

---

# Adobe Managed Services 上 Cloud Manager 2025.4.0 版的发行说明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解 Adobe Managed Services 上有关 [!UICONTROL Cloud Manager] 2025.4.0 版本的信息。

另请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.4.0的发布日期是2025年4月10日星期四。

下一个计划发布于2025年5月8日星期四。

<!--
## What's new {#what-is-new}

* 
-->


## 早期采用计划 {#early-adoption}

参与Cloud Manager的早期采用计划，在即将发布的功能正式发布之前获得独家访问权。

目前提供以下早期采用机会：

### 自带 Git：现支持 GitLab 和 Bitbucket {#gitlab-bitbucket}

**自带 Git** 功能已得到扩展，包括对 GitLab 和 Bitbucket 等外部存储库的支持。这项新的支持是对专用和企业 GitHub 存储库现有支持的补充。添加这些新的存储库时，您还可以将它们直接链接到管道。您可以在公共云平台、专用云平台或基础架构中托管这些存储库。这种集成还消除了与 Adobe 存储库持续同步代码的需要，并提供了在提取请求合并到主分支之前对其进行验证的功能。

使用外部存储库（不包括 GitHub 托管的存储库）和&#x200B;**部署触发器**&#x200B;设置为&#x200B;**在 Git 发生更改时**&#x200B;的管道现在会自动启动。

请参阅[在 Cloud Manager 中添加外部存储库](/help/managing-code/external-repositories.md)。

![添加“存储库”对话框](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>目前，开箱即用的提取请求代码质量检查仅限于 GitHub 托管的存储库，但正在计划将此功能扩展到其他 Git 供应商的更新。

如果您有兴趣测试此新功能并分享您的反馈，请从与您的 Adobe ID 关联的电子邮件地址发送电子邮件至 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)。请务必注明您想要使用的 Git 平台以及您是处于专用/公共还是企业存储库结构中。

### 仅暂存和仅生产管道 {#staging-production-only-pipelines}

Adobe 宣布推出对[仅暂存和仅生产管道](/help/using/stage-prod-only.md)的支持。此新功能可让您将全栈生产部署管道划分为更小、更专业的部署。

如果您想测试此功能并提供反馈，请使用与您的 Adobe ID 关联的电子邮件地址发送电子邮件至 [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com)。



<!--
### Self-service Service Pack updates for AMS Cloud Manager customers 

As part of the early adopters program, Adobe Managed Services Cloud Manager customers can now perform self-service service pack updates through the **Cloud Manager** user interface. This feature is currently available *only for development environments* and includes limited error reporting for failures.  

Customers can check for service pack updates on the **Program Overview** page under the **Environments** section (**three-dot menu**).

![Check for updates menu option](/help/release-notes/assets/check-for-updates-1.png)

![Update Service Pack dialog box](/help/release-notes/assets/check-for-updates-2.png)

The installation and upgrade process can be tracked on the **Activity** page. 

Once the process is complete, customers must **approve the execution** for the service pack upgrade to finalize successfully.

![Approve service page update](/help/release-notes/assets/check-for-updates-3.png)

If you are interested in testing this new feature and sharing your feedback, contact your Adobe Customer Success Engineer.

See also [Service Pack Updates for Development Environments - Early Adopter](/help/using/service-packs-environments.md).
-->



## 错误修复 {#bug-fixes}

* A

已知问题 {#known-issues}

* A —>
