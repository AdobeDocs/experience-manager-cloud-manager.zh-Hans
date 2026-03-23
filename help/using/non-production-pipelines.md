---
title: 添加非生产管道
description: 了解如何使用 Cloud Manager 创建和配置非生产管道以部署代码。
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: eaf3db69bd3cc0a06aafd1b415c5bdb467019c1b
workflow-type: tm+mt
source-wordcount: '1992'
ht-degree: 27%

---

# 添加非生产管道 {#configuring-non-production-pipelines}

了解如何使用 Cloud Manager 创建和配置非生产管道以部署代码。 如果您首先想了解有关管道在 Cloud Manager 中的工作方式的更具有概念化的概述，请参阅 [CI/CD 管道](/help/overview/ci-cd-pipelines.md)。

## 概述 {#overview}

通过使用 [!UICONTROL Cloud Manager] 中的&#x200B;**管道**&#x200B;图块，**部署管理员**&#x200B;可以创建两种不同类型的管道。

* **生产管道** – 生产管道是一个专用管道，它包含一系列精心设计的步骤，可执行这些步骤以将源代码用于生产环境。
* **非生产管道** – 非生产管道主要用于运行代码质量扫描或将源代码部署到开发环境中。

本文档侧重于非生产管道。 有关如何配置生产管道的详细信息，请参阅[配置生产管道](/help/using/production-pipelines.md)文档。

有两种类型的非生产管道：

* **代码质量管道** – 这些代码质量管道会扫描 Git 分支中的代码并执行构建和代码质量步骤。
* **部署管道** – 除了执行代码质量管道等构建和代码质量步骤之外，这些管道还将代码部署到非生产环境。

>[!NOTE]
>
>在管道的关联 Git 存储库具有至少一个分支且[项目设置](/help/getting-started/program-setup.md)完成之前，无法设置管道。 请参阅 [Cloud Manager 存储库](/help/managing-code/managing-repositories.md)，了解如何在 Cloud Manager 中添加和管理存储库。

## 添加新的非生产管道 {#add-non-production-pipeline}

在Cloud Manager UI中设置项目和至少一个环境后，您可以添加非生产管道。 在部署到生产环境之前，使用这些管道测试代码质量。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 中登录 Cloud Manager 并选择适当的组织和项目。

1. 从 Cloud Manager 主屏幕访问管道信息卡。 单击&#x200B;**添加**，然后选择&#x200B;**添加非生产管道**。

   ![添加非生产管道](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. 在&#x200B;**添加非生产管道**&#x200B;对话框的&#x200B;**配置**&#x200B;选项卡上，通过下列任一方式选择要创建的管道类型：

   * **代码质量管道** — 创建管道，在不部署到环境的情况下，生成代码、运行单元测试和评估代码质量。
   * **部署管道** — 创建用于生成代码、运行单元测试、评估代码质量并部署到环境的管道。

   ![选择管道类型](/help/using/assets/add-non-production-pipeline-cm-ams.png)

>[!BEGINTABS]

>[!TAB 代码质量管道 — 配置选项卡]

| 区域 | 选项 | 描述 |
| --- | --- | --- |
| **管道配置** | **非生产管道名称** | 在&#x200B;**非生产管道名称**&#x200B;字段中提供管道描述。 |
|  | **正在测试** | 仅在编辑非生产管道时可见。<br>UI显示管道作为代码质量验证的一部分运行的测试类别。<ul><li>**静态代码测试** — 分析代码的质量问题和正确性问题。<li>**负载/性能测试** — 在管道测试过程中评估与性能相关的行为。<li>**安全测试** — 检查代码和管道输出中的安全相关问题。 |
| **部署选项** | **部署触发器** | <ul><li>**手动** - 您可以手动启动管道。<li>**在 Git 发生更改时** – 只要将承诺添加到配置的 Git 分支就会启动管道。 利用此选项，您仍能根据需要手动启动管道。 |
|  | **重要量度失败行为** | <ul><li>**每次询问** – 此行为是默认设置，需要对任何重要失败进行手动干预。<li>**立即失败** — 如果选定此选项，则只要发生重要失败，就会取消管道。 它实际上模拟用户手动拒绝每个失败。<li>**立即继续** — 如果选定此选项，则每当发生重要失败时，管道就会自动继续。 它实际上模拟用户手动批准每个失败。</li></ul> |
|  | **阶段部署后审批**&#x200B;复选框 | 仅在编辑非生产管道时可见。<br>选择此选项要求在部署到暂存环境后审批，管道才能继续。 如果未选中此选项，则管道将根据配置的行为继续运行。 |

>[!TAB 部署管道 — 配置选项卡]

| 区域 | 选项 | 描述 |
| --- | --- | --- |
| **管道配置** | **非生产管道名称** | 在&#x200B;**非生产管道名称**&#x200B;字段中提供管道描述。 |
|   | **符合条件的部署环境** | 如果您的管道是部署管道，则必须选择Cloud Manager部署代码的环境。 |
|   | **正在测试** | 仅在编辑非生产管道时可见。<br>UI显示管道作为代码质量验证的一部分运行的测试类别。<ul><li>**静态代码测试** — 分析代码的质量问题和正确性问题。<li>**负载/性能测试** — 在管道测试过程中评估与性能相关的行为。<li>**安全测试** — 检查代码和管道输出中的安全相关问题。</li></ul> |
| **部署选项** | **部署触发器** | <ul><li>**手动** - 您可以手动启动管道。<li>**在 Git 发生更改时** – 只要将承诺添加到配置的 Git 分支就会启动管道。 利用此选项，您仍能根据需要手动启动管道。 |
|   | **重要量度失败行为** | <ul><li>**每次询问** — 默认设置并提示用户决定重要量度失败时如何继续。<li>**立即失败** — 只要重要量度失败，就会取消管道。 它实际上是在模拟用户手动拒绝每个失败。<li>**立即继续** — 每当重要量度失败时，管道会自动继续。 它实际上是在模拟用户手动批准每个失败。</li></ul> |
|  | **阶段部署后审批**&#x200B;复选框 | 仅在编辑非生产管道时可见。<br>选择此选项要求在部署到暂存环境后审批，管道才能继续。 如果未选中此选项，则管道将根据配置的行为继续运行。 |
|  | **跳过负载平衡器更改**&#x200B;复选框 | 选择此选项可防止管道在部署期间进行负载平衡器更改。 |
|  | **Dispatcher配置** | **部署管理员**&#x200B;角色可以配置一组内容路径，这些路径将在管道运行时失效或从AEM Dispatcher缓存中刷新。 在部署任何内容包之后，便会作为部署管道步骤的一部分执行这些缓存操作。 这些设置使用标准的 AEM Dispatcher 行为。 要配置`Dispatcher`，请执行以下操作：<ul><li>在&#x200B;**PATH**&#x200B;下，提供您希望管道刷新或失效的内容路径。<li>在&#x200B;**类型**&#x200B;下，选择要对路径执行的操作。<ul><li>**刷新** — 在指定的路径上执行缓存删除。</li><li>**使无效** - 执行缓存无效，与将内容从创作实例激活到发布实例时类似。</li><li>单击&#x200B;**添加路径**&#x200B;以添加指定路径。 可以为每个环境添加最多 100 个路径。</li></ul> |
| **管道** | **体验审核**&#x200B;复选框 | 选择此选项可在管道中包含体验审核步骤。 启用后，该管道会在“Source代码”选项卡之后包含“体验审核”步骤。 |

>[!ENDTABS]

1. 在&#x200B;**添加非生产管道**&#x200B;对话框的右下角，单击&#x200B;**继续**。
1. 选择管道配置为生成和部署的代码类型。

>[!BEGINTABS]

>[!TAB Source“代码”选项卡 — 全栈代码]

部署完整的AEM应用程序，包括应用程序代码和默认的Web层配置。

| 区域 | 选项 | 描述 |
| --- | --- | --- |
| **Source代码** | **存储库** | 从下拉列表中，选择管道用作其源的Git存储库。 Cloud Manager从您在此处选择的存储库中生成代码。 |
|   | **Git分支** | 从下拉列表中，选择管道应从中构建的所选存储库的分支。 默认为 `main`。 管道使用所选分支作为构建和部署的源。 如有必要，请单击&#x200B;**刷新**&#x200B;以更新所选存储库的可用分支列表。 如果最近创建的分支未出现在列表中，请使用此选项。 |
|   | **生成策略** | <ul><li>**完整生成** — 每次生成存储库中的所有模块<li>Beta **智能生成** — 仅生成自上次提交以来更改的模块。<br>了解有关[在非生产管道中使用智能生成的更多信息](#about-smart-build)。</li></ol>**重要信息**： Smart Build仅适用于代码质量管道和开发全栈代码部署管道。 |
|   | **忽略Web层配置**&#x200B;复选框 | 选择此选项可跳过全栈代码管道中Web层配置的部署。 保持未选中选项以部署Web层配置以及管道代码。 |
| **管道** | **体验审核**&#x200B;复选框 | 选择此选项可在管道中包含体验审核步骤。 启用后，该管道会在“Source代码”选项卡之后包含“体验审核”步骤。 |

>[!TAB Source代码 — Web层配置]

仅部署Web层配置，例如用于存储、处理网页并将网页交付给客户端的Dispatcher资产。 当您选择&#x200B;**Web层配置**&#x200B;时，Cloud Manager将创建一个专用于Web层配置部署的管道。

如果全栈管道已存在，Cloud Manager会显示一条通知，指出创建Web层配置管道会导致现有全栈管道忽略Web层配置。 在创建Web层配置管道后，Cloud Manager会通过该管道（而不是全栈管道）管理Web层配置部署。

| 区域 | 选项 | 描述 |
| --- | --- | --- |
| **Source代码** | **存储库** | 从下拉列表中，选择包含Web层配置的Git存储库。 |
|   | **Git分支** | 选择Cloud Manager用于部署的所选存储库中的分支。 如有必要，请单击&#x200B;**刷新**&#x200B;以更新所选存储库的可用分支列表。 如果最近创建的分支未出现在列表中，请使用此选项。 |
|   | **代码位置** | 在包含要部署的Web层配置的所选存储库中输入路径。 默认位置是存储库根(`/`)。 |

>[!ENDTABS]

1. 单击&#x200B;**保存**。

## 关于在非生产管道中使用Smart Build{#about-smart-build}

Cloud Manager中的&#x200B;**智能生成**&#x200B;是适用于非生产管道的优化生成策略。 Smart Build通过缓存模块并仅重新生成自上次成功运行以来发生更改的模块来缩短构建时间。 未更改的模块从缓存中重用，而只重新构建已修改的模块及其依赖关系，从而提高迭代开发工作流的效率。

Smart Build当前仅适用于以下项目：

* 代码质量管道。
* 开发全栈部署管道。

>[!NOTE]
>
>启用Smart Build后首次运行的行为类似于Full Build，因为缓存为空。

在出现以下情况时，建议使用Smart Build：
* 您正在积极开发和提交频繁的增量更改。
* 您的项目包含多个Maven模块。
* 完整内部版本需要大量时间。

当出现以下情况时，Smart Build并不总是理想的：
* 您的内部版本严重依赖在Maven的依赖关系图之外执行操作的插件。
* 每次执行都需要完全重新生成验证。

### 了解构建性能{#smart-build-performance}

使用Smart Build的性能提升取决于以下几个因素：

* 项目中的模块数。
* 代码更改的频率和范围。
* 依赖项在各个模块之间的分布。

通常，具有许多独立模块的项目通常会看到最大的改进。

### 每模块缓存选择退出{#smart-build-cache-optout}

Smart Build提供细粒度控制，允许您禁用特定模块的缓存。 此功能在以下情况下很有用：

* 使用插件，如`exec-maven-plugin`或`maven-antrun-plugin`。
* 执行Maven依赖项未跟踪的文件操作。
* 缓存时生成不一致的结果。

### 禁用模块的缓存{#smart-build-disable-caching}

您可以将以下属性添加到受影响模块的`pom.xml`：

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

此语法强制模块在每次管道执行时重新生成，而其他模块继续受益于缓存。

### 使用智能构建时的限制和注意事项{#smart-build-limitations}

使用Smart Build时，请牢记以下几点：

* Smart Build依赖于Maven依赖关系分析。
* 在依赖关系图之外进行的更改可能不会触发重新生成。
* 某些插件可能与缓存不完全兼容。
* 您可以通过编辑非生产管道随时切换回&#x200B;**完整内部版本**。

如果遇到意外的生成行为，请考虑禁用特定模块的缓存或暂时将生成策略切换到&#x200B;**完整生成**。

### 智能生成问题疑难解答{#smart-build-troubleshoot}

| 问题 | 建议的解决方案 |
| --- | --- |
| 生成结果不一致 | ·禁用受影响模块的缓存。<br>·验证插件行为（尤其是`exec`/`antrun`插件）。 |
| 无性能改进 | ·确保已多次运行（缓存预热）。<br>·检查大多数模块是否频繁更改。 |
| 意外的项目或缺少更改 | ·检查更改是否在Maven依赖项跟踪之外。<br>·使用&#x200B;**Full Build**&#x200B;进行验证。 |

请参阅[添加非生产管道](#add-non-production-pipeline)以启用智能生成。



<!-- 
1. If you chose to add a **Deployment Pipeline**, select the target deployment environment from the **Eligible Deployment Environments** dropdown.

1. Provide the repository where the pipeline should retrieve the code.

   * **Repository** - Defines from which Git repo that the pipeline should retrieve the code.
   * **Git Branch** - Defines from which branch in Git that the selected pipeline should retrieve the code.

1. Define your deployment options.

   1. Under **Deployment Trigger**, define what event activates the pipeline.

      * **Manual** - Lets you manually start the pipeline.
      * **On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required.

   1. For deployment pipelines, under **Important Metric Failures Behavior**, define the behavior of the pipeline when an important failure is encountered in any of the quality gates.

       * **Ask every time** - The default setting and requires manual intervention on any important failure.
       * **Fail Immediately** - The pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
       * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

   1. **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that are either invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:

      1. Under **PATH** provide a content path.
      1. Under **TYPE**, select the action to be taken on that path.

         * **Flush** - Perform a cache deletion.
         * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
         
      1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

1. Click **Save**.
-->

## 后续步骤 {#the-next-steps}

配置管道后，您可以部署代码。 请参阅 [代码部署](/help/using/code-deployment.md)以了解更多详细信息。

## 视频教程 {#video-tutorial}

该视频概述了本文档中详述的管道创建过程。

>[!VIDEO](https://video.tv.adobe.com/v/327618?captions=chi_hans)
