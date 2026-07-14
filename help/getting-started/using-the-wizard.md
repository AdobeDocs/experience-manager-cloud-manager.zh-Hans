---
title: 使用新项目向导
description: 关注此页面，了解如何使用该向导创建 AEM 应用程序项目。
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
TQID: https://experienceleague.adobe.com/zoiHL1lNC2XN-T9g0dh3pQyL4Yw3uYgFpHs8d6hkj3M
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 317
ht-degree: 54%

---

# 使用新建项目向导 {#using-the-wizard}

当您以新客户身份登记到Cloud Manager时，将为您提供一个空的Git存储库。 为了帮助您入门，Cloud Manager提供了一个向导，可让您根据[AEM项目原型](https://github.com/adobe/aem-project-archetype)创建一个最小的AEM项目作为起点。

**要使用新建项目向导：**

1. 在 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 中登录 Cloud Manager 并选择适当的组织。

1. 如果您尚未这样做，请[创建您的项目](program-setup.md)。 创建项目后，Cloud Manager会检测到存储库未设置。 然后，**概述**&#x200B;屏幕上会出现一个特殊的提示卡。

   ![创建项目 CTA](/help/assets/image2018-10-3_14-29-44.png)

1. 单击&#x200B;**创建**&#x200B;以启动向导并提供重要的值。

   * **标题** - 项目的标题。 默认情况下，它会被设置为该程序的名称。
   * **新分支名称** - Git存储库的初始分支。 默认情况下，这是 `main`。

   ![项目值](/help/assets/screen_shot_2018-10-08at55825am.png)

1. 该对话框有一个部分，单击底部附近的图标可显示该部分。 在对话框的展开形式下，将显示 AEM 项目原型的所有配置参数。 这些参数的默认值是根据您已提供的&#x200B;**标题**&#x200B;生成的，无需进行修改。 这里对其进行了解释以供您参考。

   ![详细的原型参数](/help/assets/screen_shot_2018-10-08at60032am.png)

1. 单击&#x200B;**创建**&#x200B;以使用原型创建入门项目并提交到指定的 Git 分支。

您现在已具有基础项目。 您现在可以配置管道。

## 现有或迁移客户 {#existing-migrating}

如果您是正在迁移的当前Adobe Managed Services (AMS)客户或内部部署AEM客户，则Git或其他版本控制系统中已具有项目代码。

在此类情况下，您可以将项目导入 Cloud Manager Git 存储库中。
