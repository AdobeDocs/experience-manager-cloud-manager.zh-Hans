---
title: Cloud Manager 2026.11.0发行说明
description: 了解Adobe Managed Services中的Cloud Manager 2026.11.0版本。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: 'https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro'
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: b48085c8209c0802f6f2d321865bd1a1ee786139
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 8%
---

# Adobe Managed Services中的Cloud Manager 2026.11.0发行说明 {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解Adobe Managed Services中的[!UICONTROL Cloud Manager] 2026.11.0版本。

另请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

[!UICONTROL Cloud Manager] 2026.11.0的发布日期是2026年11月5日星期四。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一个计划发布于2026年12月3日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#new-features}

### AEM Managed Services的Web层管道 {#web-tier-pipelines}

Cloud Manager现在支持AMS程序的专用Web层管道，允许团队独立于全栈部署部署Dispatcher和Web层配置。 这样可以在Web层更改上加快迭代，同时减少不必要的完整管道执行。

配置Web层管道后，全栈管道会自动跳过该环境的Web层部署，以防止部署冲突。 删除Web层管道会自动恢复默认部署行为。<!-- CMGR-27553 -->

查看[Web层配置管道](/help/overview/ci-cd-pipelines.md#web-tier-config-pipelines)。

## Beta 计划 {#beta-program}

目前没有可用的测试版计划机会。

<!--
To get exclusive access to upcoming features before their general release, participate in Cloud Manager's beta programs.

>[!IMPORTANT]
>
>Beta releases contain issues and are provided without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify or otherwise support (through Adobe Support Services or otherwise) the beta releases. Customers use beta releases at their own risk. Do not rely on the correct functioning or performance of beta releases, or on any accompanying documentation or materials. Features and APIs in beta are subject to change without notice. Any use of the beta releases is entirely at the customer's own risk.

The following beta program opportunity is currently available:
-->

## 错误修复 {#bug-fixes}


* 代码质量扫描在大型项目上失败。 代码质量(SonarQube)扫描会生成多GB的调试日志，并在扫描某些捆绑的库时终止，从而导致生成失败。 已更正扫描，以便在受影响的项目中正常完成扫描。 (CMGR-80025)

* 网站使用CSV导出显示月份标签移动了一个月。 在许可证>站点使用详细信息页面上，CSV导出显示位于后UTC时区的用户一个月前移动的标签数。 现在，无论用户的时区如何，导出都会显示正确的月份标签。 (CMGR-80903)

* 重用访问令牌名称不再覆盖现有令牌。 在程序中重用现有的访问令牌名称会覆盖共享令牌并创建重复的访问密钥。 Cloud Manager现在可以正确处理令牌名称重用，防止意外覆盖和重复。 (CMGR-81236)


<!--
Known Issues {#known-issues}
-->
