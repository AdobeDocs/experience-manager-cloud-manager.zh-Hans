---
title: Cloud Manager 常见问题解答
description: 了解有关适用于 AMS 客户的 Cloud Manager 的最常见问题的解答。
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
TQID: https://experienceleague.adobe.com/aBIiazPCm-krE6rew6k-HSl-Uvc79eagMzM7uYciWdc
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 4dcc367f82c51626ca449ff389a9c9574a562ff7
workflow-type: tm+mt
source-wordcount: 764
ht-degree: 69%

---

# Cloud Manager 常见问题解答 {#cloud-manager-faqs}

本文档提供了有关适用于 AMS 客户的 Cloud Manager 的最常见问题的解答。

<!-- 
## Is it possible to use Java 11 with Cloud Manager builds? {#java-11}

Yes. You need to add the `maven-toolchains-plugin` with the correct settings for Java 11.

* This process is documented [here](/help/getting-started/using-the-wizard.md).
* For an example, see the [WKND sample project code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75). 
-->

## 从 Java 8 切换到 Java 11 后，我的构建失败，并显示一个有关 maven-scr-plugin 的错误。 我该怎么办？ {#maven-src-plugin}

尝试从Java 8切换到Java 11时，您的AEM Cloud Manager内部版本失败。 如果您遇到以下错误，则需要移除 `maven-scr-plugin` 并将所有 OSGi 注释转换为 OSGi R6 注释。

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

有关如何删除此插件的说明，[请见此处](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/)。

## 从 Java 8 切换到 Java 11 后，我的构建失败，并显示一个有关 RequireJavaVersion 的错误。 我该怎么办？ {#requirejavaversion}

对于 Cloud Manager 构建，`maven-enforcer-plugin` 可能会失败，并显示此错误。

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

出现此问题的原因是Cloud Manager使用其他版本的Java来运行Maven命令。 此版本与用于编译代码的版本不同。 从 `maven-enforcer-plugin` 配置中忽略 `requireJavaVersion`。

## 代码质量检查失败，现在部署已暂停。 是否能通过某种方式绕过此检查？ {#deployment-stuck}

是。 除安全评级之外的所有代码质量故障都是非关键量度。 因此，可以通过展开结果 UI 中的项目将它们作为部署管道的一部分绕过。

具有[部署经理、项目经理或业务所有者](/help/requirements/users-and-roles.md#role-definitions)角色的用户可以忽略这些问题。 在这种情况下，管道将会继续运行。 或者，他们可以接受这些问题，在这种情况下，管道会因失败而停止。

有关更多详细信息，请参阅[运行管道时的三层审核](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline)和[配置非生产管道](/help/using/non-production-pipelines.md#understanding-the-flow)文档。

## Cloud Manager 部署在 Adobe Managed Services 环境中执行性能测试步骤时失败。 如何解决此问题以传递关键量度？ {#debug-critical-metrics}

这个问题没有单一的最终答案。 但是，以下关于性能测试步骤的要点很有帮助：

* 此步骤是 Web 性能步骤。 也就是说，在Web浏览器中加载页面大约需要花费时间。
* 在测试期间，在Cloud Manager基础架构内的Chrome浏览器中加载结果.csv文件中列出的URL。
* 一个常见的失败量度是错误率。 因此，为了使 URL 通过，主 URL 必须以 `200` 状态加载，并且加载时间必须少于 `20` 秒。 如果页面加载时间超过 `20` 秒，则会被标记为 `504` 错误。
* 如果网站要求实施用户身份验证，请参阅[了解测试结果](/help/using/code-quality-testing.md#authenticated-performance-testing)，了解如何通过配置测试来针对网站进行身份验证。

有关质量检查的更多信息，请参阅[了解测试结果](/help/using/code-quality-testing.md)。

## 我是否能将 SNAPSHOT 用于 Maven 项目版本？ {#snapshot}

是。 对于开发人员部署，Git 分支 `pom.xml` 文件必须在 `<version>` 值的末尾包含 `-SNAPSHOT`。

这样一来，在版本未更改时便可以安装后续部署。 在开发人员部署中，不会为Maven内部版本添加或生成自动版本。

您也可以为暂存和生产构建或部署将版本设置为 `-SNAPSHOT`。 Cloud Manager 会自动设置适当的版本号并在 Git 中为您创建标记。 如果需要，可以稍后参考此标记。

[此处记录了](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling)有关版本处理的更多详细信息。

## 包和捆绑包版本控制如何用于暂存和生产部署？ {#staging-production}

在准备和生产部署中，会生成一个自动版本，[如此处所记录](/help/managing-code/maven-project-version.md)。

对于暂存和生产部署中的自定义版本控制，请设置适当的三部分Maven版本，如`1.0.0`。 每次部署到生产环境时提高版本。

Cloud Manager 自动将其版本添加到暂存和生产构建，并创建 Git 分支。 无需特殊配置。 如果您未按照之前所述设置Maven版本，则部署仍会成功，并且会自动设置版本。

## 对于Cloud Manager部署，我的Maven构建失败，但它会在本地构建，并且不会出现错误。 原因是什么？ {#maven-build-fail}

有关更多详细信息，请参阅此 [Git 资源](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)。

## 我无法使用 aio 命令设置变量。 我该怎么办？ {#set-variable}

在尝试通过`aio`命令列出或设置管道变量时，您收到如下所示的403错误。

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

在此情况下，需要在 Admin Console 中将执行这些命令的用户添加到&#x200B;**部署经理**&#x200B;角色。

有关更多详细信息，请参阅 [API 权限](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions)。
