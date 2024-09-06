---
title: 使用新项目向导
description: 关注此页面，了解如何使用该向导创建 AEM 应用程序项目
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '321'
ht-degree: 100%

---


# 使用新项目向导 {#using-the-wizard}

当您以新客户身份登记到 Cloud Manager 时，将会为您提供一个空的 Git 存储库。 为了帮助您入门，Cloud Manger 提供了一个向导，可让您根据 [AEM 项目原型](https://github.com/adobe/aem-project-archetype)创建最小 AEM 项目作为起点。

执行以下步骤，使用该向导创建 AEM 项目。

1. 在 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 中登录 Cloud Manager 并选择适当的组织。

1. 如果您尚未这样做，请[创建您的项目](program-setup.md)。创建程序时，Cloud Manager 检测到存储库尚未设置。 然后，一张特殊的行动号召信息卡会在&#x200B;**概述**&#x200B;屏幕中出现。

   ![创建项目 CTA](/help/assets/image2018-10-3_14-29-44.png)

1. 单击&#x200B;**创建**&#x200B;以启动向导并提供重要的值。

   * **标题** - 项目的标题。 默认情况下，它会被设置为该程序的名称。
   * **新分支名称** - 您的 Git 存储库的初始分支。默认情况下，这是 `main`。

   ![项目值](/help/assets/screen_shot_2018-10-08at55825am.png)

1. 该对话框有一个抽屉，可以通过单击底部的图柄来打开它。 在对话框的展开形式下，将显示 AEM 项目原型的所有配置参数。这些参数的默认值是根据您已提供的&#x200B;**标题**&#x200B;生成的，无需进行修改。这里对其进行了解释以供您参考。

   ![详细的原型参数](/help/assets/screen_shot_2018-10-08at60032am.png)

1. 单击&#x200B;**创建**&#x200B;以使用原型创建入门项目并提交到指定的 Git 分支。

您现在已具有基础项目。现在请设置您的管道。

## 现有或迁移客户 {#existing-migrating}

如果您是现任 Adobe Managed Services (AMS) 客户或要迁移到 AMS 的内部部署 AEM 客户，则您可能已在 Git 或其他版本控制系统中拥有项目代码。

在此类情况下，您可以将项目导入 Cloud Manager Git 存储库中。
