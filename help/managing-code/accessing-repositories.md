---
title: 存储库访问信息
description: 了解如何使用 Cloud Manager 的自助 Git 帐户管理访问和管理 Adobe 管理的 Git 存储库。
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 04fbc4a3fdba8b108055d66a4fdb1a31994cb18e
workflow-type: ht
source-wordcount: '381'
ht-degree: 100%

---

# 存储库访问信息 {#accessing-repos}

了解如何使用 Cloud Manager 的自助 Git 帐户管理访问和管理 Adobe 管理的 Git 存储库。

## 从概述页面访问存储库信息 {#overview-page}

通过 Cloud Manager，您可以使用&#x200B;**管道**&#x200B;信息卡中的 **Access Repo Info** 轻松检索 Cloud Manager 存储库的存储库访问信息。

**存储库信息** 对话框可让您查看 Adobe 管理的存储库的以下访问信息：

* Git 用户名。
* Git 密码。
* Cloud Manager Git 存储库的 URL。
* 预构建的 Git 命令，用于快速将远程添加到 Git 存储库并推送代码。

  ![存储库信息窗口](assets/repository-info.png)

Cloud Manager 中没有关于[专用存储库](/help/managing-code/private-repositories.md)的访问信息。

**Access Repo Info**&#x200B;属性对具有&#x200B;**开发人员**&#x200B;或&#x200B;**部署管理员**&#x200B;角色的用户可见。

**从概述页面访问存储库信息：**

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 在 **程序概述** 页面的 **管道** 信息卡下，单击 **Access Repo Info**。

   ![管道信息卡上的 Access Repo Info](/help/managing-code/assets/pipelines-card2.png)

1. 要访问密码，必须生成一个新密码。在 **存储库信息** 对话框中，选择 **生成密码**。

1. 在确认对话框中，选择 **生成密码**。

1. 在 **密码** 字段右侧，点击 ![复制图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) 将密码复制到剪贴板。

   * 生成密码会使之前的密码失效。
   * Cloud Manager 不保存密码。安全地保存此密码是您的责任。
   * 由于 Cloud Manager 不保存密码，因此，如果您丢失密码，则必须重新生成一个新密码。

   ![在“存储库信息”对话框中复制密码](/help/managing-code/assets/repository-copy-password.png)

使用这些凭据，您可以克隆存储库的本地副本，在该本地存储库中进行更改，并在准备就绪后将任何代码更改提交回 Cloud Manager 中的远程代码存储库。

## 从存储库窗口访问存储库信息 {#repositories-window}

 **Access Repo Info** 功能也可从 [**存储库** 页面](/help/managing-code/managing-repositories.md)获得。该工具栏显示有关访问 Adobe 管理的存储库的相同信息。

## 撤销访问密码 {#revoke-password}

您可以随时撤销访问密码。

为此，[为此请求创建支持工单](https://experienceleague.adobe.com/zh-hans?support-solution=Experience+Manager&amp;support-tab=home#support)。该工单会得到优先处理，并且通常会在一天内撤销。
