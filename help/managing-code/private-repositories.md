---
title: 在 Cloud Manager 中添加专用存储库
description: 了解如何设置 Cloud Manager 以使用您自己的专用 GitHub 存储库。
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: 34c0b39d50dd4998cb75cc032d71d24798dee729
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 94%

---


# 在 Cloud Manager 中添加专用存储库 {#private-repositories}

了解如何设置 Cloud Manager 以使用您自己的专用 GitHub 存储库。

## 概述 {#overview}

通过使用您的私有 GitHub 存储库配置 Cloud Manager，您可以直接在 GitHub 中验证代码，而无需频繁与 Adobe 存储库同步。

>[!NOTE]
>
>此功能为公共 GitHub 所独有。不支持自托管 GitHub。

## 配置 {#configuration}

配置包含两个主要步骤：

1. [添加存储库](#add-repo)
1. [专用存储库所有权验证](#validate-ownership)



### 添加一个存储库 {#add-repo}

1. 在 Cloud Manager 中，从&#x200B;**项目概述**&#x200B;页面中，单击&#x200B;**存储库**&#x200B;选项卡以切换到&#x200B;**存储库**&#x200B;页面，然后单击&#x200B;**添加存储库**。

1. 在&#x200B;**添加存储库**&#x200B;对话框中，选择&#x200B;**专用存储库**&#x200B;作为存储库类型。

1. 提供您的存储库的详细信息

   * **存储库名称** - 一个富有表现力的名称
   * **存储库 URL** - 存储库的 URL，它必须以 `.git` 结尾
   * **描述**（可选）- 存储库的更详细描述（如有必要）

   ![添加自己的存储库](/help/assets/repositories/add-own-github.png)

1. 单击&#x200B;**保存**。

>[!TIP]
>
>有关在 Cloud Manager 中管理存储库的详细信息，请参阅 [Cloud Manager 存储库](/help/managing-code/managing-repositories.md)。



### 验证专用存储库所有权 {#validate-ownership}

Cloud Manager 现已知道您的 GitHub 存储库，但它仍需要其访问权限。要授予访问权限，您需要安装 Adobe GitHub 应用程序并验证您是否拥有指定的存储库。

1. 添加您自己的存储库后，**专用存储库所有权验证**&#x200B;对话框将会显示。

   ![专用存储库所有权验证](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager 使用 GitHub 应用程序与您的存储库安全地交互。

   您的 GitHub 组织的所有者必须安装位于 `https://github.com/apps/cloud-manager-for-aem` 的应用程序并授予对存储库的访问权限。 有关详细信息，请参阅 GitHub 的文档。

1. 为了增强安全性，请在存储库的默认分支中创建一个秘密文件。 单击&#x200B;**生成**。

1. 通过单击&#x200B;**确认**&#x200B;以确认秘密文件的生成。

   ![确认密码生成](/help/assets/repositories/confirm-generation.png)

1. 返回&#x200B;**专用存储库所有权验证**&#x200B;对话框中，Cloud Manager 已在&#x200B;**秘密文件内容**&#x200B;字段中生成了该内容。 复制该字段中的内容。

   秘密文件的内容仅显示一次。 如果您在关闭此窗口之前未复制该内容，则必须重新生成密码。

   ![复制秘密文件内容](/help/assets/repositories/new-secret.png)

1. 在 GitHub 存储库的默认分支中创建一个名为 `.well-known/adobe/cloud-manager-challenge` 的新文件，将秘密文件内容粘贴到该文件中并进行保存。

1. 在安装应用程序并将秘密文件保存在存储库中后，可以单击&#x200B;**专用存储库所有权验证**&#x200B;对话框中的&#x200B;**验证**。

可以安装该应用程序，并且您可以按任何顺序生成秘密文件。 但必须先完成这两个步骤，之后才能进行验证。

在验证之前，存储库将会列出红色图标，这表示它尚未经过验证，因此尚无法使用。

![未经验证的存储库](/help/assets/repositories/unvalidated-repo.png)

请注意，**类型**&#x200B;列可轻松识别 Adobe 提供的存储库 (**Adobe**) 和您自己的 GitHub 存储库 (**GitHub**)。

要稍后返回存储库并完成验证，请转到&#x200B;**存储库**&#x200B;页面。 点击您添加的 GitHub 存储库旁边的![“更多”图标（省略号 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)），然后点击&#x200B;**所有权验证**。


## 将专用存储库与 Cloud Manager 结合使用 {#using}

在 Cloud Manager 中验证 GitHub 存储库后，便已完成集成，您可以在 Cloud Manager 中使用该存储库。

**将专用存储库与 Cloud Manager 结合使用：**

1. 在创建提取请求时，GitHub 检查会自动启动。

   ![GitHub 检查](/help/assets/repositories/github-checks.png)

1. 对于每个提取请求，系统会自动创建[全栈代码质量管道](/help/using/managing-pipelines.md)。 每次更新提取请求时，此管道便会启动。

1. GitHub 检查会持续运行，直到完成代码质量检查。 之后，代码质量结果会传播到 GitHub 检查。

   ![GitHub 代码质量检查](/help/assets/repositories/github-code-quality.png)

在关闭或合并提取请求时，将自动删除创建的全栈代码质量管道。

>[!TIP]
>
>有关运行提取请求检查时通过 GitHub 提供信息的详细信息，请参阅文档 [GitHub 检查批注](github-annotations.md)。

>[!TIP]
>
>您可以控制自动创建的管道，验证对专用存储库的每个提取请求。请参阅 [GitHub 检查专用存储库的配置](github-check-config.md)，了解更多信息。



## 将专用存储库与管道关联 {#pipelines}

经过验证的专用存储库可以与[全栈和前端管道相关联](/help/overview/ci-cd-pipelines.md)。



## 限制 {#limitations}

在 Cloud Manager 中使用专用存储库时会受到某些限制。

* 在生产全栈管道上使用专用存储库时，不会创建和推送任何 Git 标记。
* 如果从您的 GitHb 组织中删除 Adobe GitHub 应用程序，则该操作会移除所有存储库的提取请求验证功能。
* 将新提交推送到所选分支时，使用专用存储库和已提交生成触发器的管道不会自动启动。
* [工件重用功能](/help/getting-started/project-setup.md#build-artifact-reuse)不适用于专用存储库。
* 您无法使用 Cloud Manager 的 GitHub 检查来暂停提取请求验证。 如果在 Cloud Manager 中验证 GitHub 存储库，则 Cloud Manager 会尝试验证为该存储库创建的提取请求。
* 如果您的GitHub组织强制执行IP限制，请打开支持案例以获取必须允许的IP地址列表。
