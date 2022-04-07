---
title: 2021.12.0 版发行说明
description: 以下是Cloud Manager版本2021.12.0的发行说明。
feature: Release Information
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---

# Cloud Manager版本2021.12.0的发行说明 {#release-notes}

以下部分概述了 [!UICONTROL Cloud Manager] 版本2021.12.0。

>[!NOTE]
>
>有关AEMas a Cloud Service中Cloud Manager的最新发行说明，请参阅 [AEM Manager的最新发行说明](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## 发布日期 {#release-date}

的发行日期 [!UICONTROL Cloud Manager] 2021.12.0版于2021年12月16日发布。 下一版本计划于2022年1月发布。

## 新增功能 {#whats-new}

* 提交哈希（已在UI中可见）现在也在API中提供。
* “活动”页面现在包含一个用于运行管道的弹出窗口，该弹出窗口提供了管道详细信息概览摘要。
* 添加了更新，以包含“活动”页面中显示的其他详细信息。
* Cloud Manager中的“学习”选项卡现在包含对API指南和相关资源的快速访问。
* 现在，具有部署管理器角色的用户可以从“存储库”页面的“操作”菜单中为没有分支的存储库启动项目/分支创建向导。
* 现在，将通知处于添加或编辑管道工作流中的部署管理器在选定的存储库没有分支时如何创建分支或项目。
* 在“编辑生产管道”窗口中，如果生产存在多个阶段环境，则可以使用用于环境选择的下拉列表。
* Cloud Manager使用的AEM项目原型版本已更新至版本32。

## 错误修复 {#bug-fixes}

* 即使用户在名称字段中输入不同的名称，完整堆栈生产管道仍将保留为“生产管道”。