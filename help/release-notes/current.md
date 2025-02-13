---
title: Cloud Manager 2025.2.0 版的发行说明
description: 了解 Adobe Managed Services 上有关 Cloud Manager 2025.2.0 版本的信息。
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 9d9bf7d689c0ace41bce3f31febe8ba78636c01f
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 88%

---

# Adobe Managed Services 上 Cloud Manager 2025.2.0 版的发行说明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

了解 Adobe Managed Services 上有关 [!UICONTROL Cloud Manager] 2025.2.0 版本的信息。

另请参阅[当前的Adobe Experience Manager as a Cloud Service发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

*Cloud Manager 2月版本没有显着错误或功能。*

[!UICONTROL Cloud Manager] 2025.2.0的发布日期是2025年2月13日星期四。

下一个计划发布于2025年3月13日星期四。

## 新增功能 {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* 从 2025 年 2 月 13 日星期四开始，Cloud Manager 代码质量步骤现在使用升级的 SonarQube 版本 9.9.5.90363。

  更新后的规则可通过[此链接](/help/using/code-quality-testing.md#code-quality-testing-step)获取，适用于 AMS，可确定 Cloud Manager 管道的安全分数和代码质量。此更新可能会影响您的质量关卡，甚至可能阻碍部署。

## 早期采用计划 {#early-adoption}

加入 Cloud Manager 早期采用计划，即有机会测试即将推出的功能。

### 自带 Git - 现支持 GitLab 和 Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**自带 Git** 功能已得到扩展，包括对 GitLab 和 Bitbucket 等外部存储库的支持。这项新的支持是对专用和企业 GitHub 存储库现有支持的补充。添加这些新的存储库时，您还可以将它们直接链接到管道。您可以在公共云平台、专用云平台或基础架构中托管这些存储库。这种集成还消除了与 Adobe 存储库持续同步代码的需要，并提供了在提取请求合并到主分支之前对其进行验证的功能。

使用外部存储库（不包括 GitHub 托管的存储库）和&#x200B;**部署触发器**&#x200B;设置为&#x200B;**在 Git 发生更改时**&#x200B;的管道现在会自动启动。

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
