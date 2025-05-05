---
title: 监控环境
description: 了解如何在 Cloud Manager 中监控环境。
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 53fb666ab6caff7a697d7f1942ce25f2bf27a2ce
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 98%

---


# 监控环境 {#monitoring-environments}

了解如何在 Cloud Manager 中监控环境。

## 量度阈值 {#thresholds}

在 [!UICONTROL Cloud Manager] 中，通过观察环境中的各个实例并跟踪每个实例的各种量度来监控系统。 每个量度都有两个定义的阈值：*警告*&#x200B;阈值和&#x200B;*关键*&#x200B;阈值。

如果量度超过其警告阈值（但低于其关键阈值），则将被视为处于警告状态。

如果量度超过其关键阈值，则将被视为处于关键状态。

Adobe Managed Services 会设置阈值，而您可以在 [!UICONTROL Cloud Manager] 中查看这些阈值。 在大多数情况下，客户之间的阈值是一致的，但在某些情况下，Adobe Managed Services 会修改阈值以匹配特定的客户要求。请向您的客户成功工程师 (CSE) 咨询任何有关阈值的问题。

## 访问系统监控功能 {#accessing-system-monitoring}

1. 在 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 上登录到 Cloud Manager 并选择适当的组织和项目。

1. 单击要监视的程序的![更多图标，省略号](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)。
1. 在菜单中，在&#x200B;**管理**&#x200B;标题下，单击&#x200B;**显示监控**，以打开显示系统监控信息的&#x200B;**报告**&#x200B;页面。

   ![设置](/help/assets/first-timea1.png)

。

## 系统监控概述 {#system-monitoring-overview}

**报告**&#x200B;页面的&#x200B;**系统监控**&#x200B;部分列出了程序中受监控的环境。它通过以下四个不同的类别报告了它们的高级健康状况：

* 主机
* 存储
* 网络
* 应用程序

每个类别中的状态均为各个量度的摘要。如果某个类别中的任意量度处于关键状态，则对于概述页面而言，整个类别都处于关键状态。 可以在环境级别和实例级别查看同一摘要。

![系统监控概述](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>默认情况下，在导航到此页面时，生产环境实例是可见的，也可以查看其他环境。

## 系统监控详细信息 {#system-monitoring-detail}

要查看特定量度的详细信息，请单击特定实例的其中一个类别列或左侧导航中的类别标题。每个详细信息页面均显示该类别中量度的一系列图表。您可以查看环境中所有实例或某个特定实例的量度。您可以使用右上角的下拉框在环境和实例之间切换。

![选择环境](/help/assets/System_Monitoring1.png)

左侧导航显示当前所选类别中的可用量度，其中包含当前所选环境和实例的数据。

状态和一段时间内的数据图形以及阈值会在单个图形中显示。 如果显示多个实例，则每个实例的数据都会位于一个单独的系列中。

![量度图表](/help/assets/Monitoring_Graphs1.png)

通过单击图例中的系列，可以在图表上隐藏该系列。例如，如果您单击警告阈值系列，则您只会看到关键阈值。

![修改图表](/help/assets/Monitoring_Graphs2.png)

### 量度定义 {#metric-definitions}

#### 主机 {#host}

* **每个核心的负载**：CPU 正在执行的进程数。 或者，一分钟（load1）、五分钟（load5）和十五分钟（load15）时间内处于等待状态的排队进程数的平均值。
* **进程计数**：当前打开的进程数。
* **用户计数**：具有活动 shell 会话的用户的数量。
* **内存使用**：当前分配的系统内存的百分比。
* **JVM 内存**：分配的 Java 堆的大小（以 MB 为单位）。
* **旧一代空间**：当前分配的 JVM 旧一代内存的百分比。

#### 网络 {#network}

* **CQ 端口检查**：访问 AEM 或 Dispatcher 端口的响应时间（以秒为单位）。创作、发布和 Dispatcher 具有不同的量度。

#### 存储 {#storage}

* **磁盘空间**：主机上每个挂载点的已用磁盘空间（以 MB 为单位）。 每个挂载点具有不同的量度。 至少有 `/` 和 `/mnt` 的量度，但根据具体的实例配置，可能会提供额外的挂载点量度。
* **文件夹大小**
* **AEM 区段存储**：AEM 区段存储的已用磁盘空间（以 GB 为单位）。

#### 应用程序 {#application}

* **复制代理**：测试复制事件所用的时间（以秒为单位）
   * 每个复制代理均具有单独的量度。
* **Dispatcher 刷新**：当前位于 Dispatcher 刷新队列中的项目数

## SLA 报告 {#sla-reporting}

您可以查看生产 AEM 环境相对于约定的服务水平协议 (SLA) 的性能。

以下图表显示了 2019 年的月度 SLA 达到情况。

![SLA 2018 图表](/help/assets/SLA-Reports-one.png)

与使用系统监控图表时一样，滚存数据点可显示该月的具体值。

![数据点滚存](/help/assets/SLA-Reports-two.png)

此图表下的&#x200B;**事件分析**&#x200B;部分显示在当前选定年份中发生的与项目相关的事件集。 每个事件均具有一个时间范围、一个原因和一组注释。

![事件分析](/help/assets/sla-reporting3.png)

## SLA 量度 {#sla-metrics}

* **作者合同**：您与 Adobe Managed Services 签订的合同中为创作层定义的 SLA。
* **AMS 作者 SLA**：测量出的生产作者层的正常运行时间，其中考虑了供应商或 Adobe 引起的事故。
* **作者 SLA**：测量出的作者层的正常运行时间，其中忽略了计划的停机时间，例如维护时段。
* **最终用户合同**：您与 Adobe Managed Services 签订的合同中为发布层定义的 SLA。
* **AMS 最终用户 SLA**：测量出的生产发布层的正常运行时间，其中考虑了由供应商或 Adobe 引起的事故。
* **最终用户 SLA**：测量出的发布层的正常运行时间，其中忽略了计划的停机时间，例如维护时段。

## 视频教程 {#video-tutorial}

本视频概述如何使用 Cloud Manager 报告生成的图表来查看项目环境。

>[!VIDEO](https://video.tv.adobe.com/v/34273?captions=chi_hans)
