---
title: 评估阶段
seo-title: Evaluation Phase
description: 了解产品更新向导的评估阶段如何使用模式检测器来评估升级复杂性。
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
TQID: https://experienceleague.adobe.com/dj-Wnq9FagNI3mzzVHcUH-sOufzb02D0juHqhtgpon0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 1b146c2a01d3371ed2fe014a15a84ddee2cd9b6c
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 40%

---

# 评估阶段 {#evaluation}

产品更新向导的第一阶段是&#x200B;**[!UICONTROL 评估]**&#x200B;阶段。 它会在向导中运行模式检测器以评估升级复杂性。 在此步骤结束时，您可以查看评估报告。

该报告通过检测以下内容的模式来检查创作实例的升级准备情况：

* 受升级影响或覆盖的区域中的规则违规。
* 它可检测不向后兼容的AEM 6.x功能或API，这些API在升级后可能会失败。

此报表可帮助估计升级到Adobe Experience Manager (AEM) 6.5所需的开发工作。

>[!NOTE]
>
>要了解有关模式检测器的更多信息，请参阅[使用模式检测器来评估升级复杂性](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector)。

## 运行评估报告 {#running}

模式检测器可在任何环境中运行。 但是，为了提高检测率并避免对关键实例造成任何性能影响，Cloud Manager会在创作实例的暂存环境中运行它。

**若要运行评估报告：**

1. 启动向导，如[产品更新向导](/help/product-update-wizard/overview.md)文档中所述。

1. 单击&#x200B;**[!UICONTROL 运行评估]**。

   ![运行评估](/help/assets/Run-Evaluation.png)

1. 向导会告知您操作的状态。 注意&#x200B;**进行中**&#x200B;或&#x200B;**已完成**（如果适用），同时正在生成评估报告。

1. 生成报告后，可单击&#x200B;**[!UICONTROL 下载报告]**&#x200B;以保存副本。

   ![已创建报告](/help/assets/Evaluation-1.png)

Cloud Manager中的当前产品更新向导仅支持&#x200B;**评估**&#x200B;阶段。 即将推出其他四个阶段，即&#x200B;**修正**、**执行**、**验证**&#x200B;和&#x200B;**完成**。
