---
title: 在Cloud Manager中管理存储库
description: 了解如何在Cloud Manager中创建、查看和编辑Git存储库。
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 73add7bee892769d1b3864e3238aff26bf96162d
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 25%

---


# Cloud Manager 存储库 {#cloud-manager-repos}

了解如何在Cloud Manager中创建、查看和编辑Git存储库。

## 概述 {#overview}

存储库用于通过Git存储和管理项目的代码。 您在Cloud Manager中创建的每个程序都有一个为其创建的Adobe管理的存储库。

您可以选择创建其他Adobe管理存储库，也可以添加您自己的专用存储库。 可以在以下位置查看与您的项目关联的所有存储库： **存储库** 窗口。

在 Cloud Manager 中创建的存储库也可供您在添加或编辑管道时选择。 请参阅 [CI-CD 管道](/help/overview/ci-cd-pipelines.md)，以了解更多信息。

任何给定的管道都有一个主存储库或分支。 替换为 [git子模块支持，](git-submodules.md) 可以在构建时包括许多二级分支。

## 存储库窗口 {#repositories-window}

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 从 **项目概述** 页面上，选择 **存储库** 制表符以切换到 **存储库** 页面。

1. 此 **存储库** 窗口显示与您的项目关联的所有存储库。

   ![存储库窗口](assets/repositories.png)

此 **存储库** 窗口提供了有关存储库的详细信息：

* 存储库的类型
   * **Adobe** 指示Adobe管理的存储库
   * **GitHub** 指示您管理的专用GitHub存储库
* 创建时间
* 与存储库关联的管道

您可以在窗口中选择存储库，然后单击省略号按钮以对所选存储库执行操作。

* **[检查分支/创建项目](#check-branches)** (仅适用于Adobe存储库)
* **[复制存储库URL](#copy-url)**
* **[查看和更新](#view-update)**
* **[删除](#delete)**

![存储库操作](assets/repository-actions.png)

## 添加存储库 {#adding-repositories}

点按或单击 **添加存储库** 中的按钮 **存储库** 窗口启动 **添加存储库** 向导。

![添加存储库向导](assets/add-repository-wizard.png)

Cloud Manager支持由Adobe(**Adobe存储库**)以及您自己的自管理存储库(**专用存储库**)。 根据您选择添加的存储库类型，必填字段会有所不同。 有关更多详细信息，请参阅以下文档。

* [在Cloud Manager中添加Adobe存储库](adobe-repositories.md)
* [在Cloud Manager中添加专用存储库](private-repositories.md)

>[!NOTE]
>
>* 用户必须具有&#x200B;**部署管理员**&#x200B;或&#x200B;**业务负责人**&#x200B;角色才能添加存储库。
>* 在任何给定公司或 IMS 组织的所有项目中，存储库的数量限制为 300 个。

## 访问存储库信息 {#repo-info}

在中查看存储库时 **存储库** Adobe窗口中，您可以通过点按或单击 **访问存储库信息** 工具栏中的按钮。

![存储库信息](assets/access-repo-info.png)

此 **存储库信息** 此时将打开一个窗口，其中包含详细信息。 有关访问存储库信息的更多信息，请参阅文档 [访问存储库信息。](accessing-repositories.md)

## 检查分支 {#check-branches}

此 **检查分支/创建项目** 操作根据存储库的状态执行两个功能。

* 如果存储库是新创建的，则该操作会根据以下内容创建一个示例项目 [AEM项目原型。](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/overview)
* 如果存储库已创建示例项目，则会检查存储库及其分支的状态，如果示例项目已存在，则会返回报告。

![检查分支操作](assets/check-branches.png)

## 复制存储库 URL {#copy-url}

此 **复制存储库URL** 操作将复制在所选存储库的URL **存储库** 窗口到剪贴板以在其他位置使用。

## 查看和更新 {#view-update}

此 **查看和更新** 操作打开 **更新存储库** 对话框。 利用它，您可以查看 **名称** 和 **存储库URL预览** 以及更新 **描述** 存储库的。

![查看和更新存储库信息](assets/update-repository.png)

## 删除 {#delete}

此 **删除** 操作从您的项目中删除存储库。 无法删除与管道关联的存储库。

![删除](assets/delete.png)

请注意，在 Cloud Manager 中删除某个存储库时，将它标为已删除，用户无法再访问它，但在系统中保留它以供恢复。

如果您尝试在删除同名存储库后创建新存储库，您将收到错误消息 `An error has occurred while trying to create repository. Please contact your CSE or Adobe Support.`

如果显示此错误消息，请联系 Adobe 支持人员，以使其可协助重命名被删除的存储库或为新存储库选择其他名称。
