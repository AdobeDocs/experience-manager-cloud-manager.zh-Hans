---
title: 2024.7.0 的发行说明
description: 了解Cloud Manager 2024.7.0的发行说明。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 4%

---


# Cloud Manager 2024.7.0发行说明 {#release-notes}

本页记录了[!UICONTROL Cloud Manager] 2024.7.0的发行说明。

>[!NOTE]
>
>有关AEM as a Cloud Service中Cloud Manager的最新发行说明，请参阅AEM as a Cloud Service的最新发行说明中的[Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)。

## 发布日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.7.0的发布日期是2024年7月18日。 下一个版本计划于2024年8月13日发布。

## 新增功能 {#what-is-new}

* [生产管道](/help/using/production-pipelines.md#adding-production-pipeline)和[非生产管道](/help/using/non-production-pipelines.md#adding-non-production-pipeline)在Git更改上触发&#x200B;**On Git Changes**&#x200B;以在提交上启动管道，现在可用于[专用存储库](/help/managing-code/private-repositories.md)。
* 生产前管道只能手动触发，不能在Git更改&#x200B;**时配置为**。
* 对于仅用于生产的管道，可升级执行列表包括其工件版本大于在生产环境中部署的工件版本的执行。
* [AEM项目原型](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-core-components/using/developing/archetype/overview)已更新为[版本49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49)。

## 早期采用计划 {#early-adoption}

成为Cloud Manager早期采用计划的一部分，并有机会测试一些即将推出的功能

### 仅限暂存和仅限生产的管道 {#staging-production-only-pipelines}

现在引入了对[仅暂存管道和仅生产管道](/help/using/stage-prod-only.md)的支持，可让您将全栈生产部署管道拆分为更小的专用部署。

如果您有兴趣测试这项新功能并分享您的反馈，请从与Adobe ID关联的电子邮件地址向`Grp-cloudmanager_splitpipelines@adobe.com`发送电子邮件。
