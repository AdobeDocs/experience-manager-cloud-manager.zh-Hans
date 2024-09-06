---
title: 内容复制工具
description: 通过 Cloud Manager 内容复制工具，用户可按需将可变内容从 AMS 托管的 AEM 6.x 生产环境复制到较低版本的环境以供测试。
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '1144'
ht-degree: 100%

---


# 内容复制工具 {#content-copy}

通过 Cloud Manager 内容复制工具，用户可按需将可变内容从 AMS 托管的 AEM 6.x 生产环境复制到较低版本的环境以供测试。

## 简介 {#introduction}

当前的真实数据对于测试、验证和用户验收很有价值。通过内容复制工具，可将内容从 AMS 托管的 AEM 6.x 生产环境复制到暂存或开发环境。该工作流程支持各种测试场景。

要复制的内容由内容集定义。 内容集包括要复制的可变内容的 JCR 路径列表。 内容会从源环境移动到目标环境。 所有操作均会在同一个 Cloud Manager 程序中完成。

内容集中允许使用以下路径：

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

复制内容时，源环境是真实的来源。

* 如果您在目标环境中编辑内容，则在路径匹配的情况下源内容会覆盖它。
* 如果路径不同，源中的内容会与目标中的内容进行合并。

## 权限 {#permissions}

为了使用内容复制工具，用户必须分配有源和目标环境中的&#x200B;**部署经理**&#x200B;角色。

## 创建内容集 {#create-content-set}

在可以复制任何内容之前，必须定义一个内容集。内容集在定义之后可以重复使用来复制内容。请按照以下步骤操作来创建内容集。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 从&#x200B;**概述**&#x200B;页面，导航到&#x200B;**环境**&#x200B;屏幕。

1. 从&#x200B;**环境**&#x200B;屏幕导航到&#x200B;**内容集**&#x200B;页面。

1. 在屏幕右上角附近，单击&#x200B;**添加内容集**。

   ![内容集](/help/assets/content-sets.png)

1. 在向导的&#x200B;**详细信息**&#x200B;选项卡上，为内容集提供名称和描述，然后单击&#x200B;**继续**。

   ![内容集详细信息](/help/assets/add-content-set-details.png)

1. 在向导的&#x200B;**内容路径**&#x200B;选项卡上，指定要包含在内容集中的可变内容的路径。

   1. 在&#x200B;**添加包含路径**&#x200B;字段中输入路径。
   1. 单击&#x200B;**添加路径**&#x200B;按钮将路径添加到内容集中。
   1. 根据需要，单击&#x200B;**添加路径**&#x200B;按钮。

   ![添加路径到内容集](/help/assets/add-content-set-paths.png)

1. 如果您需要优化或限制您的内容集，可以排除子路径。

   1. 在包含的路径列表中，单击您需要限制的路径旁边的&#x200B;**添加排除子路径**&#x200B;图标。
   1. 输入要从选定路径中排除的子路径。
   1. 点击 **排除路径**。
   1. 根据需要，再次单击&#x200B;**添加排除子路径**&#x200B;以添加要排除的其他路径。

   ![排除路径](/help/assets/add-content-set-paths-excluded.png)

1. 如果需要，您可以修改指定的路径。

   1. 单击排除的子路径旁边的 `X` 以将其删除。
   1. 单击路径旁边的省略号按钮以显示&#x200B;**编辑**&#x200B;和&#x200B;**删除**&#x200B;选项。

   ![编辑路径列表](/help/assets/add-content-set-excluded-paths.png)

1. 单击&#x200B;**创建**&#x200B;以创建内容集。

内容集现在可用于在环境之间复制内容。

>[!NOTE]
>
>您最多可以在一个内容集中添加 50 个路径。
>排除的路径没有限制。

## 编辑内容集 {#edit-content-set}

遵循与创建内容步骤时类似的步骤。不要单击&#x200B;**添加内容集**，而是从控制台选择一个现有集，然后从省略号菜单中选择&#x200B;**编辑**。

![编辑内容集](/help/assets/edit-content-set.png)

编辑内容集时，您可能需要展开配置的路径以显示排除的子路径。

## 复制内容 {#copy-content}

创建内容集后，您可以使用它来复制内容。按照以下步骤操作来复制内容。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 从&#x200B;**概述**&#x200B;页面，导航到&#x200B;**环境**&#x200B;屏幕。

1. 从&#x200B;**环境**&#x200B;屏幕导航到&#x200B;**内容集**&#x200B;页面。

1. 从控制台选择一个内容集，然后从省略号菜单中选择&#x200B;**复制内容**。

   ![内容复制](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >在以下情况下可能无法选择环境：
   >
   >* 用户没有适当的权限。
   >* 环境中有正在运行的管道或正在进行的复制内容操作。

1. 在&#x200B;**复制内容**&#x200B;对话框中，指定内容复制操作的源和目标环境。
   * 目标环境的区域必须与源环境的区域相同或为其子集。

1. 可选择在目标环境中删除或保留排除路径。选中复选框 `Do not delete exclude paths from destination` 以保留内容集中指定的 `exclude paths`。 如果未选中复选框，则会在目标环境中删除排除路径。

1. 可选择复制从源环境复制到目标环境的路径的版本历史记录。 如果要复制所有的版本历史记录，请选中复选框`Copy Versions`。

   ![复制内容](/help/assets/copying-content.png)

1. 点击 **复制**。

复制过程开始。复制过程的状态将反映在所选内容集的控制台中。

## 内容复制活动 {#copy-activity}

您可以在&#x200B;**复制内容活动**&#x200B;页面中监控复制过程的状态。

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager，然后选择相应的组织和项目。

1. 从&#x200B;**概述**&#x200B;页面，导航到&#x200B;**环境**&#x200B;屏幕。

1. 从&#x200B;**环境**&#x200B;屏幕导航到&#x200B;**复制内容活动**&#x200B;页面。

![内容复制活动](/help/assets/copy-content-activity.png)

### 内容复制状态 {#statuses}

开始复制内容后，复制过程可能具有以下状态之一。

| 状态 | 描述 |
|---|---|
| 进行中 | 内容复制操作正在进行中 |
| 失败 | 内容复制操作失败 |
| 已完成 | 内容复制操作成功完成 |

## 限制 {#limitations}

内容复制工具具有以下限制。

* 无法从较低环境向较高环境执行内容复制。
* 内容复制只能在同一层级内进行。 也就是说，作者对作者，或者发布对发布。
* 无法跨项目和跨区域复制内容。
* 只有当源环境和目标环境在同一云提供商和同一区域上时，才能为基于云数据存储的拓扑执行内容复制。
* 在同一环境中运行并发的内容复制操作是不可能的。
* 如果在目标或源环境（例如 CI/CD 管道）上正在运行任何活动操作，则无法执行内容复制。
* 每个内容集最多可以指定五十条路径。排除的路径没有限制。
* 内容复制工具不应用作克隆或镜像工具，因为它无法跟踪源上移动或删除的内容。
* 内容复制一旦开始即无法暂停或取消。
* 内容复制工具将资源和 Dynamic Media 元数据从较高的环境复制到所选的较低环境。 然后，需要在较低的环境中使用 [DAM 处理资源工作流程](https://experienceleague.adobe.com/zh-hans/docs/ experience-manager-65/content/assets/using/assets-workflow)重新处理复制的资源，以使用相应的 Dynamic Media 配置。
* 当不复制版本历史记录时，内容复制过程会大大加快。
* [已启用资产大小大于 2 GB 的 Dynamic Media 配置](https://experienceleague.adobe.com/zh-hans/docs/ experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb)不受支持。
* 当不复制版本历史记录时，内容复制过程会大大加快。
* 目标环境的区域必须与源环境的区域相同或为其子集。

## 已知问题 {#known-issues}

{{content-copy-known-issues}}
