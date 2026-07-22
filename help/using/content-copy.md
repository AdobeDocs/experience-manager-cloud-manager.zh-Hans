---
title: 内容复制以实现环境一致性
description: Cloud Manager 中的内容复制允许用户按需将可变内容从 Adobe Managed Services 托管的 Adobe Experience Manager 6.x 生产环境复制到较低的环境进行测试。
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
TQID: https://experienceleague.adobe.com/ffcf9UNSOp7oIpDZdtLcoFWp-Ww-A1XV3kCDmKqJLSw
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 845c182685d59844a2349c90d176d3e7c8a594cf
workflow-type: tm+mt
source-wordcount: 1435
ht-degree: 84%

---

# 内容复制以实现环境一致性 {#content-copy}

Cloud Manager 中的内容复制允许用户按需将可变内容从 Adobe Managed Services 托管的 Adobe Experience Manager 6.x 生产环境复制到较低的环境进行测试。

## 关于内容复制 {#introduction}

当前的真实数据对于测试、验证和用户验收很有价值。 通过内容复制，可将内容从 AMS 托管的 AEM 6.x 生产环境复制到暂存或开发环境。 该工作流程支持各种测试场景。

要复制的内容由内容集定义。 内容集包括要复制的可变内容的 JCR 路径列表。 内容会从源环境移动到目标环境。 此操作在同一Cloud Manager程序中执行。

内容集中允许使用以下路径：

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

复制内容时，源环境是主要引用。

如果您在目标环境中编辑内容，则在路径匹配的情况下源内容会覆盖它。

如果路径不同，源中的内容会与目标中的内容进行合并。

### 权限 {#permissions}

为了使用内容复制功能，用户必须分配有源和目标环境中的&#x200B;**部署管理员**&#x200B;角色。

## 创建内容集 {#create-content-set}

在可以复制任何内容之前，必须定义一个内容集。 内容集在定义之后可以重复使用来复制内容。

**要创建内容集：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 在页面左上角，单击![显示菜单图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)打开左侧菜单。

1. 从左侧菜单的&#x200B;**服务**&#x200B;下，单击![框图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **内容集**。

1. 在页面的右上角附近，单击&#x200B;**添加内容集**。

   ![内容集](/help/assets/content-sets.png)

1. 在&#x200B;**`Add Content Set`**&#x200B;对话框&#x200B;**详细信息**&#x200B;选项卡的&#x200B;**名称**&#x200B;和&#x200B;**描述**&#x200B;字段中，键入内容集的名称和可选描述，然后单击&#x200B;**继续**。

   ![内容集详细信息](/help/assets/add-content-set-details.png)

1. 在&#x200B;**内容路径**&#x200B;选项卡的&#x200B;**路径**&#x200B;文本字段中，指定可更改且应包含在内容集中的内容路径。

   只有以 `/content`、`/conf`、`/etc`、`/var/workflow/models` 或 `/var/commerce` 开头的路径才有资格纳入。

1. 单击![文件夹添加图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg)**添加路径**&#x200B;以添加（或包含）内容集的路径。

1. （可选）如有必要，请重复前两个步骤以添加其他路径（最多50个）。 否则，继续下一步。

   ![添加路径到内容集](/help/assets/add-content-set-paths.png)

1. （可选）要优化内容集，您可以选择在应排除的已包含内容路径中指定子路径。

   1. 在要排除的已包含内容路径的右侧，单击![文件夹删除图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg)。
   1. 在文本字段中，键入对话框中显示的根路径的相对路径。
   1. 单击![文件夹删除图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **排除路径**。
   1. 重复步骤i、ii和iii以添加更多排除的路径；没有限制。 否则，继续下一步。

   ![排除路径](/help/assets/add-content-set-paths-excluded.png)

1. （可选）执行下列任一操作：

   1. 单击排除子路径右侧的![十字大小 500 图标](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg)即可将其删除。
   1. 单击所包含内容路径右侧的![更多图标](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然后单击&#x200B;**编辑**&#x200B;或&#x200B;**删除**。

   ![编辑路径列表](/help/assets/add-content-set-excluded-paths.png)

1. 单击&#x200B;**创建**。 您现在可以使用内容集在环境之间复制内容。

## 编辑或删除内容集 {#edit-content-set}

要显示排除的子路径，请展开配置的路径。

**要编辑或删除内容集：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 在页面左上角，单击![显示菜单图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)打开左侧菜单。

1. 从左侧菜单中的&#x200B;**服务**&#x200B;下，单击![盒子图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **内容集**。

1. 在&#x200B;**内容集**&#x200B;页面的表中，单击所含内容路径右侧的![更多图标](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然后单击&#x200B;**编辑**&#x200B;或&#x200B;**删除**。

![编辑内容集](/help/assets/edit-content-set.png)

## 复制内容 {#copy-content}

创建内容集后，您可以使用它来复制内容。

如果满足以下任一条件，则环境可能无法进行选择：

* 用户缺少所需的权限。
* 当前环境中正在运行管道或内容复制操作。

**要复制内容：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 在页面左上角，单击![显示菜单图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)打开左侧菜单。

1. 从左侧菜单中的&#x200B;**服务**&#x200B;下，单击![盒子图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **内容集**。

1. 在&#x200B;**内容集**&#x200B;页面的表中，您想要复制的包含内容路径的右侧，单击![更多图标](https://spectrum.adobe.com/static/icons/ui_18/More.svg)，然后单击&#x200B;**复制内容**。

   ![内容复制](/help/assets/copy-content.png)

1. 在&#x200B;**复制内容**&#x200B;对话框中，选择内容复制操作的&#x200B;**源**&#x200B;环境和&#x200B;**目标**&#x200B;环境。

   * 目标环境中的区域必须是源环境中区域的子集。
   * 在运行内容复制操作之前检查兼容性问题。 当您选择&#x200B;**目标**&#x200B;环境时，系统会自动验证源环境和目标环境。 如果验证失败，则过程停止，并在对话框中显示一条错误消息，解释失败的原因。

     ![复制内容](/help/assets/copying-content.png)

1. （可选）执行下列任一操作：

   1. 要&#x200B;*保留*&#x200B;目标环境中排除的路径，请选中&#x200B;**`Do not delete excluded paths from destination`**。 此设置可保持内容集中指定的排除路径不变。
   1. 要&#x200B;*移除*&#x200B;目标环境中排除的路径，请取消选中&#x200B;**`Do not delete excluded paths from destination`**。 此设置会删除内容集中指定的排除路径。
   1. 要将路径的版本历史记录从源环境复制到目标环境，请选中&#x200B;**复制版本**。 当&#x200B;*不*&#x200B;复制版本历史记录时，内容复制过程会大大加快。

1. 单击&#x200B;**复制**。 复制过程的状态将反映在所选内容集的控制台中。

## 检查内容复制的状态 {#copy-activity}

您可以在&#x200B;**复制内容活动**&#x200B;页面中监控复制过程的状态。

**要检查内容复制的状态：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 在页面左上角，单击![显示菜单图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)打开左侧菜单。

1. 从左侧菜单的&#x200B;**服务**&#x200B;下，单击![历史记录图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg)**复制内容活动**。

   ![内容复制活动](/help/assets/copy-content-activity.png)

   内容复制过程可以具有以下状态之一：

   | 状态 | 描述 |
   | --- | --- |
   | 进行中 | 内容复制过程正在进行中。 |
   | 已完成 | 内容复制过程成功完成。 |
   | 失败 | 内容复制过程失败。 |

## 内容复制的局限性 {#limitations}

* 无法从较低环境向较高环境执行内容复制。
* 内容复制只能在同一层级内进行。 具体而言，这意味着作者到作者或发布到发布。
* 无法跨项目和跨区域复制内容。
* 仅当源和目标环境位于同一云提供商和同一区域时，才能对基于云数据存储的拓扑执行内容复制。
* 在同一环境中运行并发的内容复制操作是不可能的。
* 如果在目标或源环境（例如 CI/CD 管道）上正在运行任何活动操作，则无法执行内容复制。
* 内容复制不应用作克隆或镜像工具，因为它无法跟踪源上移动或删除的内容。
* 内容复制一旦开始即无法暂停或取消。
* 内容复制将资产和 Dynamic Media 元数据从较高的环境复制到所选的较低环境。 然后，需要在较低环境中使用[DAM流程资源工作流](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/assets/using/assets-workflow)重新处理复制的资源。 要使用相应的Dynamic Media配置，需要重新处理。
* 不支持启用了资源大小大于2 GB的[Dynamic Media配置](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb)。
* 目标环境的区域必须与源环境的区域相同或为其子集。

## 内容复制的已知问题 {#known-issues}

{{content-copy-known-issues}}
