---
title: Cloud Manager 2025.2.0 版的发行说明
description: 了解 Adobe Managed Services 上有关 Cloud Manager 2025.2.0 版本的信息。
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 51dd060ec9b922ace9ce537cac669c61154284e8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 20%

---

# Adobe Managed Services 上 Cloud Manager 2025.2.0 版的发行说明 {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

了解 Adobe Managed Services 上有关 [!UICONTROL Cloud Manager] 2025.2.0 版本的信息。

另请参阅[当前的Adobe Experience Manager as a Cloud Service发行说明](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/release-notes/home)。

## 发行日期 {#release-date}

[!UICONTROL Cloud Manager] 2025.2.0的发布日期是2025年2月13日星期四。

下一个计划发布于2025年3月13日星期四。

## 新增功能 {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* **升级的SonarQube**

  从2025年2月13日星期四开始，Cloud Manager代码质量步骤现在使用SonarQube 9.9.5.90363。

  更新后的规则可用于[此链接](/help/using/code-quality-testing.md#code-quality-testing-step)上的AMS，这些规则确定Cloud Manager管道的安全分数和代码质量。

* SonarQube 9.9现在是所有客户的默认代码质量扫描引擎。

* **Java 17和Java 21生成环境支持**

  客户现在可以选择使用Java 17或Java 21进行构建，从而受益于性能改进和新的语言功能。 有关配置步骤（包括更新Maven项目描述和某些库版本），请参阅[构建环境](/help/getting-started/build-environment.md)。

  >[!NOTE]
  >对于Cloud Service环境，当内部版本设置为Java 17或Java 21时，运行时默认为Java 21。

* **扩展的内容副本验证**

  内容副本验证规则已更新。 在此版本中，如果在源或目标环境中有活动的管道执行，则用户无法再触发内容副本。 用户必须等到所有正在进行的管道执行完成后才能启动内容副本。

<!-- 
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

The **Bring Your Own Git** feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
