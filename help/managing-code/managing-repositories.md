---
title: 在 Cloud Manager 中管理存储库
description: 了解如何在 Cloud Manager 中查看、添加和删除 Git 存储库。
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 97%

---


# 在 Cloud Manager 中管理存储库 {#cloud-manager-repos}

了解如何在 Cloud Manager 中查看、添加和删除 Git 存储库。

## 概述 {#overview}

Cloud Manager 中的存储库用于使用 Git 存储和管理项目代码。对于您添加的每个 *程序*，都会自动创建一个 Adobe 管理的存储库。

此外，您可以选择创建更多 Adobe 管理的存储库，也可以添加您自己的专用存储库。所有关联到您的程序的存储库都可以在 **存储库** 页面上查看。

添加或编辑管道时也可以选择在 Cloud Manager 中创建的存储库。有关配置管道的更多信息，请参阅 [CI-CD 管道](/help/overview/ci-cd-pipelines.md)。

每个管道都关联到一个主存储库或分支。但是，借助 [Git 子模块支持](/help/managing-code/git-submodules.md)，可以在构建过程中包含多个二级分支。

## 查看存储库页面 {#repositories-window}

在 **存储库** 页面上，您可以查看有关所选存储库的详细信息。此信息包括正在使用的存储库的类型。如果存储库标记为 **Adobe**，则表示它是 Adobe 管理的存储库。如果标记为 **GitHub**，则指的是您管理的专用 GitHub 存储库。此外，该页面还提供详细信息，例如存储库的创建时间以及与其关联的管道。

要对选定的存储库执行操作，您可以单击该存储库并使用 ![更多图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) 打开下拉菜单。对于 Adobe 管理的存储库，您可以&#x200B;**[检查分支/创建项目](#check-branches)**。

![存储库操作](assets/repository-actions.png)
*存储库页面上的下拉菜单。*

下拉菜单上的其他可用操作包括 **[复制存储库 URL](#copy-url)**、**[查看和更新](#view-update)**&#x200B;以及 **[删除](#delete)** 存储库。

**查看存储库页面：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 在 **程序概述** 页面的侧面菜单中，单击 ![文件夹图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **存储库**。

1. **存储库**&#x200B;页面显示与您所选项目群相关的所有存储库。

   ![存储库页面](assets/repositories.png)
   *Cloud Manager 中的存储库页面。*


## 添加一个存储库 {#adding-repositories}

用户必须具有&#x200B;**部署经理**&#x200B;或&#x200B;**业务负责人**&#x200B;角色才能添加存储库。

在 **存储库** 页面的右上角附近，点击 **添加存储库**

![添加“存储库”对话框。](assets/repository-add.png)
*添加“存储库”对话框。*

Cloud Manager 支持两种类型的存储库：Adobe 管理的存储库（**Adobe 存储库**）和自己管理的存储库（**专用存储库**）。设置所需的字段根据您选择添加的存储库类型而有所不同。有关更多信息，请参阅以下内容：

* [在 Cloud Manager 中添加 Adobe 存储库](/help/managing-code/adobe-repositories.md)
* [在 Cloud Manager 中添加专用存储库](/help/managing-code/private-repositories.md)

在任何给定公司或 IMS 组织的所有项目中，存储库的数量限制为 300 个。

## 访问存储库信息 {#repo-info}

在&#x200B;**存储库**&#x200B;窗口中查看您的存储库时，您可以通过单击工具栏中的&#x200B;**访问存储库信息**&#x200B;按钮，查看有关如何以编程方式访问 Adobe 管理的存储库的详细信息。

![存储库信息](assets/repository-access-repo-info2.png)

**存储库信息**&#x200B;窗口将打开并显示详细信息。有关访问存储库信息的更多信息，请参阅[访问存储库信息](/help/managing-code/accessing-repositories.md)。

## 检查分支 / 创建项目 {#check-branches}

在&#x200B;**AEM Cloud Manager**&#x200B;中，**检查分支/创建项目**&#x200B;有两个用途，具体取决于存储库的当前状态。

* 如果存储库是新创建的，此操作将使用 [AEM 项目原型](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-core-components/using/developing/archetype/overview)生成示例项目。
* 如果示例项目已在存储库中创建，则该操作将检查存储库及其分支的状态，并提供示例项目是否已存在的反馈。


  ![检查分支机构操作](assets/check-branches.png)

## 复制存储库 URL {#copy-url}

**复制存储库 URL**&#x200B;操作会将&#x200B;**存储库**&#x200B;页面中选定存储库的 URL 复制到剪贴板以便在其他地方使用。

## 查看和更新存储库 {#view-update}

**查看和更新** 操作将打开 **更新存储库** 对话框，您可以在其中查看存储库的 **名称** 和 **存储库 URL 预览**。此外，它还允许您更新存储库的 **描述**。

![查看和更新存储库信息](assets/repository-view-update.png)

## 删除存储库 {#delete}

**删除**&#x200B;操作会从您的项目中删除存储库。如果存储库与管道关联，则无法删除它。

![删除一个存储库](assets/delete.png)

当在 Cloud Manager 中删除存储库时，它会被标记为已删除；用户无法再访问它。但是，为了实现恢复目的，它会在系统中保留。

如果您在删除同名存储库后尝试创建新的存储库，则会收到以下错误消息：

`An error has occurred while trying to create repository. Contact your CSE or Adobe Support.`

如果您收到此错误消息，请联系 Adobe 支持。他们可以帮助您重命名已删除的存储库或为新存储库选择不同的名称。
