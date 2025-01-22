---
title: Cloud Manager 2025.1.0 版的发行说明
description: 了解 Adobe Managed Services 上有关 Cloud Manager 2025.1.0 版本的信息。
feature: Release Information
source-git-commit: c25508b24f00b8f8cfa7bae3cc4b0d6ecf684db3
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 32%

---

# Adobe Managed Services 上 Cloud Manager 2025.1.0 版的发行说明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

了解 Adobe Managed Services 上有关 [!UICONTROL Cloud Manager] 2025.1.0 版本的信息。

>[!NOTE]
>
>请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2025.1.0的发布日期是2024年1月22日星期三。

下一个计划发布于2025年2月13日星期四。

## 新增功能 {#what-is-new}

**代码质量规则：** Cloud Manager代码质量步骤将开始将SonarQube Server 9.9与Cloud Manager 2025.2.0版本一起使用，该版本计划于2025年2月13日星期四发布。

为了准备，更新的SonarQube规则现在可在[代码质量规则](/help/using/code-quality-testing.md#code-quality-testing-step)中获取。

您可以通过设置以下管道文本变量（请参阅下面的屏幕快照），“提前检查”新规则：

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

此外，设置以下变量以确保为同一提交运行代码质量步骤（通常为同一`commitId`跳过）：

`CM_DISABLE_BUILD_REUSE` = `true`

![变量配置页面](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe建议创建一个新的CI/CD代码质量管道，并将其配置为与主生产管道位于同一分支。 在&#x200B;*2025年2月13日版本之前*&#x200B;设置适当的变量，以验证新的强制执行规则不会引入阻止程序。

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
