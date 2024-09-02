---
title: 评估阶段
seo-title: Evaluation Phase
description: 了解产品更新向导的评估阶段如何使用模式检测器来评估升级复杂性。
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: ht
source-wordcount: '279'
ht-degree: 100%

---


# 评估阶段 {#evaluation}

产品更新向导中的第一个阶段是&#x200B;**[!UICONTROL 评估]**&#x200B;阶段，该阶段会直接用该向导中的模式检测器评估升级复杂性。 在此步骤结束时，您可以访问该评估报告。

利用生成的报告，您可以通过检测以下模式来检查作者实例的升级资格：

* 违反与升级影响或覆盖的区域相关的某些规则。

* 使用一项 AEM 6.x 功能或一个 API，此 API 无法与新版本 AEM 向后兼容，并且在升级后可能会中断。

该报告用于评估升级到 Adobe Experience Manager (AEM) 6.5 的过程中涉及的开发工作。

>[!NOTE]
>
>要了解有关模式检测器的更多信息，请参阅[使用模式检测器来评估升级复杂性](https://experienceleague.adobe.com/zh-hans/docs/ experience-manager-65/content/implementing/deploying/upgrading/pattern-detector)。

## 运行评估报告 {#running}

模式检测器可在任何环境中运行。 但是，为了提高检测率并避免关键业务实例速度减慢，Cloud Manager 会在作者实例的暂存环境中运行模式检测器。

**若要运行评估报告：**

1. 启动向导，如[产品更新向导](/help/product-update-wizard/overview.md)文档中所述。

1. 单击&#x200B;**[!UICONTROL 运行评估]**。

   ![运行评估](/help/assets/Run-Evaluation.png)

1. 向导会告知您操作的状态。在生成评估报告时会看到&#x200B;**进行中**&#x200B;或&#x200B;**已完成**&#x200B;状态（如适用）。

1. 生成报告后，可单击&#x200B;**[!UICONTROL 下载报告]**&#x200B;以保存副本。

   ![已创建报告](/help/assets/Evaluation-1.png)

Cloud Manager 中的当前版本的产品更新向导仅支持&#x200B;**评估**&#x200B;阶段。 其他四个阶段即将推出，即&#x200B;**修复**、**执行**、**验证**&#x200B;和&#x200B;**完成**。
