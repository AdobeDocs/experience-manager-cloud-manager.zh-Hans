---
title: 开发环境的服务包更新 - 早期采用者
description: 了解如何通过 Cloud Manager 用户界面启动开发环境的服务包更新。
hide: true
hidefromtoc: true
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: 55b33db1bf80f066b1a66bc87c0abeefa4771871
workflow-type: ht
source-wordcount: '453'
ht-degree: 100%

---

# 开发环境的服务包更新（早期采用者） {#stage-prod-only}

了解如何通过 Cloud Manager 用户界面启动开发环境的服务包更新。

>[!NOTE]
>
>此功能仅适用于[早期采用者计划](/help/release-notes/current.md#early-adoption)。

## 概述 {#service-pack-updates-overview}

您可以通过 Cloud Manager 用户界面启动开发环境的服务包更新。此功能可让您检查可用的服务包更新并独立管理安装过程。

**主要优点** 

* 更好地控制 Cloud Manager 服务包更新。
* 减少在启动更新中对 Adobe 客户成功工程师 (CSE) 的依赖。
* 通过 Cloud Manager 跟踪整个更新过程。

**当前限制**

* 自助更新选项仅适用于开发环境。
* 可提供关于更新失败的有限的错误报告。
* 如果出现问题，您必须联系 Adobe CSE 进一步调查。

## 启动服务包更新

1. 使用部署管理员权限登录 Cloud Manager。
1. 导航至程序概述页面。
1. 在“环境”部分，点击![“更多”图标（省略号）](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)。

   ![在下拉菜单中查看服务包更新](/help/using/assets/service-pack-check-for-updates.png)

1. 在下拉菜单中点击![通过灯泡图标打开](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **检查更新**，寻找可用的服务包更新。

   ![现在会打开一个可用更新的列表](/help/using/assets/service-pack-versions.png)

1. 在列表中点击所需的服务包版本。
1. 点击&#x200B;**更新服务包**，开始更新过程。
1. 在确认对话框中查看详细信息并确认更新。

   确认后，安装过程就会开始，可以在 Cloud Manager 中跟踪进度。

## 跟踪服务包更新

启动更新后，您可以在 Cloud Manager 的活动页面中监控进度。

**如要跟踪服务包更新：**

1. 从 Cloud Manager 仪表板导航到活动页面。
1. 查找服务包安装条目。

   ![服务包安装](/help/using/assets/service-pack-installation.png)

1. 点击该条目可以查看类似以下内容的详细进度和状态更新：

   ![服务包安装进度](/help/using/assets/service-pack-progression.png)

### 解决安装失败问题

* 如果安装失败，Cloud Manager 会自动触发回滚到以前的状态。
* 如果问题仍然存在，点击&#x200B;**下载日志**，收集错误日志，然后联系 Adobe 支持部门解决问题。

## 批准或拒绝服务包执行

安装完成后，需要您的批准或拒绝才能最终完成更新。

**如要批准或拒绝服务包执行：**

1. 在 Cloud Manager 中打开活动页面。
1. 找到该服务包更新的待处理批准请求。

   ![拒绝或批准服务包更新](/help/using/assets/service-pack-reject-approve.png)

1. 执行以下任一操作：

   * 要最终完成更新，点击&#x200B;**批准**。

   ![批准服务包](/help/using/assets/service-pack-approve.png)

   * 要取消更新，点击&#x200B;**拒绝**。
服务包安装被取消，不做任何更改。

   ![拒绝服务包](/help/using/assets/service-pack-reject.png)
