---
title: 使用“新建项目”向导
description: 关注此页面，了解如何使用该向导创建 AEM 应用程序项目
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 36%

---


# 使用“新建项目”向导 {#using-the-wizard}

当您以新客户身份登记到Cloud Manager时，将为您提供一个空的Git存储库。 为了帮助您入门，Cloud Manger 提供了一个向导，可让您根据 [AEM 项目原型](https://github.com/adobe/aem-project-archetype)创建最小 AEM 项目作为起点。

执行以下步骤，使用该向导创建 AEM 项目。

1. 在 [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) 中登录 Cloud Manager 并选择适当的组织。

1. 如果您尚未这样做，请[创建您的项目](program-setup.md)。创建项目后，Cloud Manager会检测到尚未设置存储库。 然后，**概述**&#x200B;屏幕上会显示一个特殊的行动号召信息卡。

   ![创建项目 CTA](/help/assets/image2018-10-3_14-29-44.png)

1. 单击&#x200B;**创建**&#x200B;以启动向导并提供重要的值。

   * **标题** — 项目的标题。 默认情况下，它被设置为项目的名称。
   * **新分支名称** - Git存储库的初始分支。 默认情况下，该值为`main`。

   ![项目值](/help/assets/screen_shot_2018-10-08at55825am.png)

1. 该对话框有一个抽屉，可以通过单击底部的图柄来打开它。 在其展开形式中，该对话框显示AEM项目原型的所有配置参数。 这些参数的默认值是根据您已提供的&#x200B;**标题**&#x200B;生成的，无需修改。 这里对其进行了解释以供您参考。

   ![详细的原型参数](/help/assets/screen_shot_2018-10-08at60032am.png)

1. 单击&#x200B;**创建**&#x200B;以使用原型创建入门项目并提交到指定的 Git 分支。

您现在已拥有基础项目。 是时候设置您的管道了。

## 现有或迁移的客户 {#existing-migrating}

如果您是当前Adobe的Managed Services (AMS)客户或要迁移到的内部部署AEM客户，则您可能已在Git或其他版本控制系统中拥有项目代码。

在这种情况下，您可以将项目导入Cloud Manager Git存储库。
