---
title: Cloud Manager 2024.10.0 版的发行说明
description: 了解 Cloud Manager 2024.10.0 的发行说明。
feature: Release Information
source-git-commit: 94d5f3487408f9d8908bb15221c48ef768390527
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 24%

---

# Cloud Manager 2024.10.0 版的发行说明 {#release-notes}

本页面记录了 [!UICONTROL Cloud Manager] 2024.10.0 版的发行说明。

>[!NOTE]
>
>有关 AEM as a Cloud Service 中的 Cloud Manager 的最新发行说明，请参阅 [AEM as a Cloud Service 中的 Cloud Manager 的最新发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)。



## 发布日期 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2024.10.0的发布日期是2024年10月3日。

下一个版本计划于2024年11月14日发布。



## 新增功能 {#what-is-new}

* <!-- BOTH CS & AMS --> Cloud Manager中使用的AEM原型版本现已更新到版本26。 请参阅[https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases)
<!-- (CMGR-59817) -->



## 早期采用计划 {#early-adoption}

加入Cloud Manager的早期采用计划，并有机会测试即将推出的功能。

### 自带Git — 现在支持GitLab和Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**自带Git**&#x200B;功能已扩展到包括对GitLab和Bitbucket等外部存储库的支持。 此新支持是对专用和企业GitHub存储库的现有支持之外的支持。 添加这些新存储库时，您还可以将其直接链接到管道。 您可以在公共云平台上或私有云或基础架构内托管这些存储库。 此集成还消除了对与Adobe存储库进行持续代码同步的需求，并提供了在合并到主分支之前验证拉取请求的功能。

请参阅[在Cloud Manager中添加外部存储库](/help/managing-code/external-repositories.md)。

![添加存储库对话框](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>目前，开箱即用的拉取请求代码质量检查专供GitHub托管的存储库使用，但正在研究如何将此功能扩展到其他Git供应商。

如果您有兴趣测试这项新功能并分享您的反馈，请从与Adobe ID关联的电子邮件地址向[Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)发送电子邮件。 请务必包括您要使用的Git平台，以及您使用的是专用/公共还是企业存储库结构。

### 仅暂存和仅生产管道 {#staging-production-only-pipelines}

Adobe宣布引入对[仅限暂存和仅限生产的管道](/help/using/stage-prod-only.md)的支持。 此新功能可让您将全栈生产部署管道划分为更小、更专业的部署。

如果要测试此功能并提供反馈，请通过与Adobe ID关联的电子邮件地址向[Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com)发送电子邮件。

<!-- ## Bug fixes

* text
-->

## 已知问题 {#known-issues}

{{content-copy-known-issues}}
