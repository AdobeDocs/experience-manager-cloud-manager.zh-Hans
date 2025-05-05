---
title: 添加非生产管道
description: 了解如何使用 Cloud Manager 创建和配置非生产管道以部署代码。
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 1209faf71edbd74cd87acfe24ec438b98ddd4a3a
workflow-type: ht
source-wordcount: '688'
ht-degree: 100%

---

# 添加非生产管道 {#configuring-non-production-pipelines}

了解如何使用 Cloud Manager 创建和配置非生产管道以部署代码。 如果您首先想了解有关管道在 Cloud Manager 中的工作方式的更具有概念化的概述，请参阅 [CI/CD 管道](/help/overview/ci-cd-pipelines.md)。

## 概述 {#overview}

通过使用 [!UICONTROL Cloud Manager] 中的&#x200B;**管道**&#x200B;图块，**部署管理员**&#x200B;可以创建两种不同类型的管道。

* **生产管道** – 生产管道是一个专用管道，它包含一系列精心设计的步骤，可执行这些步骤以将源代码用于生产环境。
* **非生产管道** – 非生产管道主要用于运行代码质量扫描或将源代码部署到开发环境中。

本文档侧重于非生产管道。有关如何配置生产管道的详细信息，请参阅[配置生产管道](/help/using/production-pipelines.md)文档。

有两种类型的非生产管道：

* **代码质量管道** – 这些代码质量管道会扫描 Git 分支中的代码并执行构建和代码质量步骤。
* **部署管道** – 除了执行代码质量管道等构建和代码质量步骤之外，这些管道还将代码部署到非生产环境。

>[!NOTE]
>
>在管道的关联 Git 存储库具有至少一个分支且[项目设置](/help/getting-started/program-setup.md)完成之前，无法设置管道。请参阅 [Cloud Manager 存储库](/help/managing-code/managing-repositories.md)，了解如何在 Cloud Manager 中添加和管理存储库。

## 添加新的非生产管道 {#add-non-production-pipeline}

在设置项目并具有至少一个使用 Cloud Manager UI 的环境后，便可以执行以下步骤来添加非生产管道。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 中登录 Cloud Manager 并选择适当的组织和项目。

1. 从 Cloud Manager 主屏幕访问管道信息卡。单击&#x200B;**添加**，然后选择&#x200B;**添加非生产管道**。

   ![添加非生产管道](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. 在&#x200B;**添加非生产管道**&#x200B;对话框的&#x200B;**配置**&#x200B;选项卡上，选择要创建的管道类型，即&#x200B;**代码质量管道**&#x200B;或&#x200B;**部署管道**。

   ![选择管道类型](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. 在&#x200B;**非生产管道名称**&#x200B;字段中提供管道描述。

1. 如果您已选择添加&#x200B;**部署管道**，请从&#x200B;**符合条件的部署环境**&#x200B;下拉列表中选择目标部署环境。

1. 提供管道应从中检索代码的存储库。

   * **存储库**：定义管道应从中检索代码的 Git 存储库。
   * **Git 分支** – 定义所选管道应从 Git 中的哪个分支检索代码。

1. 定义部署选项。

   1. 在&#x200B;**部署触发器**&#x200B;下，定义将激活管道的事件。

      * **手动** - 您可以手动启动管道。
      * **在 Git 发生更改时** – 只要将承诺添加到配置的 Git 分支就会启动管道。 利用此选项，您仍能根据需要手动启动管道。

   1. 对于部署管道，在&#x200B;**重要量度失败行为**&#x200B;下，定义在任何质量审核出现重要失败时的管道行为。

      * **每次询问** – 默认设置，需要对任何重要失败进行手动干预。
      * **立即失败** – 每当发生重要失败时，管道都会被取消。 它实际上是在模拟用户手动拒绝每个失败。
      * **立即继续** – 每当发生重要失败时，管道都会自动运行。 它实际上是在模拟用户手动批准每个失败。

   1. **Dispatcher 配置** - **部署管理员**&#x200B;角色可以配置一组内容路径，这些路径会在管道运行时失效或从 AEM Dispatcher 缓存中刷新。 在部署任何内容包之后，便会作为部署管道步骤的一部分执行这些缓存操作。 这些设置使用标准的 AEM Dispatcher 行为。 要进行配置，请执行以下操作：

      1. 在&#x200B;**路径**&#x200B;下，提供内容路径。
      1. 在&#x200B;**类型**&#x200B;下，选择要对路径执行的操作。

         * **刷新** - 执行缓存删除。
         * **使无效** - 执行缓存无效，与将内容从创作实例激活到发布实例时类似。

      1. 单击&#x200B;**添加路径**&#x200B;以添加指定路径。可以为每个环境添加最多 100 个路径。

1. 单击&#x200B;**保存**。

## 后续步骤 {#the-next-steps}

配置管道后，您可以部署代码。 请参阅 [代码部署](/help/using/code-deployment.md)以了解更多详细信息。

## 视频教程 {#video-tutorial}

该视频概述了本文档中详述的管道创建过程。

>[!VIDEO](https://video.tv.adobe.com/v/327618?captions=chi_hans)
