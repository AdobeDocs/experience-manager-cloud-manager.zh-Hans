---
title: 在Cloud Manager中添加专用存储库
description: 了解如何设置 Cloud Manager 以使用您自己的专用 GitHub 存储库。
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 45%

---


# 在Cloud Manager中添加专用存储库 {#private-repositories}

了解如何设置 Cloud Manager 以使用您自己的专用 GitHub 存储库。

## 概述 {#overview}

通过将Cloud Manager与专用GitHub存储库配置，您可以直接在GitHub中验证代码，而无需经常与Adobe存储库同步。

>[!NOTE]
>
>此功能为公共 GitHub 所独有。不支持自托管 GitHub。

## 配置 {#configuration}

配置包含两个主要步骤：

1. [添加存储库](#add-repo)
1. [专用存储库所有权验证](#validate-ownership)

### 添加存储库 {#add-repo}

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
>有关在Cloud Manager中管理存储库的详细信息，请参阅[Cloud Manager存储库](/help/managing-code/managing-repositories.md)。

### 专用存储库所有权验证 {#validate-ownership}

Cloud Manager 现已知道您的 GitHub 存储库，但它仍需要其访问权限。要授予访问权限，您需要安装 Adobe GitHub 应用程序并验证您是否拥有指定的存储库。

1. 添加您自己的存储库后，将显示&#x200B;**私有存储库所有权验证**&#x200B;对话框。

   ![专用存储库所有权验证](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager使用GitHub应用程序与您的存储库安全交互。

   GitHub组织的所有者必须安装位于`https://github.com/apps/cloud-manager-for-aem`的应用程序并授予对存储库的访问权限。 有关详细信息，请参阅GitHub的文档。

1. 要增强安全性，请在存储库的默认分支中创建机密文件。 单击&#x200B;**生成**。

1. 通过单击&#x200B;**确认**&#x200B;以确认秘密文件的生成。

   ![确认密码生成](/help/assets/repositories/confirm-generation.png)

1. 返回&#x200B;**私有存储库所有权验证**&#x200B;对话框，Cloud Manager已在&#x200B;**机密文件内容**&#x200B;字段中生成内容。 复制该字段中的内容。

   机密文件的内容只显示一次。 如果在关闭此窗口之前没有复制内容，则必须重新生成密码。

   ![复制秘密文件内容](/help/assets/repositories/new-secret.png)

1. 在 GitHub 存储库的默认分支中创建一个名为 `.well-known/adobe/cloud-manager-challenge` 的新文件，将秘密文件内容粘贴到该文件中并进行保存。

1. 安装应用程序且存储库中存在机密文件后，您可以在&#x200B;**私有存储库所有权验证**&#x200B;对话框中单击&#x200B;**验证**。

可以安装应用程序，也可以按任意顺序生成机密文件。 但是，必须先完成这两个步骤，然后才能进行验证。

在验证之前，存储库将以红色图标列出，表示它尚未验证且尚无法使用。

![未经验证的存储库](/help/assets/repositories/unvalidated-repo.png)

请注意，**类型**&#x200B;列可轻松识别 Adobe 提供的存储库 (**Adobe**) 和您自己的 GitHub 存储库 (**GitHub**)。

要稍后返回到存储库并完成验证，请转到&#x200B;**存储库**&#x200B;页面。 单击您添加的GitHub存储库旁边的省略号按钮，然后从下拉菜单中选择&#x200B;**所有权验证**。

## 将专用存储库与Cloud Manager结合使用 {#using}

在Cloud Manager中验证GitHub存储库后，集成即完成，您可以将该存储库与Cloud Manager结合使用。

1. 创建拉取请求时，会自动启动GitHub检查。

   ![GitHub 检查](/help/assets/repositories/github-checks.png)

1. 对于每个拉取请求，都会自动创建[全栈栈代码质量管道](/help/using/managing-pipelines.md)。 每次更新提取请求时，此管道将启动。

1. 在代码质量检查完成之前，GitHub检查将保持运行状态。 代码质量结果随后将传播到GitHub检查。

   ![GitHub 代码质量检查](/help/assets/repositories/github-code-quality.png)

在关闭或合并提取请求时，将自动删除创建的全栈代码质量管道。

>[!TIP]
>
>有关运行拉取请求检查时通过 GitHub 提供信息的详细信息，请参阅文档 [GitHub 检查批注](github-annotations.md)。

>[!TIP]
>
>您可以控制自动创建的管道，验证对专用存储库的每个拉取请求。请参阅 [GitHub 检查专用存储库的配置](github-check-config.md)，了解更多信息。

## 将专用存储库与管道关联 {#pipelines}

经过验证的专用存储库可以与[全栈管道相关联](/help/overview/ci-cd-pipelines.md)。

## 限制 {#limitations}

在 Cloud Manager 中使用专用存储库时会受到某些限制。

* 使用Cloud Manager中的GitHub检查，无法暂停拉取请求验证。 如果在Cloud Manager中验证了GitHub存储库，Cloud Manager将尝试验证为该存储库创建的拉取请求。
* 如果从您的GitHb组织中删除了AdobeGitHub应用程序，则此操作将删除所有存储库的拉取请求验证功能。
* 在生产全栈管道上使用专用存储库时，不会创建和推送Git标记。
* 当新的提交被推送到选定的分支时，使用专用存储库和提交构建触发器的管道不会自动启动。
* [工件重用功能](/help/getting-started/project-setup.md#build-artifact-reuse)不适用于专用存储库。
