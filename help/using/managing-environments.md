---
title: 管理环境
description: 了解如何使用 Cloud Manager 管理环境。
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
TQID: https://experienceleague.adobe.com/Dz3Z5i-gSNSorc7Na74RKgm3e0P9b-3vjVRdJvu6a0c
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 0dde660205ad28bc5924a5cc14404c48a0533ceb
workflow-type: tm+mt
source-wordcount: 261
ht-degree: 57%

---

# 管理环境 {#managing-environments}

了解如何使用 Cloud Manager 管理环境。

## “概述”页面 {#overview-page}

Cloud Manager 的&#x200B;**概述**&#x200B;页面包含&#x200B;**环境**&#x200B;图块，它列出了所有托管的 AEM 环境。

每个列出的环境都会显示其关联状态。

![“概述”页面](/help/assets/Manage-Environ-Overview.png)

## “环境”图块 {#environments-tile}

**环境**&#x200B;图块显示项目中配置的生产和暂存环境以及状态。

状态是按顺序列出的环境节点中的聚合电源状态。

* 绿色 – 所有节点都正在运行。
* 红色 — 一个或多个节点已停止。
* 蓝色 — 一个或多个节点正在启动。
* 黄色 — 一个或多个节点的电源状态为不可用。

![“环境”图块](/help/assets/Environments-card-new.png)

## 管理环境 {#managing-environments-with-cloud-manager}

在&#x200B;**环境**&#x200B;磁贴上，单击任意环境的行可显示&#x200B;**环境**&#x200B;屏幕。

**环境**&#x200B;屏幕显示项目中的每个生产和暂存环境。 环境名称显示在每张信息卡的上方。 该信息卡包括环境中的节点表以及CPU的大小、存储、区域和状态。

>[!NOTE]
>
>节点的&#x200B;**状态**&#x200B;表示 VM 的电源状态，而不会反映服务器上 AEM 的状态。 状态可以是：

* 绿色 – 正在运行
* 红色 – 已停止
* 蓝色 — 正在启动
* 黄色 – 不可用

![“环境”信息卡](/help/assets/Environments-tab.png)

>[!NOTE]
>
>一旦配置完成，环境详细信息（例如名称）就无法更改。

>[!NOTE]
>
>通过客户成功代表请求环境日志。

## 视频教程 {#video-tutorial}

本视频介绍了由Cloud Manager创作、发布和AEM实例组成的Dispatcher环境。

>[!VIDEO](https://video.tv.adobe.com/v/34270?captions=chi_hans)

*（3 分钟，1 秒钟）*
