---
title: 2024.4.0 的发行说明
description: 这些是 Cloud Manager 2024.4.0 版的发行说明。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 4a7c6fbc3fa936ff1470420966823f94fb3a4d7b
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 79%

---


# Cloud Manager 2024.4.0 版的发行说明 {#release-notes}

此页面记载 [!UICONTROL Cloud Manager] 2024.4.0 版的发行说明。

>[!NOTE]
>
>有关 AEM as a Cloud Service 中的 Cloud Manager 的最新发行说明，请参阅 [AEM as a Cloud Service 中的 Cloud Manager 的最新发行说明](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)。

## 发布日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.4.0 版的发布日期为 2024 年 4 月 10 日。下一个版本计划于 2024 年 5 月 9 日发布。

## 新增功能 {#what-is-new}

* 引入了对仅暂存管道和仅生产管道的支持，使您能够将全栈生产部署管道拆分为更小的专用部署。
* 增强了代码构建问题的错误消息，能够更轻松地识别根本原因以及后续可操作的步骤。

## 早期采用计划 {#early-adoption}

成为我们早期采用计划的一部分，并有机会测试一些即将推出的功能

### 自带 GitHub {#byo-github}

如果您使用 GitHub 管理存储库，则[现在可以通过 Cloud Manager 直接在 GitHub 存储库中验证代码。](/help/managing-code/byo-github.md)此集成使得无需始终与 Adobe 存储库同步代码，并使您可验证拉取请求后再将其合并到主分支中。此功能为公共 GitHub 所独有。不支持自托管 GitHub。

如果您有兴趣测试这项新功能并共享您的反馈，请从您的 Adobe ID 关联的电子邮件地址发送电子邮件至 `Grp-CloudManager_BYOG@adobe.com`。

## 错误修复 {#bug-fixes}

* 解决了Cloud Manager重用具有错误承诺哈希的工件的错误。
