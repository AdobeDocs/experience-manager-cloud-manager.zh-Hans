---
title: 2024.6.0 的发行说明
description: 这些是 Cloud Manager 2024.6.0 版的发行说明。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 851b556c0917d9f6d97d958a0c8e8aeff4141079
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 100%

---


# Cloud Manager 2024.6.0 版的发行说明 {#release-notes}

此页面记载 [!UICONTROL Cloud Manager] 2024.6.0 版的发行说明。

>[!NOTE]
>
>有关 AEM as a Cloud Service 中的 Cloud Manager 的最新发行说明，请参阅 [AEM as a Cloud Service 中的 Cloud Manager 的最新发行说明](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=zh-Hans)。

## 发布日期 {#release-date}

[!UICONTROL Cloud Manager] 2024.6.0 版的发布日期为 2024 年 6 月 6 日。下一个版本计划于 2024 年 7 月 18 日发布。

## 新增功能 {#what-is-new}

* 您现在可以[使用您自己的 GitHub 存储库](/help/managing-code/private-repositories.md)作为全堆叠管道的源。
   * 此外，您还可以利用带有 [Git 子模块](/help/managing-code/git-submodules.md)的 GitHub 存储库，为您提供对用于拉取请求验证的自动生成管道的增强控制，并允许您在代码扫描阶段定义关键指标的行为。
   * [您还可以选择](/help/managing-code/github-check-config.md)在 GitHub 上保存报告历史记录、命名管道和设置管道变量以满足您的需求。
* 新的 OakPal 规则已添加到[云管理器代码质量扫描中](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)。
   * 自 2024 年 6 月起添加的每条新规则都是非重大更改。
   * 我们建议您尽快解决这些问题，因为从 Cloud Manager 2024 年 8 月版本开始，这些新规则将导致管道失败。

## 早期采用计划 {#early-adoption}

成为我们早期采用计划的一部分，并有机会测试一些即将推出的功能

### 仅暂存和仅生产管道 {#staging-production-only-pipelines}

我们引入了对[仅暂存和仅生产管道](/help/using/stage-prod-only.md)的支持，使您能够将全栈生产部署管道拆分为更小的专用部署。

如果您有兴趣测试这项新功能并共享您的反馈，请从您 Adobe ID 关联的电子邮件地址发送电子邮件至 `Grp-cloudmanager_splitpipelines@adobe.com`。
