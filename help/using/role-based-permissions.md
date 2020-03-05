---
title: 基于角色的权限
description: 可查看本页以了解“基于角色的权限”。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 157370b193c104915be063d1a4375f81839b88a2

---


# 基于角色的权限 {#role-based-permissions}

[!UICONTROL Cloud Manager] 具有预配置的角色，并具有相应的权限。 例如，开发人员开发代码并具有将代码推送到 **Git存储库的权限**。 或者，业务所有者具有不同的权限，允许他们定义关键绩效指标(KPI)并批准部署。

## 用户角色 {#user-roles}

角色管理 [!UICONTROL Cloud Manager] 在 [Adobe Admin Console中完成](https://helpx.adobe.com/enterprise/using/admin-console.html)。 其任何用 [!UICONTROL Cloud Manager] 户都必须是客户的IMS组织的成员，并具有Adobe Managed Services产品上下文。 通过将用户添加到管理控制台中的产品配置，可 [!UICONTROL Cloud Manager] 以提供特定角色成员关系。

要了解有关如何设置角色的更多信息，请参 [阅设置用户和角色](setting-up-users-and-roles.md)。

下表列出了您可以在Admin Console中分配的可能角色。

| **[!UICONTROL Cloud Manager]角色&#x200B;** | **描述** |
|---|---|
| 企业所有者 | 完成初始设置的主 [!UICONTROL Cloud Manager] 用户。 负责定义KPI、批准生产部署和覆盖重要的3层故障。 |
| 计划经理 | 用于 [!UICONTROL Cloud Manager] 执行团队设置、审核状态和查看KPI。 可能批准重要的3层故障。 |
| 部署管理器 | 管理部署操作。 用于 [!UICONTROL Cloud Manager] 执行舞台和生产部署。 可能批准重要的3层故障。 有权访问Git存储库。 |
| 开发人员 | 开发和测试自定义应用程序代码。 主要用 [!UICONTROL Cloud Manager] 于查看状态。 具有对Git存储库的提交访问权限。 |
| 客户成功工程师 | 通常支持AMS客户的成功。 与之交 [!UICONTROL Cloud Manager] 互以执行需要客户成功工程师(CSE)监督的部署。 |
| 内容作者 | 通常不与交互 [!UICONTROL Cloud Manager]。 此用户可以使用 [!UICONTROL Cloud Manager] 计划切换程序(已从 [!UICONTROL Experience Cloud]中导航)访问Adobe Experience Manager(AEM)。 |

## 用户权限 {#user-permissions}

每个角色都具有与每个角色关联的特定权限、预配置的任务或权限。 下表列出了可用的函数以及可以执行该函数的角色。

要进一步了解如何设置用户，请参阅 [设置用户和角色](setting-up-users-and-roles.md)。

| 权限 | 描述 | 企业所有者 | 部署管理器 | 计划经理 | 开发人员 | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| 读取应用程序 | 阅读计划KPI。 | x | x | x | x | x |
| 编写应用程序 | 程序设置或编辑。 | x |  |  |  |  |
| 添加计划 | 添加新计划。 | x |  |  |  |  |
| 阅读环境 | 请参阅环境详细信息。 | x | x | x | x | x |
| 创建执行 | 启动管道。 | x | x | x |  |  |
| 读取执行 | 请参阅执行状态。 | x | x | x | x | x |
| 恢复执行 | 可以在暂停时继续执行。 | x | x | x |  | x |
| 执行批准部署到生产 | 提供GoLive Approval。 | x | x | x |  |  |
| 执行计划部署到生产 | 计划生产部署。 | x | x | x |  | x |
| 执行部署到生产 | 暂停CSE监督时将应用程序部署到生产。 |  |  |  |  | x |
| 执行取消 | 取消当前执行。 | x | x | x |  |  |
| 执行覆盖质量门故障 | 批准重要的质量门故障。 | x | x | x |  |  |
| 管线创建 | 设置／编辑管道。 |  | x |  |  |  |
| 管道读取 | 请参阅管道详细信息。 | x | x | x | x | x |
| 管道写入 | 设置／编辑管道。 |  | x |  |  |  |
| 管道修改批准 | 允许编辑“业务所有者”选项。 |  | x |  |  |  |
| 管道修改受管部署 | 允许编辑CSE监督选项。 |  | x |  |  |  |
| 步骤阅读 | 查看步骤质量指标结果。 | x | x | x | x | x |
| 生成个人访问令牌 | 访问Git。 |  | x |  | x |  |
