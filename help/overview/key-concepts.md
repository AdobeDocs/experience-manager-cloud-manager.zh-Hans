---
title: 重要概念
description: 与所有功能强大的工具一样，Cloud Manager 包含了许多概念和术语。本文档总结了开始使用 Cloud Manager 时的一些最重要内容。
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: ht
source-wordcount: '414'
ht-degree: 100%

---


# 重要概念 {#key-concepts}

与所有功能强大的工具一样，Cloud Manager 包含了许多概念和术语。本文档总结了开始使用 Cloud Manager 时的一些最重要内容。

## 应用程序 {#application}

应用程序是客户创建的一组自定义项和配置，以根据其具体的用例要求和需求来调整底层[解决方案](#solution)（例如 AEM Sites 或 AEM Assets）。 应用程序是一个逻辑单元，其中可能包含多个[工件](#artifact)。

虚构的 [WKND 生活方式应用程序](https://experienceleague.adobe.com/zh-hans/docs/ experience-manager-learn/getting-started-wknd-tutorial-develop/overview)是一个示例应用程序。

## 工件 {#artifact}

工件是一个可部署的单元，它是将源代码转换为一个单元的构建过程所产生的结果。 例如，一个包含源代码的 .zip 文件。

## 工件存储库 {#artifact-repository}

工件存储库是一个存储位置，可在其中保存和保护特定于客户的[工件](#artifact)。

## 环境 {#environment}

环境是一个[程序](#program)内的单个虚拟机集群对于 AEM，这种环境由一个创作实例（（可选）带有一个额外的冷辅助创作实例）、零个或多个发布实例、一个或多个 Dispatcher 实例和一个负载平衡器组成。

## Git 存储库 {#git-repository}

Git 存储库是一个存储客户特定源代码的位置，可[使用 Git](https://git-scm.com) 进行访问。

## 实例 {#instance}

实例是一台运行 AEM [解决方案](#solution)的特定虚拟服务器。从部署的角度来看，实例代表一个逻辑单元。

## 组织 {#organization}

组织是代表企业客户的 Adobe 构造。一家公司可能有多个组织，具体取决于它们在 Adobe Identity Management System (IMS) 中的配置方式。

## 管道 {#pipeline}

管道是一组按顺序运行或“执行”的部署步骤。

## 产品 {#product}

产品是由组织许可的[解决方案](#solution)中的一组特定功能。组织中不同的[项目](#program)可能有资格使用一组不同的产品，例如 AEM Sites、AEM Assets 或 AEM Forms。

## 项目 {#program}

项目是一组支持对客户计划进行逻辑分组的环境，通常对应于购买的服务水平协议 (SLA)。每个项目只具有一个生产环境，并且可能具有多个非生产环境。

## 解决方案 {#solution}

解决方案是某个 Adobe [!UICONTROL Experience Cloud] 解决方案。例如，Adobe Experience Manager、Adobe Target 或 Adobe Analytics。

## 步骤 {#step}

步骤是配置的指令集，它作为[管道](#pipeline)的构建块完成一些工作单元。
