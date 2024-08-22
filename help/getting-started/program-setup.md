---
title: 项目设置
description: 完成新用户引导后，业务负责人必须对项目进行一些初始设置。
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 49%

---


# 项目设置 {#program-setup}

完成新用户引导后，业务负责人通过添加描述并定义关键绩效指标(KPI)来设置项目。 然后使用这些KPI进行性能测试。

## 使用[!UICONTROL Cloud Manager]设置项目 {#program-setup-cloud-manager}

执行以下步骤可设置项目和定义 KPI。

1. 在 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 中登录 Cloud Manager 并选择适当的组织。

1. 单击&#x200B;**设置项目**&#x200B;以开始设置过程。

   ![设置项目](/help/assets/set-up-program/setup1.png)

1. 在&#x200B;**设置程序**&#x200B;对话框中，您可以在三个选项卡中输入程序信息：

   * **常规**
   * **KPI**
   * **配置**

1. 在&#x200B;**常规**&#x200B;选项卡上，添加项目描述，并（可选）通过单击&#x200B;**更改图片**&#x200B;来上传缩略图。

   ![“常规”选项卡](/help/assets/Setup_Program-General.png)

1. 在 **KPI** 选项卡上，定义 KPI。在此示例中，为 **AEM Sites** 和 **AEM Assets** 定义了单独的 KPI。为已许可的产品指定KPI。

   有关如何在 Cloud Manager 中测量 KPI 的更多详细信息，请参阅 [KPI](#kpis) 部分。

   ![定义 KPI](/help/assets/Setup_Program-KPIs.png)

1. 在&#x200B;**配置**&#x200B;选项卡上，可以为环境定义按需缩放选项（如果为项目启用了自动缩放）。

   自动缩放仅适用于生产环境，并且可能不适用于所有客户项目。

   ![配置选项](/help/assets/Setup_Program-Provisioning.png)

1. 单击&#x200B;**保存**。

您的项目已创建。 可能需要几分钟的时间来配置资源，之后项目才可供使用。

## 编辑项目 {#editing-program}

在设置项目后，可以编辑项目。执行以下步骤来编辑项目。

1. 在 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 中登录 Cloud Manager 并选择适当的组织。

1. 从 Cloud Manager 主屏幕导航到项目。

1. 单击&#x200B;**编辑程序**&#x200B;以从&#x200B;**概述**&#x200B;页面更新或修改您的程序。

   ![“编辑项目”选项](/help/assets/set-up-program/edit-program1.png)

1. 这将显示&#x200B;**编辑项目**&#x200B;对话框，在其中可以更新项目。有关可用字段的详细信息，请参阅[使用 Cloud Manager 设置项目](#program-setup-cloud-manager)部分。

   ![“编辑项目”对话框](/help/assets/set-up-program/edit-program-general.png)

1. 单击&#x200B;**更新**&#x200B;以保存更改。

更改将立即保存到Cloud Manager中，但在下一次管道运行之前不会反映在您的环境中。

如果尚未创建管道，请参阅[配置生产管道](/help/using/production-pipelines.md)和[配置非生产管道](/help/using/non-production-pipelines.md)。

## 在程序之间切换 {#swithing-programs}

在使用一个项目时，可以快速切换到另一个项目，而无需返回 Cloud Manager 概述页面。

使用操作栏切换到另一个项目、编辑当前项目或添加新项目。

![项目切换器](/help/assets/set-up-program/setup2.png)

## KPI {#kpis}

站点KPI是根据在暂存环境中运行的测试来测量的。 通常，这些 KPI 将缩小以适应暂存环境的功能。

例如，一个用户期望其生产环境中的每分钟平均页面查看次数达到1000次，其生产环境中有四个Dispatcher/发布服务器，则应该将此方案的每分钟页面查看次数扩展到250次。 此方案假定其暂存环境仅包含一个Dispatcher/发布服务器对。

Assets性能测试包括在30分钟的时间段内重复上传资源。 在整个测试中会测量每个资产的处理时间以及各种系统级量度。

您的生产环境前面可能有一个内容交付网络 (CDN)，例如 Akamai 或 CloudFront。由于[!UICONTROL Cloud Manager]直接针对暂存环境进行测试，因此KPI应仅反映预期将通过CDN的流量。 也就是说，缓存未命中。 通常，此体验只是总生产流量的一个相对较小的部分。

## 视频概述 {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
