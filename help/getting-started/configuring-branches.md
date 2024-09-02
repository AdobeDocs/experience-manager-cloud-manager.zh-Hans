---
title: 配置分支
description: 了解如何在 Git 中设置您的第一个分支，以及 CI/CD 管道如何使用它来部署您的应用程序代码。
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 90%

---


# 配置分支 {#configuring-branches}

了解如何在 Git 中设置您的第一个分支，以及 CI/CD 管道如何使用它来部署您的应用程序代码。

## 在 Git 中设置您的第一个分支 {#setting-up-your-first-branch-in-git}

将为登记到Cloud Manager中的每个项目配置一个最初为空的Git存储库[](/help/requirements/environment-provisioning.md)。 此存储库可以包含开发过程所需的任意数量的分支，但必须至少有一个分支可供 CI/CD 管道用来将应用程序代码部署到暂存和生产环境。 最佳实践是将 `main` 用作此分支的名称。 方便之处在于，这种方法是 Git 客户端在设置新项目时的默认行为。

例如，在设置新项目时，您会运行一组与以下内容类似的命令。

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>不是必须使用命令行客户端。 有多种图形 Git 客户端可用，它们可作为独立应用程序或集成开发环境 (IDE)（如 Eclipse 或 IntelliJ）的一部分。 只要客户端应用程序支持使用HTTPS的Git，它就应该与[!UICONTROL Cloud Manager]兼容。

## 推送您的第一个分支 {#pushing-your-first-branch}

在提交至少一项修订后，您可以将 [!UICONTROL Cloud Manager] 存储库添加为远程存储库，然后将提交内容推送到其中。

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>在 [!UICONTROL Cloud Manager] 新用户引导过程中，您的 Adobe 客户成功工程师（简称“CSE”）会为您提供具体的 URL 以及您的凭据。

## 其他分支 {#additional-branches}

对于非常简单的项目，单个 `main` 分支可能已够用，但在大多数情况下，需要更复杂的分支策略。 许多客户都遵循一个流程，即在名为 `develop` 的分支上执行日常开发活动。 然后，在部署时将开发分支合并到 `main` 分支中。

>[!TIP]
>
>要查看常见的 Git 命令，请参阅 [Git 备忘单](https://training.github.com/downloads/github-git-cheat-sheet)。
