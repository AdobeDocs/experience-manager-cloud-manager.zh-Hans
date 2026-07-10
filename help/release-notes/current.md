---
title: Cloud Manager 2026.7.0发行说明
description: 了解Adobe Managed Services中的Cloud Manager 2026.7.0版本。
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
source-git-commit: 4c73ab16ff7eab406c31a6d26cdd09360a94b3ea
workflow-type: tm+mt
source-wordcount: 391
ht-degree: 14%

---


# Adobe Managed Services中的Cloud Manager 2026.7.0发行说明 {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解Adobe Managed Services中的[!UICONTROL Cloud Manager] 2026.6.0版本。

另请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

[!UICONTROL Cloud Manager] 2026.7.0的发布日期是2026年7月9日星期四。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一个计划发布于2026年8月6日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#what-is-new}

<!-- There are no significant new features in the June 2026 Cloud Manager on AMS release. -->

* **通过模块缓存提高了生成性能**
新的构建模型使用模块级缓存提高构建性能，只编译已更改的模块（而不是整个存储库）。 适用于生产管道。 您控制哪些生产管道使用&#x200B;**智能生成**。

  有关更多信息，请参阅以下内容：

   * [关于在生产管道中使用Smart Build](/help/using/production-pipelines.md#about-smart-build)和[关于在非生产管道中使用Smart Build](/help/using/non-production-pipelines.md#about-smart-build)
   * [添加生产管道](/help/using/production-pipelines.md##adding-production-pipeline)和[添加非生产管道](/help/using/non-production-pipelines.md#add-non-production-pipeline)。

## Beta 计划 {#beta-program}

参与 Cloud Manager 的 beta 计划，在即将推出的功能正式发布之前获得独家访问权限。

>[!IMPORTANT]
>
>Beta版本存在缺陷，并“按原样”提供，无任何形式的担保。 Adobe没有义务维护、更正、更新、更改、修改或以其他方式支持（通过Adobe支持服务或其他方式）Beta版。 客户自行承担使用测试版的风险，不应依赖于测试版的正确功能或性能，也不应依赖于任何随附的文档或材料。 Beta版中的功能和API如有更改，恕不另行通知。 任何使用测试版的风险完全由客户自行承担。

目前提供以下测试版计划机会：

### AEM Managed Services的Web层管道 {#web-tier-pipelines}

Cloud Manager现在支持AMS程序的专用Web层管道，允许团队独立于全栈部署部署Dispatcher和Web层配置。 这样可以在Web层更改上加快迭代，同时减少不必要的完整管道执行。 配置Web层管道后，全栈管道会自动跳过该环境的Web层部署，以防止部署冲突。 删除Web层管道会自动恢复默认部署行为。

要加入Beta，请联系您的Adobe客户成功工程师以了解更多信息。




## 错误修复 {#bug-fixes}

2026年6月的AMS版本Cloud Manager中没有重大错误修复。

<!--
Known Issues {#known-issues}

* A 
-->
