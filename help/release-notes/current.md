---
title: Cloud Manager 2025.10.0 版的发行说明
description: 了解 Adobe Managed Services 上有关 Cloud Manager 2025.10.0 版本的信息。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: e203ab018908ec0a47e8d472079843d5db05dce0
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 54%

---

# Adobe Managed Services 上 Cloud Manager 2025.10.0 版的发行说明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

了解 Adobe Managed Services 上有关 [!UICONTROL Cloud Manager] 2025.10.0 版本的信息。

另请参阅 [Adobe Experience Manager as a Cloud Service 的当前发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.10.0的发布日期是2025年10月2日星期四。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

下一个计划发布于2025年11月6日星期四。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新增功能 {#what-is-new}

10月发行的Cloud Manager没有重大的新增功能。


## Beta 计划 {#beta-program}

参与Cloud Manager的Beta计划，在即将发布的功能正式发布之前以独占方式访问这些功能。

目前提供以下机会：

### Experience Hub可扩展性和自定义 {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub)是您进入AEM的入口点，根据贵组织的需求进行自定义。 介绍Adobe中您现有的AEM UI扩展，以便它们可以帮助您在Experience Hub中轻松启用它们。

![Experience Hub可扩展性和自定义工作流程示意图](/help/release-notes/assets/experience-hub-extensibility-customization.png)

在Experience Hub中嵌入自定义体验，以扩展和个性化贵组织的仪表板。 除了Adobe的内置小组件之外，还可以使用[UI可扩展性](https://developer.adobe.com/uix/docs/)框架添加您自己的小组件。 构建基于JavaScript的UI应用程序，并将其呈现给您的用户，以满足特定于业务的要求和工作流。

对Beta版感兴趣吗？ 向[beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com)发送电子邮件，其中包含您的Adobe OrgID以及要创建的自定义设置的简短说明。

### 通过模块缓存加快构建速度 {#quick-build-cm-pipelines}

新的构建模型使用模块级缓存仅编译已更改的模块（而不是整个存储库）以缩短构建时间。 它适用于代码质量、全栈和仅限暂存的管道。

对Beta版感兴趣吗？ 使用您的Adobe OrgID和项目ID向[beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com)发送电子邮件。

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


### 使用您自己的 Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

客户现在可以将他们的 Azure DevOps Git 存储库加入到 Cloud Manager 中，同时支持现代 Azure DevOps 和旧版 VSTS（Visual Studio Team Services）两种存储库。

* Edge Delivery Services 用户可以使用已加入的存储库来同步和部署网站代码。
* 对于 AEM as a Cloud Service 和 Adobe Managed Services (AMS) 用户，该存储库可以链接到全栈和前端两种管道。

对其他管道类型以及通过代码质量管道进行提取请求验证的支持即将推出。

请参阅[在 Cloud Manager 中添加外部存储库](/help/managing-code/external-repositories.md)。

![添加“存储库”对话框](/help/release-notes/assets/azure-repo.png)

如果您有兴趣测试此新功能并分享您的反馈，请从与您的 Adobe ID 关联的电子邮件地址发送电子邮件至 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)。请务必注明您想要使用的 Git 平台以及您是处于专用/公共还是企业存储库结构中。

#### 管理访问令牌{#manage-access-tokens}

在 Cloud Manager 中使用&#x200B;**管理访问令牌**&#x200B;功能，可查看、重命名并删除与外部自带 Git 存储库（如 GitHub Enterprise、GitLab、Bitbucket 和 Azure DevOps）关联的访问令牌。

请参阅[管理访问令牌](/help/managing-code/manage-access-tokens.md)。

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## 错误修复 {#bug-fixes}

10月的Cloud Manager版本中没有重大的错误修复。

<!--
Known Issues {#known-issues}

* A -->
