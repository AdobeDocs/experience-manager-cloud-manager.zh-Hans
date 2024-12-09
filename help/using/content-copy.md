---
title: 内容拷贝以实现环境一致性
description: 通过Cloud Manager中的内容复制，用户可按需将可变内容从AdobeManaged Services托管的Adobe Experience Manager 6.x生产环境复制到较低级别的环境以进行测试。
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 228006b424504306e916014bbe8543dc41ba43b5
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 33%

---


# 内容拷贝以实现环境一致性 {#content-copy}

通过Cloud Manager中的内容复制，用户可按需将可变内容从AdobeManaged Services托管的Adobe Experience Manager 6.x生产环境复制到较低级别的环境以进行测试。

## 关于内容复制 {#introduction}

当前的真实数据对于测试、验证和用户验收很有价值。内容复制允许您将内容从AMS托管的生产AEM 6.x环境复制到暂存或开发环境。 该工作流程支持各种测试场景。

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

若要使用内容复制功能，必须将用户分配到源环境和目标环境中的&#x200B;**部署管理员**&#x200B;角色。

## 创建内容集 {#create-content-set}

在可以复制任何内容之前，必须定义一个内容集。内容集在定义之后可以重复使用来复制内容。请按照以下步骤操作来创建内容集。

**创建内容集：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 在页面的左上角，单击![显示菜单图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以打开左侧菜单。

1. 从左侧菜单的&#x200B;**服务**&#x200B;页面下，单击![框图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **内容集**。

1. 在页面的右上角附近，单击&#x200B;**添加内容集**。

   ![内容集](/help/assets/content-sets.png)

1. 在&#x200B;**`Add Content Set`**&#x200B;对话框的&#x200B;**详细信息**&#x200B;选项卡的&#x200B;**名称**&#x200B;和&#x200B;**描述**&#x200B;字段中，键入内容集的名称和可选描述，然后单击&#x200B;**继续**。

   ![内容集详细信息](/help/assets/add-content-set-details.png)

1. 在&#x200B;**内容路径**&#x200B;选项卡的&#x200B;**路径**&#x200B;文本字段中，指定可更改且应包含在内容集中的内容路径。

   只有以`/content`、`/conf`、`/etc`、`/var/workflow/models`或`/var/commerce`开头的路径才符合包含条件。

1. 单击&#x200B;**![文件夹添加图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg)添加路径**&#x200B;以添加（或包含）内容集的路径。

1. （可选）如有必要，请重复前两个步骤，根据需要添加添加路径（最多50个）。 否则，请继续执行下一步。

   ![添加路径到内容集](/help/assets/add-content-set-paths.png)

1. （可选）要缩小内容集的范围，您可以选择在所包含的内容路径中指定应排除的子路径。

   1. 在要限制的包含内容路径的右侧，单击![文件夹删除图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg)。
   1. 在文本字段中，键入对话框中显示的根路径的相对路径。
   1. 单击![文件夹删除图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **排除路径**。
   1. 如有必要，请重复步骤i.至iii。 添加更多排除路径；没有限制。 否则，请继续执行下一步。

   ![排除路径](/help/assets/add-content-set-paths-excluded.png)

1. （可选）执行以下任一操作：

   1. 单击已排除子路径右侧的![跨大小500图标](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg)以将其删除。
   1. 单击所包含内容路径右侧的![更多图标](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然后单击&#x200B;**编辑**&#x200B;或&#x200B;**删除**。

   ![编辑路径列表](/help/assets/add-content-set-excluded-paths.png)

1. 单击&#x200B;**创建**。您现在可以使用内容集在环境之间复制内容。

## 编辑或删除内容集 {#edit-content-set}

编辑内容集时，您可能需要展开配置的路径以显示排除的子路径。

**要编辑或删除内容集：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 在页面的左上角，单击![显示菜单图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以打开左侧菜单。

1. 从左侧菜单的&#x200B;**服务**&#x200B;下，单击![框图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **内容集**。

1. 在&#x200B;**内容集**&#x200B;页面上的表中，单击所包含内容路径右侧的![更多图标](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然后单击&#x200B;**编辑**&#x200B;或&#x200B;**删除**。

![编辑内容集](/help/assets/edit-content-set.png)


## 复制内容 {#copy-content}

创建内容集后，您可以使用该内容集复制内容。

如果满足以下任一条件，则环境可能无法进行选择：

* 用户缺少所需的权限。
* 当前环境中正在运行管道或内容复制操作。

**要复制内容：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 在页面的左上角，单击![显示菜单图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以打开左侧菜单。

1. 从左侧菜单的&#x200B;**服务**&#x200B;下，单击![框图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **内容集**。

1. 在&#x200B;**内容集**&#x200B;页面上的表格中，在要复制的包含的内容路径右侧，单击![更多图标](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然后单击&#x200B;**复制内容**。

   ![内容复制](/help/assets/copy-content.png)

1. 在&#x200B;**复制内容**&#x200B;对话框中，为您的内容复制操作选择&#x200B;**Source**&#x200B;环境和&#x200B;**目标**&#x200B;环境。

   * 目标环境中的区域必须是源环境中的区域子集。
   * 在运行内容复制操作之前会检查兼容性问题。 当您选择&#x200B;**目标**&#x200B;环境时，系统会自动验证源和目标环境。 如果验证失败，进程将停止，并在说明失败原因的对话框中显示错误消息。

     ![复制内容](/help/assets/copying-content.png)

1. （可选）执行以下任一操作：

   1. 要&#x200B;*保留*&#x200B;目标环境中排除的路径，请选中&#x200B;**`Do not delete exclude paths from destination`**。 此设置会保持内容集中指定的排除路径不变。
   1. 要&#x200B;*删除*&#x200B;目标环境中排除的路径，请取消选中&#x200B;**`Do not delete exclude paths from destination`**。 此设置将删除内容集中指定的排除路径。
   1. 若要将路径版本历史记录从源环境复制到目标环境，请选中&#x200B;**复制版本**。 当版本历史记录为&#x200B;*而非*&#x200B;时，内容复制过程要快得多。



1. 单击&#x200B;**复制**。 复制过程的状态将反映在所选内容集的控制台中。

## 监控内容复制状态 {#copy-activity}

您可以在&#x200B;**复制内容活动**&#x200B;页面中监控复制过程的状态。

**监视内容副本状态：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 在页面的左上角，单击![显示菜单图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)以打开左侧菜单。

1. 从左侧菜单的&#x200B;**服务**&#x200B;下，单击![历史记录图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg)**复制内容活动**。

   ![内容复制活动](/help/assets/copy-content-activity.png)

   内容复制进程可以具有以下状态之一：

   | 状态 | 描述 |
   | --- | --- |
   | 进行中 | 正在执行内容复制操作。 |
   | 已完成 | 内容复制操作已成功完成。 |
   | 失败 | 内容复制操作失败。 |


## 内容副本的限制 {#limitations}

* 无法从较低环境向较高环境执行内容复制。
* 内容复制只能在同一层级内进行。 也就是说，作者对作者，或者发布对发布。
* 无法跨项目和跨区域复制内容。
* 只有当源环境和目标环境在同一云提供商和同一区域上时，才能为基于云数据存储的拓扑执行内容复制。
* 在同一环境中运行并发的内容复制操作是不可能的。
* 如果在目标或源环境（例如 CI/CD 管道）上正在运行任何活动操作，则无法执行内容复制。
* 内容复制不应用作克隆或镜像工具，因为它不能跟踪源上已移动或删除的内容。
* 内容复制一旦开始即无法暂停或取消。
* 内容复制将资源和Dynamic Media元数据从较高的环境复制到选定的较低环境。 然后，需要在较低的环境中使用 [DAM 处理资源工作流程](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/assets/using/assets-workflow)重新处理复制的资源，以使用相应的 Dynamic Media 配置。
* [已启用资产大小大于 2 GB 的 Dynamic Media 配置](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb)不受支持。
* 目标环境的区域必须与源环境的区域相同或为其子集。

## 已知问题 {#known-issues}

{{content-copy-known-issues}}
