---
title: CI/CD 管道
description: 了解 CI/CD 管道以及它们如何在 Cloud Manager 中处理到暂存和生产环境的部署。
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '562'
ht-degree: 100%

---


# CI/CD 管道 {#ci-cd-pipeline}

了解 CI/CD 管道以及它们如何在 Cloud Manager 中处理到暂存和生产环境的部署。

## 概述 {#overview}

[!UICONTROL Cloud Manager] 包含一个持续集成/持续交付 (CI/CD) 框架，允许实施团队快速测试和交付新代码或更新后的代码。实施团队可以设置、配置和启动自动化 CI/CD 管道。该管道遵循 Adobe 编码的最佳实践，已执行全面的代码扫描，并确保最高的代码质量。

CI/CD 管道还可以自动实施单元测试和性能测试过程，提高部署效率并主动识别部署后要以高昂成本修复的关键问题。如果将代码部署到生产环境，则实施团队可以访问全面的代码性能报告，以了解可能对 KPI 和关键安全性验证产生的影响。

## 关于管道过程 {#pipeline-process}

下图说明了使用管道在 [!UICONTROL Cloud Manager] 中触发版本后发生的情况。

![管道过程](/help/assets/screen_shot_2018-05-30at82457pm.png)

| 管道步骤 | 描述 |
| --- | --- |
| 1. 启动版本 | 部署管理员使用 Git 承诺手动触发或基于定期计划触发版本。 |
| 2. 创建版本标记 | [!UICONTROL Cloud Manager] 使用自动生成的版本号（例如 `2018.531.245527.0000001222`）创建一个 Git 标记来标记版本。 |
| 3. 构建为具有自动生成的版本的发行版 | [!UICONTROL Cloud Manager] 使用新分配的版本号构建应用程序。 |
| 4. 评估代码质量 | [!UICONTROL Cloud Manager] 先扫描源代码并提供摘要，之后才能将代码部署到暂存环境。 |
| 5. 存储版本化工件 | 存储版本工件以便在后面的部署步骤中使用。 |
| 6. 自动将工件部署到 AMS AEM 暂存环境 | 将版本工件部署到暂存环境。 |
| 7. 触发自动测试 | [!UICONTROL Cloud Manager] 对工件运行性能测试和安全性测试。 |
| 8. 生产触发器部署 | 在自动测试完成后，[!UICONTROL Cloud Manager] 会启动到生产环境的部署。 |
| 9. [!UICONTROL Cloud Manager] 部署工件 | [!UICONTROL Cloud Manager] 拉出存储的版本工件。 |
| 10. 将工件部署到生产环境 | 将版本工件部署到生产环境。 |

### 如何设置 CI/CD 管道 {#how-to-setup-a-ci-cd-pipeline}

要了解有关管道配置的更多信息，请参阅[配置生产管道](/help/using/production-pipelines.md)和[配置非生产管道](/help/using/non-production-pipelines.md)文档。

## 质量审核 {#quality-gates}

CI/CD 管道提供质量审核或验收标准，必须先达到此标准，之后才能将代码从暂存环境移至部署环境。管道中有三项审核：

* 代码质量
* 性能测试
* 安全性测试

对于这三项审核中的每项审核，可以识别三个级别的问题：

* **关键** - 由审核识别的关键问题会导致管道立即失效。
* **重要** - 由审核识别的重要问题会导致管道进入暂停状态。部署经理、项目经理或业务所有者可以推翻这些问题，从而允许管道继续进行。或者，他们可以接受这些问题，导致管道因故障而停止。
* **信息** - 由审核识别的信息问题仅供参考，并且对管道执行没有影响。

以下是已识别问题的代码扫描示例。

![代码扫描示例](/help/assets/quality-gate-failed.png)

### 如何设置审核 {#how-to-setup-gates}

有关设置代码审核、质量审核和性能审核的详细信息，请参阅[配置生产管道](/help/using/production-pipelines.md)文档。
