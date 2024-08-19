---
title: 基于角色的权限
description: 了解 Cloud Manager 预先配置的基于角色的权限来管理对云资源的访问。
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 57%

---


# 基于角色的权限 {#role-based-permissions}

[!UICONTROL Cloud Manager 预配置了一些具有适当权限的角色。]例如，开发人员会开发代码并有权将代码推送到Git存储库。 业务负责人具有不同的权限，可让他们定义关键绩效指标 (KPI) 并审批部署。

>[!NOTE]
>
>本文档介绍了 Cloud Manager for Adobe Managed Services (AMS) 的基于角色的权限。
>
>AEM as a Cloud Service 的等效文档可以在 AEM as a Cloud Service 文档中的 [Cloud Manager 简介](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions)文档中找到。

## 用户角色 {#user-roles}

使用 [Admin Console](https://helpx.adobe.com/cn/enterprise/using/admin-console.html) 对 [!UICONTROL Cloud Manager] 进行角色管理。任何 [!UICONTROL Cloud Manager] 用户都必须是客户的 IMS 组织的成员，并且具有 Adobe Managed Services 产品上下文。通过在 Admin Console 中将用户添加到 [!UICONTROL Cloud Manager] 产品配置文件来提供特定的角色成员资格。

要了解有关如何设置角色的更多信息，请参阅[设置用户和角色](/help/requirements/users-and-roles.md)。

下表列出了可以在Admin Console中分配的角色。

| [!UICONTROL Cloud Manager]角色 | 描述 |
|---|---|
| 业务负责人 | 完成初始[!UICONTROL Cloud Manager]设置并负责定义KPI、审批生产部署和覆盖重要三层失败（如有必要）的主要用户。 |
| 内容作者 | 用户通常不会与Cloud Manager进行交互，但可以使用Cloud Manager项目切换器(从Experience Cloud导航)来访问Adobe Experience Manager (AEM)。 |
| 客户成功工程师 | 该用户主要支持AMS客户成功，并与[!UICONTROL Cloud Manager]合作以执行部署。 这些部署需要Adobe客户成功工程师(CSE)的监督。 |
| 部署管理员 | 用户使用[!UICONTROL Cloud Manager]管理部署操作以执行暂存和生产部署，可以在必要时审批重要三层失败，并且有权访问Git存储库。 |
| 开发人员 | 用户开发和测试自定义应用程序代码，主要使用[!UICONTROL Cloud Manager]来查看部署状态，并具有对Git存储库的提交访问权限。 |
| 项目管理员 | 用户使用[!UICONTROL Cloud Manager]执行团队设置、审查状态、查看KPI，并且可以在必要时审批重要三层失败。 |

## 用户权限 {#user-permissions}

每个角色都具有相关联的特定预配置权限。 下表列出了可用的权限以及可以执行这些权限的角色。

| 权限 | 描述 | 业务负责人 | 部署管理员 | 项目管理员 | 开发人员 | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| 读取应用程序 | 读取项目 KPI | x | x | x | x | x |
| 编写应用程序 | 项目设置或编辑 | x | | | | |
| 添加项目 | 添加新项目 | x | | | | |
| 读取环境 | 查看环境详细信息 | x | x | x | x | x |
| 创建执行 | 启动管道 | x | x | x | | |
| 读取执行 | 查看执行状态 | x | x | x | x | x |
| 恢复执行 | 能够在暂停后恢复执行 | x | x | x | | x |
| 执行审批部署到生产 | 提供上线审批 | x | x | x | | |
| 计划将执行部署到生产 | 计划生产部署 | x | x | x | | x |
| 将执行部署到生产 | 在因 CSE 监督而暂停时将应用程序部署到生产环境 | | | | | x |
| 执行取消 | 取消当前执行 | | | x | | |
| 执行覆盖质量审核失败 | 审批重要质量审核失败 | x | x | x | | |
| 管道创建 | 设置/编辑管道 | | x | | | |
| 管道读取 | 查看管道详细信息 | x | x | x | x | x |
| 管道写入 | 设置/编辑管道 | | x | | | |
| 管道修改审批 | 允许编辑“业务负责人”选项 | | x | | | |
| 管道修改托管部署 | 允许编辑“CSE 监督”选项 | | x | | | |
| 管道删除 | 允许管道删除 | | x | | | |
| 步骤读取 | 查看步骤质量量度结果 | x | x | x | x | x |
| 生成个人访问令牌 | 访问 Git | | x | | x | |

要了解有关如何设置用户的详细信息，请参阅[设置用户和角色](/help/requirements/users-and-roles.md)。

>[!TIP]
>
>还提供具有可配置权限的自定义权限配置文件。有关详细信息，请参阅[自定义权限](/help/using/custom-permissions.md)。
