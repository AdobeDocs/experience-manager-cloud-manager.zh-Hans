---
title: Cloud Manager 2026.1.0 版的发行说明
description: 了解 Adobe Managed Services 上有关 Cloud Manager 2026.1.0 版本的信息。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 28841719e820e47577b411a4034ebc7a8e1bb556
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 48%

---

# Adobe Managed Services 上 Cloud Manager 2026.1.0 版的发行说明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解 Adobe Managed Services 上有关 [!UICONTROL Cloud Manager] 2026.1.0 版本的信息。

另请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

[!UICONTROL Cloud Manager] 2026.1.0的发布日期是2026年1月22日星期四。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一个计划发布于2026年2月5日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#what-is-new}

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

### Experience Hub 可扩展性和自定义 {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/experience-hub/experience-hub) 是您进入 AEM 的入口点，可根据组织需求进行自定义。请告知 Adobe 您现有的 AEM UI 扩展，以便他们协助您在 Experience Hub 中轻松启用这些功能。

![Experience Hub 可扩展性和自定义工作流程示意图](/help/release-notes/assets/experience-hub-extensibility-customization.png)

在 Experience Hub 中嵌入自定义体验，扩展和个性化组织的仪表板。除了 Adobe 的内置构件之外，还可以使用 [UI 可扩展性](https://developer.adobe.com/uix/docs/)框架添加您自己的构件。构建基于 JavaScript 的 UI 应用程序，并将其呈现给您的用户，以满足特定业务需求和工作流程。

是否对 Beta 感兴趣？向 [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) 发送电子邮件，其中包含您的 Adobe OrgID 以及要创建自定义设置的简短说明。

### 通过模块缓存加快构建速度 {#quick-build-cm-pipelines}

新的构建模型使用模块级缓存仅编译已更改的模块（而不是整个存储库）以缩短构建时间。它适用于代码质量、全栈和仅限暂存的管道。

![编辑非生产管道对话框，其中显示两个生成策略选项，即“完全生成”和“智能生成”](/help/release-notes/assets/non-production-pipeline-edit.png)
*显示“完全生成”和“智能生成”这两个生成策略选项的“编辑非生产管道”对话框。*

在&#x200B;**添加/编辑管道**&#x200B;对话框的&#x200B;**Source代码**&#x200B;选项卡下，新增的&#x200B;**生成策略**&#x200B;部分允许您选择以下生成选项之一：

* **完整内部版本** — 每次运行都会在存储库中生成所有模块。
* **智能生成** — 仅生成自上次提交以来更改的模块，这会缩短总体生成时间。

您控制哪些管道使用&#x200B;**智能生成**。 在Beta测试期间，此选项仅对&#x200B;**代码质量**&#x200B;和&#x200B;**开发部署**&#x200B;管道显示。

是否有兴趣？向 [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) 发送电子邮件，其中包含您的 Adobe OrgID 和项目群 ID。

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## 错误修复 {#bug-fixes}

2026年1月的Cloud Manager AMS版本没有重大错误修复。

<!--
Known Issues {#known-issues}

* A -->
