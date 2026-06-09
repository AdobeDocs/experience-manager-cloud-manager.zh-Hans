---
title: 添加生产管道
description: 了解如何使用 Cloud Manager 创建和配置生产管道以部署代码。
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
TQID: https://experienceleague.adobe.com/WH6W8bZNCWo0BAGLwnMOPpB3bk5P6Fd7c5b-dRT5Vc0
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: badb64b816e83ca08a39b2b39eda13335f6a3c1d
workflow-type: tm+mt
source-wordcount: 1665
ht-degree: 73%

---

# 添加生产管道 {#configuring-production-pipelines}

了解如何使用 Cloud Manager 创建和配置生产管道以部署代码。 如果您首先想了解有关管道在 Cloud Manager 中的工作方式的更具有概念化的概述，请参阅 [CI/CD 管道](/help/overview/ci-cd-pipelines.md)。

## 概述 {#overview}

通过使用 **Cloud Manager] 中的**&#x200B;管道设置[!UICONTROL 图块，您可以创建两种不同类型的管道。

* **生产管道** - 生产管道是一个专用管道，它包含一系列精心设计的步骤，可执行这些步骤以将 Git 存储库中的源代码用于生产环境。
* **非生产管道** - 非生产管道主要用于运行代码质量扫描或将源代码部署到开发环境中。

本文档侧重于生产管道。 有关如何配置非生产管道的详细信息，请参阅[配置非生产管道](/help/using/non-production-pipelines.md)文档。

**部署管理员**&#x200B;角色负责设置管道。 管道配置包含：

1. 定义会启动管道的触发器。
1. 定义用于控制生产部署的参数。
1. 配置性能测试参数。

>[!NOTE]
>
>在管道的关联 Git 存储库具有至少一个分支且[项目设置](/help/getting-started/program-setup.md)完成之前，无法设置管道。

## 添加新的生产管道 {#adding-production-pipeline}

在使用 [!UICONTROL Cloud Manager] UI 设置项目并具有至少一个环境后，便可以添加生产管道。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 从&#x200B;**项目概述**&#x200B;页面导航到&#x200B;**管道**&#x200B;信息卡。

1. 单击 **+ 添加**，然后选择&#x200B;**添加生产管道**。

   ![添加生产管道](/help/assets/configure-pipelines/add-prod7.png)

1. 这将打开&#x200B;**添加生产管道**&#x200B;对话框，您必须在其中的&#x200B;**配置**&#x200B;选项卡上为管道定义大量选项。 这些选项将分组到多个可折叠的部分中，并且会在以下步骤中进行描述。

   1. 在&#x200B;**管道名称**&#x200B;字段中提供管道的描述性名称。

   1. 在&#x200B;**环境**&#x200B;部分下，您可以定义触发部署的内容以及应如何在每个环境中推出部署。

      1. 在&#x200B;**暂存**&#x200B;部分中，您可以定义管道部署到暂存环境的方式。

         * **部署触发器** - 您可以使用以下选项来定义部署触发器以启动管道。

            * **手动** - 使用 Cloud Manager UI 手动启动管道。
            * **在 Git 发生更改时** – 只要将承诺添加到配置的 Git 分支时就会启动 CI/CD 管道。 利用此选项，您仍能根据需要手动启动管道。

         * **重要量度失败行为** - 在管道设置或编辑期间，部署管理员可以选择定义在任何质量审核出现重要失败时的管道行为。 可用的选项为：

            * **每次询问** – 默认设置，需要对任何重要失败进行手动干预。
            * **立即失败** – 每当发生重要失败时，管道都会被取消。 它是在模拟用户手动拒绝每个失败。
            * **立即继续** – 每当发生重要失败时，管道都会自动运行。 它是在模拟用户手动批准每个失败。

         ![部署触发器](/help/assets/configure-pipelines/add-prod3.png)

         * **部署选项** - 您可以加快执行某些部署任务。

            * **暂存部署后审批** - 此审批在部署到暂存环境后且执行任何测试前进行。 否则，在生产部署之前进行审批，这将在所有测试完成后执行。

            * **跳过负载平衡器更改** - 不进行负载平衡器更改。

         ![暂存部署选项](/help/assets/configure-pipelines/add-prod4.png)

         * **Dispatcher 配置** - **部署管理员**&#x200B;角色可以配置一组内容路径，这些路径会在管道运行时失效或从 AEM Dispatcher 缓存中刷新。 在部署任何内容包之后，便会作为部署管道步骤的一部分执行这些缓存操作。 这些设置使用标准的 AEM Dispatcher 行为。 若要进行配置，请进行以下操作：

            1. 在&#x200B;**路径**&#x200B;下，提供内容路径。
            1. 在&#x200B;**类型**&#x200B;下，选择要对路径执行的操作。

               * **刷新** - 执行缓存删除。
               * **使无效** - 执行缓存无效，与将内容从创作实例激活到发布实例时类似。

            1. 单击&#x200B;**添加路径**&#x200B;以添加指定路径。 可以为每个环境添加最多 100 个路径。

         ![Dispatcher 配置](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >通常，最好是使用失效操作，但在某些情况下可能需要进行刷新，特别是在使用 AEM HTML 客户端库时。

      1. 在&#x200B;**生产**&#x200B;部分中，您可以定义管道部署到生产环境的方式。

         * **部署选项** - 您可以定义用于控制生产部署的参数。

            * **使用上线审批** – 部署必须由具有&#x200B;**业务负责人**、**项目管理员**&#x200B;或&#x200B;**部署管理员**&#x200B;角色的用户通过 [!UICONTROL Cloud Manager] UI 来手动审批。
            * **已计划** - 在生产部署前暂停管道以允许对其进行安排。 如果选择此选项，管道会在部署到暂存环境后停止，并提示用户要执行的操作。
               * **`Now`** - 立即部署到生产环境，从而有效地完成管道。
               * **日期** - 允许用户计划应完成部署的时间。
               * **停止执行** - 中止部署到生产环境。

           >[!TIP]
           >
           >请参阅[代码部署](/help/using/code-deployment.md)，了解如何设置部署计划或立即执行管道。

            * **使用 CSE 监督** - 如果选择此选项，则通过 CSE（客户成功工程师）启动实际部署。 在启用此选项的情况下创建或编辑管道时，**部署管理员**&#x200B;角色具有以下选项。

               * **任何 CSE** - 允许任何可用的 CSE 启动部署。
               * **我的 CSE** - 仅允许分配给客户的特定 CSE 启动部署。 如果分配的 CSE 不可用，该选项也将适用于指定的 CSE 后备人员。

           ![生产部署选项](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Dispatcher 配置** - 为您的生产环境定义 Dispatcher 配置。 这些选项与暂存环境的选项相同。

1. 单击&#x200B;**继续**&#x200B;进入&#x200B;**Source代码**&#x200B;选项卡，在该选项卡中选择要部署和配置源存储库的代码类型。

   1. 在&#x200B;**选择要部署的代码**&#x200B;下，选择部署类型：

      * **[全栈代码](#full-stack-code)** — 完整AEM应用程序的代码。
      * **[Web层配置](#web-tier-config)** — 用于存储、处理网页并将网页交付给客户端的Dispatcher属性。

      有关这些部署类型的详细信息，请参阅[CI/CD管道](/help/overview/ci-cd-pipelines.md#code-sources)。 完成管道配置的剩余步骤取决于您选择的类型。 按照上面的链接跳到本文档的相关部分。

1. 单击&#x200B;**继续**&#x200B;以进入&#x200B;**暂存测试**&#x200B;选项卡，可以在其中根据已许可的产品来配置 AEM Sites 和 AEM Assets 性能测试。 {#stage-testing}

   >[!TIP]
   >
   >请参阅[代码质量测试](/help/using/code-quality-testing.md#performance-testing)了解有关&#x200B;**阶段测试**&#x200B;选项卡上可用的选项的更多详细信息。

   1. 在 **站点内容传递/分布式负载权重**&#x200B;部分中，您可以根据三个页面集之间的页面请求权重来配置网站性能测试。 您可以根据需要启用或禁用页面集。

      * **受欢迎实时页面**
      * **其他实时页面**
      * **新页面**

      ![网站负载权重](/help/assets/configure-pipelines/add-prod8.png)

   1. 在 **Assets 性能测试分发**&#x200B;部分中，您可以定义图像和 PDF 的测试分发，并定义您自己的测试资产。

      * **图像** - 调整滑块可调整图像和 PDF 之间的测试拆分。
      * **PDF** - 调整滑块可调整图像和 PDF 之间的测试拆分。

      * 通过上传您自己的自定义资产来定义它们。

         1. **格式** - 选择您的自定义资产是否为 PDF 格式的图像。
         1. **文件名** - 使用文件浏览器按钮从本地计算机中选择图像。
         1. **添加测试文件** - 单击以上传您选择的资产。

      ![Assets 测试分发](/help/assets/configure-pipelines/add-prod6.png)

1. 单击&#x200B;**保存**&#x200B;以完成生产管道添加操作。

### 全栈代码 {#full-stack-code}

全栈代码管道部署后端和前端代码构建以及HTTPD/Dispatcher配置。

>[!NOTE]
>
>如果全栈生产管道已存在，则禁用此选择。

**要配置全栈栈代码生产管道：**

1. 在&#x200B;**Source代码**&#x200B;选项卡上，定义以下选项。

   * **存储库** - 定义管道应从中检索代码的 Git 存储库。

   >[!TIP]
   >
   >请参阅[项目设置](/help/getting-started/program-setup.md)文档，了解如何在 Cloud Manager 中添加和管理存储库。

   * **Git分支** — 定义管道应从中检索代码的分支。
   * **忽略 Web 层配置** – 勾选后，该管道不会部署您的 Web 层配置。 如果同一环境已存在某个Web层配置管道，则该复选框将自动选中并禁用，因为Web层配置由该管道管理。 当不存在Web层配置管道时，您可以选择或清除此选项以控制全栈管道是否部署Dispatcher配置。

   ![全栈代码源](/help/assets/configure-pipelines/add-prod-fullstack-source.png)

1. 单击&#x200B;**继续**&#x200B;进入&#x200B;**阶段测试**&#x200B;选项卡。 有关详细信息，请参阅[暂存测试](#stage-testing)。

### Web 层配置 {#web-tier-config}

Web层配置管道仅部署HTTPD/Dispatcher配置。 有关此管道类型的更多详细信息，请参阅[CI/CD管道](/help/overview/ci-cd-pipelines.md#deployment-types)。

>[!NOTE]
>
>如果Web层配置生产管道已存在，则禁用此选择。

如果您为具有现有全栈管道的环境创建Web层配置管道，则忽略全栈管道中的Web层配置。 此更改仅影响该环境中的Web层配置。

**要配置Web层配置生产管道：**

1. 在&#x200B;**Source代码**&#x200B;选项卡上，定义以下选项。

   * **存储库** — 从下拉列表中选择包含Web层配置的Git存储库。
   * **Git分支** — 选择Cloud Manager用于部署的所选存储库中的分支。
   * **代码位置** — 在包含要部署的Web层配置的选定存储库中输入路径。 默认位置是存储库根(`/`)。

   >[!NOTE]
   >
   >如果代码位置未指向Dispatcher代码位置，则可能会将其他应用程序代码拉入工件包并部署到Dispatcher，从而导致Apache在重新启动时失败以及管道失败。 确保为存储库中的Dispatcher文件设置正确的路径。

   ![Web层配置源](/help/assets/configure-pipelines/add-prod-webtier-source.png)

1. 单击&#x200B;**继续**&#x200B;进入&#x200B;**阶段测试**&#x200B;选项卡。 有关详细信息，请参阅[暂存测试](#stage-testing)。

## 后续步骤 {#the-next-steps}

配置管道后，部署代码。 请参阅 [代码部署](/help/using/code-deployment.md)以了解更多详细信息。

## 视频教程 {#video-tutorial-one}

该视频概述了本文档中详述的管道创建过程。

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
