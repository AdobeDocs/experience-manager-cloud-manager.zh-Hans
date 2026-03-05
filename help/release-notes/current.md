---
title: Cloud Manager 2026.3.0发行说明
description: 了解Adobe Managed Services上的Cloud Manager 2026.3.0版本。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 9ce8a2ca2117992421052b76b0f5c7c9c5a6195b
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 19%

---

# Adobe Managed Services上的Cloud Manager 2026.3.0发行说明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解Adobe Managed Services上的[!UICONTROL Cloud Manager] 2026.3.0版本。

另请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

[!UICONTROL Cloud Manager] 2026.3.0的发布日期是2026年3月5日星期四。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一个计划发布于2026年4月2日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#what-is-new}

* **在AEM Experience Hub中支持UI可扩展性**
[AEM Experience Hub](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/experience-hub/experience-hub)中对UI扩展的支持现已启用，从而让开发人员能够使用Adobe App Builder构建的自定义功能和构件来扩展界面。

  若要了解更多信息，请参阅[AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/)。

* **配置管道现在支持托管密钥**

  用户现在可以直接在Cloud Manager配置管道中添加和管理密钥。 这些密钥安全地覆盖管道配置规范中的值，并支持灵活、特定于环境的部署。

  ![查看/编辑所选管道下拉菜单上的变量选项](/help/release-notes/assets/view-edit-variables-option.png)
  *所选管道的下拉菜单上的“查看/编辑变量”选项。*

  ![变量配置对话框&#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*变量配置对话框。*

* **改进的稳定性、性能和可靠性**

  此版本包括优化和维护更新，这些更新改进了Cloud Manager的稳定性、性能和可靠性。


## Beta 计划 {#beta-program}

参与Cloud Manager的Beta计划，在即将发布的功能正式发布之前以独占方式访问这些功能。

目前提供以下机会：

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### 通过模块缓存加快构建速度 {#quick-build-cm-pipelines}

新的构建模型使用模块级缓存仅编译已更改的模块（而不是整个存储库）以缩短构建时间。 它适用于代码质量、全栈和仅限暂存的管道。

![编辑非生产管道对话框，其中显示两个生成策略选项，即“完全生成”和“智能生成”](/help/release-notes/assets/non-production-pipeline-edit.png)
*显示“完全生成”和“智能生成”这两个生成策略选项的“编辑非生产管道”对话框。*

在&#x200B;**添加/编辑管道**&#x200B;对话框的&#x200B;**Source代码**&#x200B;选项卡下，新增的&#x200B;**生成策略**&#x200B;部分允许您选择以下生成选项之一：

* **完整内部版本** — 每次运行都会在存储库中生成所有模块。
* **智能生成** — 仅生成自上次提交以来更改的模块，这会缩短总体生成时间。

您控制哪些管道使用&#x200B;**智能生成**。 在Beta测试期间，此选项仅对&#x200B;**代码质量**&#x200B;和&#x200B;**开发部署**&#x200B;管道显示。

是否有兴趣？ 向 [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) 发送电子邮件，其中包含您的 Adobe OrgID 和项目群 ID。

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## 错误修复 {#bug-fixes}

2026年3月的AMS版本Cloud Manager中没有重大错误修复。

<!--
Known Issues {#known-issues}

* A -->
