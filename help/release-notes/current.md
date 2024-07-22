---
title: 2024.7.0 的发行说明
description: 这些是 Cloud Manager 2024.7.0 版的发行说明。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 87c603a89b99f6984828280cba2041da8c72e839
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 63%

---


# Cloud Manager 2024.7.0 版的发行说明 {#release-notes}

此页面记载 [!UICONTROL Cloud Manager] 2024.7.0 版的发行说明。

>[!NOTE]
>
>有关 AEM as a Cloud Service 中的 Cloud Manager 的最新发行说明，请参阅 [AEM as a Cloud Service 中的 Cloud Manager 的最新发行说明](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)。

## 发布日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.7.0版的发布日期为2024年7月18日。 计划于 2024 年 8 月 8 日发布下一个版本。

## 新增功能 {#what-is-new}

* [生产管道](/help/using/production-pipelines.md#adding-production-pipeline)和[非生产管道](/help/using/non-production-pipelines.md#adding-non-production-pipeline)在Git更改上触发&#x200B;**On Git Changes**&#x200B;以在提交上启动管道，现在可供[专用存储库使用。](/help/managing-code/private-repositories.md)
* 生产前管道只能手动触发，在Git更改&#x200B;**时无法配置为**。
* 对于仅用于生产的管道，可升级执行列表包括工件版本大于生产环境中部署的工件版本的那些执行。
* [AEM项目原型](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)已更新为[版本49。](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49)


## 早期采用计划 {#early-adoption}

成为我们早期采用计划的一部分，并有机会测试一些即将推出的功能

### 仅暂存和仅生产管道 {#staging-production-only-pipelines}

我们引入了对[仅暂存和仅生产管道](/help/using/stage-prod-only.md)的支持，使您能够将全栈生产部署管道拆分为更小的专用部署。

如果您有兴趣测试这项新功能并共享您的反馈，请从您 Adobe ID 关联的电子邮件地址发送电子邮件至 `Grp-cloudmanager_splitpipelines@adobe.com`。
