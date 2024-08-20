---
title: 环境配置
description: 了解如何在 Cloud Manager 新用户引导过程中配置环境。
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 36%

---


# 环境配置 {#environments-provisioning}

了解如何在 Cloud Manager 新用户引导过程中配置环境。

## 配置 {#provisioning}

在新用户引导过程中，Adobe会自动配置您购买的所有AEM云环境，并将它们链接到[!UICONTROL Cloud Manager]中的项目。 每个AdobeManaged Services订阅都包含AEM云环境。 它们通常包括至少一个生产环境和一个暂存环境。 可选地，它们还可以包括一个或多个开发或测试环境。

## 欢迎电子邮件 {#welcome-email}

环境配置过程完成后，指定的客户管理员会收到一封欢迎电子邮件，确认已授予他们访问Adobe[!UICONTROL Experience Cloud]的权限。 欢迎电子邮件包含有关如何开始使用 [!UICONTROL Experience Cloud] 服务、[!UICONTROL AEM Managed Services] 云环境和 [!UICONTROL Cloud Manager] 自助式门户的详细信息。该电子邮件还包含了重要信息，例如客户成功工程师 (CSE) 联系信息、从何处获得支持资源、论坛、常见问题等。在该电子邮件中提供的资源列表中，您还将获得有关如何访问AEM云环境的[!UICONTROL Cloud Manager]的详细信息。

## 后续步骤 {#next-steps}

收到欢迎电子邮件后，您便能使用 Adobe IMS 凭据以系统管理员身份登录到 [!UICONTROL Cloud Manager]。登录后，您可以检查AEM云生产环境和非生产环境是否可用并且运行顺利。

[!UICONTROL Cloud Manager]使用这些AEM云环境运行CI/CD管道。 它将代码从其Git存储库部署到暂存环境。 然后，它将代码部署到您的AEM生产环境。 当您准备好开始为您的Web资产创建数字体验时，您还可以直接从[!UICONTROL Cloud Manager]访问您的AEM云环境。
