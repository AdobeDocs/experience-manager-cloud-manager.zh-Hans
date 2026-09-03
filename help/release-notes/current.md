---
title: Cloud Manager 2026.9.0发行说明
description: 了解Adobe Managed Services中的Cloud Manager 2026.9.0版本。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: e10c3c15c01c28f6bad0a9cf0464288937402cb7
workflow-type: tm+mt
source-wordcount: 403
ht-degree: 8%

---


# Adobe Managed Services中的Cloud Manager 2026.9.0发行说明 {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解Adobe Managed Services中的[!UICONTROL Cloud Manager] 2026.9.0版本。

另请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

[!UICONTROL Cloud Manager] 2026.9.0的发布日期是2026年9月3日星期四。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一个计划发布于2026年10月1日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#what-is-new}

2026年9月的AMS版本Cloud Manager中没有重大的新功能。


## Beta 计划 {#beta-program}

要在即将发布的功能正式发布之前获得独家访问权，请参与Cloud Manager的测试版计划。

>[!IMPORTANT]
>
>Beta版本存在缺陷，不提供任何形式的担保。 Adobe没有义务维护、更正、更新、更改、修改或以其他方式支持（通过Adobe支持服务或其他方式）Beta版。 客户使用测试版需自行承担风险。 请勿依赖测试版版本的正确功能或性能，或者依赖任何随附的文档或材料。 Beta版中的功能和API如有更改，恕不另行通知。 任何使用测试版的风险完全由客户自行承担。

目前提供以下测试版计划机会：

### AEM Managed Services的Web层管道 {#web-tier-pipelines}

Cloud Manager现在支持AMS程序的专用Web层管道，允许团队独立于全栈部署部署Dispatcher和Web层配置。 这样可以在Web层更改上加快迭代，同时减少不必要的完整管道执行。 配置Web层管道后，全栈管道会自动跳过该环境的Web层部署，以防止部署冲突。 删除Web层管道会自动恢复默认部署行为。

要加入Beta，请联系您的Adobe客户成功工程师以了解更多信息。


## 错误修复 {#bug-fixes}

* 现在，重新生成存储库访问密码将使旧密码无效。 以前，重新生成Git存储库访问密码不会立即使以前的密码失效，从而使旧凭据可用。 现在，重新生成密码会立即使旧密码失效，从而确保无法再使用以前的凭据。 (CMGR-41820)

* 更新了权限检查以强制实施资源所有权。 解决了如何评估权限检查，以便始终根据拥有项目的组织验证项目访问权限的问题。 这加强了组织之间对权限封闭操作的隔离。 (CMGR-79156)

<!--
Known Issues {#known-issues}
-->
