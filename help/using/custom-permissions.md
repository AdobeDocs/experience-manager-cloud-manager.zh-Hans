---
title: 自定义权限
description: 了解如何使用自定义权限创建具有可配置权限的新的自定义权限配置文件，以限制 Cloud Manager 用户对项目、管道和环境的访问。
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 98%

---

# 自定义权限 {#custom-permissions}

了解如何使用自定义权限创建具有可配置权限的新的自定义权限配置文件，以限制 Cloud Manager 用户对项目、管道和环境的访问。

## 简介 {#introduction}

Cloud Manager 有一组预定义的角色，用于管理对 Cloud Manager 各种功能的访问权限：

* 业务负责人
* 项目管理员
* 部署管理员
* 开发人员

自定义权限允许用户创建具有可配置权限的新的自定义权限配置文件，以限制 Cloud Manager 用户对项目、管道和环境的访问。

>[!TIP]
>
>有关预定义角色的详细信息，请参阅文档[基于角色的权限](/help/requirements/role-based-permissions.md)。

## 使用自定义权限 {#using}

创建和使用您自己的自定义权限需要以下三个步骤：

1. [创建新的产品配置文件](#create)。
1. [向新产品配置文件分配自定义权限](#assign-permissions)。
1. [将用户分配给新产品配置文件](#assign-users)。

此部分详细介绍了这三个步骤。 在创建自己的自定义权限时，您可能会发现参阅[术语](#terms)和[可配置权限](#configurable-permissions)会有帮助。

>[!NOTE]
>
>您必须在 Admin Console 中拥有产品管理员权限，才能创建新的配置文件并管理 Cloud Manager 的权限。

### 创建新的产品配置文件 {#create}

首先创建一个新的产品配置文件，然后为其分配自定义权限。

1. 登录 Cloud Manager，网址为 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. 选择产品 **AEM Managed Services**。

1. 搜索名称与模式 `*-cloud-manager` 匹配的实例，并单击以管理用户和权限。

1. 您将重定向到 Admin Console 的&#x200B;**产品**&#x200B;选项卡，可在其中管理 Cloud Manager 的用户和权限。 在 Admin Console 中，单击&#x200B;**新配置文件**。

![“新配置文件”按钮](/help/assets/admin-console-new-profile.png)

1. 提供有关配置文件的一般详细信息。

   * **产品配置文件名称** - 配置文件的描述性名称
   * **显示名称** - 将在用户界面（选项）中显示的缩写名称
   * **描述** - 有关配置文件的信息性描述，用于说明其用途（可选）
   * **通过电子邮件通知用户** - 选择此项后，在此配置文件中添加或移除用户时，系统会通过电子邮件通知用户。

1. 单击&#x200B;**保存**。

新的产品配置文件已保存，并在 Admin Console 中的产品配置文件列表中可见。

### 向新产品配置文件分配自定义权限 {#assign-permissions}

现在，您已拥有新的产品配置文件，可以向其分配自定义权限。

1. 在 Admin Console 中，单击[刚创建的新产品配置文件](#create)的名称。

1. 在打开的窗口中，选择&#x200B;**权限**&#x200B;选项卡以查看可编辑权限的列表。

   ![可编辑权限](/help/assets/permissions-tab.png)

1. 单击权限的&#x200B;**编辑**&#x200B;链接以编辑权限。

1. 这将打开&#x200B;**“编辑权限”**&#x200B;窗口。
   * 您在上一步中选择的权限在左列中处于选定状态。
   * 可用于权限分配的权限项位于标记为&#x200B;**可用权限**&#x200B;项的中间列中。
   * 分配的权限项位于标记为&#x200B;**“包含的权限项”**&#x200B;的右列中。

   ![编辑权限项](/help/assets/edit-permission-items.png)

1. 单击权限项旁边的加号 (`+`) 图标，将其添加到&#x200B;**包含的权限项**&#x200B;的列中。 必要时，点按或单击权限项旁边的 `i` 图标，了解有关它的更多信息。

1. 在&#x200B;**可用权限**&#x200B;列顶部，点击&#x200B;**全部添加**&#x200B;可添加所有权限。 同样，单击&#x200B;**全部移除**，即可移除所有之前选择的权限。

1. 在定义完新产品配置文件的权限项后，单击&#x200B;**保存**。

新产品配置文件现已与其自定义权限一起保存。

### 将用户分配给新产品配置文件 {#assign-users}

您现在可以将用户分配给使用自定义权限创建的新产品配置文件。

1. 在 Admin Console 中，单击[刚为其分配自定义权限的新产品配置文件](#assign-permissions)的名称。

1. 在打开的窗口中，选择&#x200B;**用户**&#x200B;选项卡。

1. 点击&#x200B;**添加用户**，将用户分配到带自定义权限的新产品配置文件。

请参阅[管理企业用户的产品配置文件](https://helpx.adobe.com/cn/enterprise/using/manage-product-profiles.html)文档中的&#x200B;**将用户和用户组添加到产品配置文件**，了解有关如何使用 Admin Console 的更多详细信息。

## 可配置的权限 {#configurable-permissions}

以下权限可用于创建自定义配置文件。

| 权限 | 描述 |
| --- | --- |
| `Program Access` | 允许用户访问项目 |
| `Program Edit` | 允许用户编辑项目 |
| `Pipeline Create` | 允许用户创建新管道 |
| `Pipeline Delete` | 允许用户删除管道 |
| `Pipeline Edit` | 允许用户编辑管道 |
| `Production Deployments Approve/Reject` | 允许用户批准或拒绝生产部署步骤 |
| `Pipeline Executions Cancel` | 允许用户取消管道执行 |
| `Pipeline Executions Start` | 允许用户开始新的管道执行 |
| `Override/Reject Important Metric Failures` | 允许用户覆盖/拒绝重要量度失败 |
| `Production Deployments Schedule` | 允许用户计划生产部署步骤 |
| `Repository Info Access` | 允许用户访问存储库信息并生成访问密码 |
| `Repository Create` | 允许用户创建新的 Git 存储库 |
| `Repository Delete` | 允许用户删除 Git 存储库 |
| `Repository Edit` | 允许用户编辑 Git 存储库 |
| `Repository Code Generate` | 允许用户从原型生成项目 |
| `Content Copy Manage` | 允许用户管理内容复制操作 |

### 组织级权限 {#organization-level}

组织级权限始终适用于组织内的所有程序。

Cloud Manager 中组织级权限的一个示例是&#x200B;**存储库信息访问权限**。 此权限允许用户生成用户名、密码和存储库 URL，以访问客户项目并为其做出贡献。 虽然用户名和密码会在组织中的所有存储库中保持一致，但每个程序都有一个唯一的存储库 URL。

请参阅 [源代码存储库](/help/requirements/source-code-repository.md)了解更多信息。

## 术语 {#terms}

以下术语用于创建并管理自定义权限和预定义的角色。

| 术语 | 描述 |
| --- | --- |
| 预定义的权限 | 预定义的角色，例如&#x200B;**业务负责人**、**部署经理**&#x200B;等。监管 Cloud Manager 的各种功能。 有关预定义角色的详细信息，请参阅文档[基于角色的权限](/help/requirements/role-based-permissions.md)。 |
| 自定义权限 | Cloud Manager 功能，允许用户创建权限配置文件，以定义管理 Cloud Manager 所支持功能的角色 |
| 权限配置文件 | 在 Admin Console 中创建，用于管理可配置的权限，这些权限适用于权限配置文件中的用户 |
| 可配置的权限 | Cloud Manager 权限可在权限配置文件中配置 |
| 权限项 | 可应用权限的项目、环境或管道资源 |

权限项是指权限应用的范围。 通常，它是下列项之一。

| 权限项类型 | 示例 | 描述 |
| --- | --- | --- |
| 组织 | 组织：A 公司 | 所有对组织适用的资源。资源可以是项目、环境或管道。如果用户为任意权限添加一个组织，则该组织中的所有新资源也会具有此权限。 |
| 项目 | 项目 A | 项目的所有适用资源。 |
| 环境 | 项目 A：环境 | 适用于特定环境。 |
| 管道 | 项目 A：管道 | 适用于特定管道。 |

## 限制 {#limitations}

在使用自定义权限时，请记住以下限制：

* [一组有限的权限](#configurable-permissions)，可用于创建自定义配置文件。
* 项目、环境、管道等资源。在 Cloud Manager 中创建，可能需要两分钟才能显示在 Admin Console 中以进行权限配置。
* 在自定义权限服务无法响应的极少数情况下，预定义的配置文件仍可用，并且预定义的配置文件中的用户仍具有相应的访问权限。

## 常见问题解答 {#faq}

### 哪些权限配置文件是预定义的权限配置文件？

* 业务负责人
* 项目管理员
* 部署管理员
* 开发人员

有关预定义角色的详细信息，请参阅文档[基于角色的权限](/help/requirements/role-based-permissions.md)。

### 引入自定义配置文件后，预定义的权限配置文件会发生什么情况？

默认产品配置文件和 Cloud Manager 角色仍将照常发挥作用。

### 是否能编辑预定义的权限配置文件？

否，默认配置文件是不可编辑的。您不能在默认权限配置文件中添加或移除权限。 您只能在预定义的配置文件中添加或删除用户。

### 在自定义配置文件可用后，是否应删除预定义的权限配置文件？

不得从 Admin Console 中删除预定义的权限配置文件。

### 是否能将用户添加到多个权限配置文件？

是，一个用户可以是多个配置文件的一部分，包括预定义的权限配置文件和自定义权限配置文件。在将一个用户分配给多个配置文件时，所有分配的权限配置文件中的组合权限可供该用户使用。

### 如果用户有权编辑环境/管道，但无权访问包含该环境/管道的程序，会发生什么情况？

在这种场景下，如果用户没有包含环境或管道的&#x200B;**程序访问**&#x200B;权限，则将无法访问环境或管道。

### 如果我在同一个 IMS 组织中同时拥有 AEM as a Cloud Service 和 AMS 项目，会发生什么情况？我是否能通过一个配置文件管理权限？ {#ams-and-aemaacs}

为每种产品类型创建单独的配置文件。 也就是说，一个用于 AEM as Cloud Service，一个用于 Adobe Managed Services 或 AMS。
