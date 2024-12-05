---
title: Cloud Manager 2024.12.0 版的发行说明
description: 了解关于Adobe Managed Services的Cloud Manager 2024.12.0版。
feature: Release Information
source-git-commit: ee79124a012106e53ffaaf9462202712f7078809
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 63%

---

# AdobeManaged Services上的Cloud Manager 2024.12.0发行说明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

了解有关AdobeManaged Services的[!UICONTROL Cloud Manager] 2024.12.0版本。

>[!NOTE]
>
>请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/ experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2024.12.0的发布日期是2024年12月5日。

下一个计划发行日期为2025年1月23日。

## 新增功能 {#what-is-new}

* AEM代码质量步骤现在使用SonarQube 9.9服务器，取代了更早的7.4版本。 此升级可提供额外的安全性、性能和代码质量检查，为您的项目提供更全面的分析和覆盖。<!-- CMGR-45683 -->

## 早期采用计划 {#early-adoption}

加入 Cloud Manager 早期采用计划，即有机会测试即将推出的功能。

### 自带 Git - 现支持 GitLab 和 Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**自带Git**&#x200B;功能已扩展到包括对外部存储库（如GitLab和Bitbucket）的支持。 这项新的支持是对专用和企业 GitHub 存储库现有支持的补充。添加这些新的存储库时，您还可以将它们直接链接到管道。您可以在公共云平台、专用云平台或基础架构中托管这些存储库。这种集成还消除了与 Adobe 存储库持续同步代码的需要，并提供了在提取请求合并到主分支之前对其进行验证的功能。

使用外部存储库（不包括GitHub托管的存储库）且&#x200B;**部署触发器**&#x200B;在Git更改&#x200B;**上设置为**&#x200B;的管道现在会自动启动。

请参阅[在 Cloud Manager 中添加外部存储库](/help/managing-code/external-repositories.md)。

![添加“存储库”对话框](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>目前，开箱即用的提取请求代码质量检查仅限于 GitHub 托管的存储库，但正在计划将此功能扩展到其他 Git 供应商的更新。

如果您有兴趣测试此新功能并分享您的反馈，请从与您的 Adobe ID 关联的电子邮件地址发送电子邮件至 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)。请务必注明您想要使用的 Git 平台以及您是处于专用/公共还是企业存储库结构中。


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
