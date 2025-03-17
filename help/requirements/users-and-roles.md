---
title: 添加用户和角色
description: 了解如何使用 Admin Console 添加用户和角色以及创建轮廓。
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: 53fb666ab6caff7a697d7f1942ce25f2bf27a2ce
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 89%

---


# 添加用户和角色 {#add-users-and-roles}

必须具有特定的权限，才能使用 [!UICONTROL Cloud Manager] 中的许多功能。例如，仅允许某些用户为项目设置关键绩效指标 (KPI)。这些权限将在逻辑上按角色分组。

[!UICONTROL Cloud Manager] 当前为用户定义了四个角色，这些角色控制特定功能的可用性：

* 业务负责人
* 项目管理员
* 部署管理员
* 开发人员

>[!NOTE]
>
>要使用 [!UICONTROL Cloud Manager]，您必须具有 Adobe ID 和 Adobe Managed Services 产品上下文。

## 角色定义 {#role-definitions}

下表总结了 Cloud Manager 中的角色。

| [!UICONTROL Cloud Manager] 角色 | 描述 |
| --- | --- |
| 业务负责人 | 负责定义 KPI、审批生产部署和覆盖重要三层失败（如有必要）。 |
| 项目管理员 | 他们会使用 [!UICONTROL Cloud Manager] 执行团队设置、审查状态、查看 KPI，并且可以在必要时审批重要三层失败。 |
| 部署管理员 | 管理部署操作并使用 [!UICONTROL Cloud Manager] 执行暂存/生产部署、编辑 CI/CD 管道、在必要时审批重要的三层失败。他们还可以访问 Git 存储库。 |
| 开发人员 | 开发并测试自定义应用程序代码并主要使用 [!UICONTROL Cloud Manager] 查看部署状态，还有权访问 Git 存储库以提交代码。 |
| 客户成功工程师 | CSE 通常会帮助 AMS 客户取得成功。他们会与 [!UICONTROL Cloud Manager] 交互，以执行需要 CSE 监督的部署。 |
| 内容作者 | 他们一般不与 [!UICONTROL Cloud Manager] 交互，但可使用 [!UICONTROL Cloud Manager] 项目切换器访问 AEM。 |

>[!NOTE]
>
>Admin Console 中的开发人员角色与 [!UICONTROL Cloud Manager] 中的开发人员角色无关。

## 使用 Admin Console 创建轮廓 {#using-admin-console-to-create-a-profile}

从 Admin Console 中管理 [!UICONTROL Cloud Manager] 角色。通过将用户添加到 [!UICONTROL Cloud Manager] 产品配置文件，提供特定的角色成员资格。

Admin Console 是一个中央位置，用于管理整个组织内的 Adobe 授权。要进一步了解Adobe Admin Console，请参阅 [Admin Console](https://helpx.adobe.com/cn/enterprise/using/admin-console.html)。

管理员必须在 [!UICONTROL AEM 托管服务]产品上下文中创建新的产品轮廓，以便为 [!UICONTROL Cloud Manager] 用户分配基于角色的权限，对应于四个 [!UICONTROL Cloud Manager] 角色中的每一个角色。

* 业务负责人
* 部署管理员
* 开发人员
* 项目管理员

您可以使用 Admin Console 创建用户或群组或将用户或群组添加到这些产品轮廓中。

1. 登录到 [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) 上的 Admin Console。

1. 单击&#x200B;**概述**&#x200B;选项卡，然后在&#x200B;**产品和服务**&#x200B;信息卡上单击要修改的产品。如果此处未列出它，请使用&#x200B;**产品**&#x200B;选项卡找到该产品并单击它。

   ![Admin Console“概述”选项卡](/help/assets/admin-console-overview.png)

1. 在&#x200B;**产品**&#x200B;选项卡上，单击要为其将用户/组添加到产品配置文件的环境。

   ![Admin Console“产品”选项卡](/help/assets/admin-console-product.png)

1. 在&#x200B;**产品配置文件**&#x200B;选项卡上，单击&#x200B;**新建配置文件**&#x200B;以添加新配置文件。

   ![新建配置文件](/help/assets/admin-console-product-profiles.png)

1. 提供信息以便为 [!UICONTROL Cloud Manager] 设置新角色。

   * **配置文件名称** - **配置文件名称**&#x200B;可为任何内容，但为了避免混淆，建议使用&#x200B;**建议的配置文件名称**&#x200B;列中的值。
   * **显示名称** - **显示名称**&#x200B;必须为 [!UICONTROL Cloud Manager] 定义的技术值（见下表）。
   * **权限组** - 可为该配置文件选择一个权限组（并非总是可用）。

   ![创建新配置文件](/help/assets/screen_shot_2018-05-04at171819.png)

   | 角色 | 显示名称（必需） | 建议的配置文件名称 |
   |---|---|---|
   | 业务负责人 | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 业务负责人角色 |
   | 部署管理员 | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 部署管理员角色 |
   | 开发人员 | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 开发人员角色 |
   | 项目管理员 | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - 项目管理员角色 |


1. 单击&#x200B;**完成**&#x200B;以保存新配置文件。

## 将配置文件分配给用户或用户组 {#assign-profiles}

在创建产品配置文件后，您可以将用户或用户组分配给这些配置文件。

1. 登录到 [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) 上的 Admin Console。

1. 在 Admin Console 中，选择&#x200B;**用户**&#x200B;选项卡。

   ![“用户”选项卡](/help/assets/admin-console-users.png)

1. 单击左侧导航面板中的&#x200B;**用户**，然后单击一个用户以修改它。

1. 单击&#x200B;**产品**&#x200B;部分中的![更多图标，省略号](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)，然后单击&#x200B;**编辑**。

   ![编辑用户](/help/assets/admin-console-edit-user.png)

1. 在&#x200B;**编辑产品和用户组**&#x200B;对话框中，单击![添加图标，加号](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)，然后选择要分配给该用户的配置文件。

   * 如果用户已分配给角色，则![添加图标加上](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)按钮是编辑按钮（铅笔），但工作方式相同。

   ![编辑产品和用户组](/help/assets/admin-console-edit-products-and-user-groups.png)

1. 单击&#x200B;**保存**&#x200B;以将配置文件保存到用户。

重复相同步骤以将配置文件分配给用户组，但在&#x200B;**用户**&#x200B;选项卡上从左侧导航面板中选择&#x200B;**用户组**。单击用户组并选择&#x200B;**已分配的产品配置文件**&#x200B;单击&#x200B;**分配产品配置文件**&#x200B;以分配配置文件。

![将配置文件分配给组](/help/assets/admin-console-edit-user-groups.png)
