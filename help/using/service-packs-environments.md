---
title: 开发环境的Service Pack更新 — 早期采用者
description: 了解如何现在通过Cloud Manager用户界面启动开发环境的Service Pack更新。
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: 91691878a2c135cc9fe123c06afcf775a962a2e0
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---

# 开发环境的Service Pack更新（早期采用者） {#stage-prod-only}

了解如何通过Cloud Manager用户界面启动开发环境的Service Pack更新。

>[!NOTE]
>
>此功能仅适用于[早期采用者计划](/help/release-notes/current.md#early-adoption)。

## 概述 {#service-pack-updates-overview}

您可以通过Cloud Manager用户界面启动开发环境的Service Pack更新。 此功能允许您检查可用的Service Pack更新，并独立管理安装过程。

**主要优势**

* 更好地控制Cloud Manager Service Pack更新。
* 减少在启动更新时依赖于Adobe客户成功工程师(CSE)。
* 通过Cloud Manager跟踪整个更新过程。

**当前限制**

* 自助更新选项仅适用于开发环境。
* 有限错误报告可用于失败的更新。
* 如果出现问题，您必须联系Adobe CSE以进一步调查。

## 启动Service Pack更新

1. 使用部署管理器权限登录到Cloud Manager。
1. 导航到项目概述页面。
1. 在“环境”部分下，单击![更多图标，省略号](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)。

   ![在下拉菜单中检查Service Pack更新](/help/using/assets/service-pack-check-for-updates.png)

1. 从下拉菜单中，单击![在指示灯图标中打开](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **检查更新**&#x200B;以扫描可用的Service Pack更新。

   ![显示可用更新的列表](/help/using/assets/service-pack-versions.png)

1. 从列表中单击所需的Service Pack版本。
1. 单击&#x200B;**更新Service Pack**&#x200B;开始更新过程。
1. 在确认对话框中，查看详细信息并确认更新。

   确认后，安装过程将开始，并且可以在Cloud Manager中跟踪进度。

## 跟踪Service Pack更新

启动更新后，您可以在Cloud Manager的“活动”页面中监控进度。

**要跟踪Service Pack更新：**

1. 从Cloud Manager仪表板导航到活动页面。
1. 查找Service Pack安装条目。

   ![服务包安装](/help/using/assets/service-pack-installation.png)

1. 单击该条目可查看详细的进度和状态更新，如下所示：

   ![Service Pack安装进度](/help/using/assets/service-pack-progression.png)

### 安装故障疑难解答

* 如果安装失败，Cloud Manager会自动触发回滚到以前的状态。
* 如果问题仍然存在，请单击&#x200B;**下载日志**&#x200B;以收集错误日志，然后与Adobe支持部门联系以进行故障排除。

## 批准或拒绝服务包执行

安装完成后，需要您批准或拒绝才能完成更新。

**要批准或拒绝服务包执行：**

1. 在Cloud Manager中打开“活动”页面。
1. 找到Service Pack更新的未决批准请求。

   ![拒绝或批准Service Pack更新](/help/using/assets/service-pack-reject-approve.png)

1. 执行以下任一操作：

   * 要完成更新，请单击&#x200B;**批准**。

   ![审批Service Pack](/help/using/assets/service-pack-approve.png)

   * 要取消更新，请单击&#x200B;**拒绝**。
Service Pack安装已取消，并且不应用任何更改。

   ![拒绝Service Pack](/help/using/assets/service-pack-reject.png)
