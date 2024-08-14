---
title: Cloud Manager 2024.8.0发行说明
description: 了解Cloud Manager 2024.8.0的发行说明。
feature: Release Information
source-git-commit: 34f15aff7478a6a0884f88f534a7dff996a8570e
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---


# Cloud Manager 2024.8.0发行说明 {#release-notes}

本页记录了[!UICONTROL Cloud Manager] 2024.8.0的发行说明。

>[!NOTE]
>
>有关AEM as a Cloud Service中Cloud Manager的最新发行说明，请参阅AEM as a Cloud Service的最新发行说明中的[Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)。

## 发布日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.8.0的发布日期是2024年8月13日。 下一个版本计划于2024年9月14日发布。

## 新增功能 {#what-is-new}

* 对于仅阶段管道和仅生产管道（作为[早期采用者计划](#staging-production-only-pipelines)的一部分提供），您现在可以在[紧急模式](/help/using/stage-prod-only.md#emergency-mode)跳过阶段测试中执行这些管道。

## 早期采用计划 {#early-adoption}

成为Adobe早期采用计划的一部分，并有机会测试一些即将推出的功能。

### 仅限暂存和仅限生产的管道 {#staging-production-only-pipelines}

Adobe很高兴地宣布引入对[仅限暂存和仅限生产的管道](/help/using/stage-prod-only.md)的支持。 此新功能让您可以将全栈生产部署管道划分为更小的、更专业的部署。

如果要测试此功能并提供反馈，请使用与您的Adobe ID关联的电子邮件地址向`Grp-cloudmanager_splitpipelines@adobe.com`发送电子邮件。

## 错误修复

* 删除管道后，发现管道步骤正在运行，此问题现已罕见地得以纠正。
* 现在，在第一次尝试时重新运行管道可正常工作，从而更正了必须多次开始重新运行的一个罕见问题。
* 全栈管道的计划部署步骤现在遵循所选的计划日期，并且不会还原为&#x200B;**现在**。
* 现已正确反映失败的复制内容任务的状态，在极少数情况下不再错误地显示`In Progress`状态。

## 已知问题 {#known-issues}

{{content-copy-known-issues}}
