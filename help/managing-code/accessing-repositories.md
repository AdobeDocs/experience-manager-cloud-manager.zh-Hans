---
title: 存储库访问信息
description: 了解如何使用 Cloud Manager 的自助 Git 帐户管理访问和管理 Adobe 管理的 Git 存储库。
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '361'
ht-degree: 100%

---

# 存储库访问信息 {#accessing-repos}

了解如何使用 Cloud Manager 的自助 Git 帐户管理访问和管理 Adobe 管理的 Git 存储库。

## 从概述页面访问存储库信息 {#overview-page}

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 从&#x200B;**项目概述**&#x200B;页面导航到&#x200B;**管道**&#x200B;信息卡。

   ![访问“环境”信息卡上的“访问存储库信息”按钮](assets/pipelines-card.png)

1. 单击&#x200B;**访问存储库信息**。 在&#x200B;**存储库信息…**&#x200B;对话框中，您可以查看以下内容：

   * Git 用户名。
   * Git 密码。
   * Cloud Manager Git 存储库的 URL。
   * 预构建的 Git 命令，用于快速将远程添加到 Git 存储库并推送代码。

   ![存储库信息窗口](assets/access-repo-info.png)

1. 要访问密码，必须生成一个新密码。单击 **`Generate password`**。

1. 在&#x200B;**您确定…**&#x200B;对话框中，通过单击&#x200B;**生成密码**&#x200B;来确认密码生成。

   ![确认密码生成](assets/confirm-password-generation.png)

1. 在&#x200B;**密码**&#x200B;字段，密码即生成。 单击复制图标将其复制到剪贴板。

   * 生成密码会使之前的密码失效。
   * Cloud Manager 不会保存您的访问密码。请确保安全保存此密码。
   * 如果密码丢失，则必须生成一个新密码。

   ![生成的密码示例](assets/generated-password.png)

使用这些凭据，您可以克隆存储库的本地副本，在该本地存储库中进行更改，并在准备就绪后将任何代码更改提交回 Cloud Manager 中的远程代码存储库。

>[!NOTE]
>
>* **访问存储库信息**&#x200B;选项对具有&#x200B;**开发人员**&#x200B;或&#x200B;**部署经理**&#x200B;角色的用户可见，或者对两者都可见。
>* **访问存储库信息**&#x200B;按钮仅显示 Adobe 管理的存储库的存储库访问信息。Cloud Manager 中没有关于[专用存储库](private-repositories.md)的访问信息。

## 从存储库窗口访问存储库信息 {#repositories-window}

**访问存储库信息**&#x200B;按钮也可在&#x200B;[**存储库**&#x200B;窗口](managing-repositories.md)的工具栏中找到。 该工具栏显示有关访问 Adobe 管理的存储库的相同信息。

## 撤销访问密码 {#revoke-password}

您可以随时撤销访问密码。[为此类请求创建支持工单](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support)。

该工单会得到优先处理，并且一般会在一天内撤销。
