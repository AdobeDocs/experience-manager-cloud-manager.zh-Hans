---
title: 代码部署
description: 了解如何部署代码以及在部署代码时 Cloud Manager 中会发生什么情况。
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: a7dc30ed31e87ab486f0b279b70c850a33a903eb
workflow-type: tm+mt
source-wordcount: '1637'
ht-degree: 58%

---


# 代码部署 {#code-deployment}

了解如何部署代码以及在部署代码时 Cloud Manager 中会发生什么情况。

## 使用 Cloud Manager 部署代码 {#deploying-code-with-cloud-manager}

配置生产管道（包括必要的存储库和环境）后，便可以部署代码。

1. 单击 Cloud Manager 中的&#x200B;**部署**&#x200B;开始部署过程。

   ![“部署”按钮](/help/assets/Deploy1.png)

1. 此时将显示&#x200B;**管道执行**&#x200B;屏幕。单击&#x200B;**构建**&#x200B;开始此流程。

   ![“构建”按钮](/help/assets/Deploy2.png)

构建过程会启动代码部署过程，包括以下步骤：

* 暂存部署
* 暂存测试
* 生产部署

您可以通过查看日志或根据测试标准审查结果来审查各种部署过程的步骤。

## 部署步骤 {#deployment-steps}

在部署的每个步骤中都会执行大量操作，本节将对此进行介绍。 有关如何在幕后部署代码本身的技术详细信息，请参阅[部署进程详细信息](#deployment-process)。

### 暂存部署步骤 {#stage-deployment}

**暂存部署**&#x200B;步骤包含以下操作：

* **验证**：此步骤可确保将管道配置为使用当前可用的资源。 例如，存在已配置的分支并且环境可用。
* **构建和单元测试**：此步骤运行容器化的构建过程。有关详细信息，请参阅[生成环境](/help/getting-started/build-environment.md)。
* **代码扫描**：此步骤评估应用程序代码的质量。有关测试过程的详细信息，请参阅[了解测试结果](/help/using/code-quality-testing.md)。
* **部署到暂存**

![暂存部署](/help/assets/Stage_Deployment1.png)

### 暂存测试步骤 {#stage-testing}

**暂存测试**&#x200B;步骤包含以下操作：

* **安全性测试**：此步骤评估代码对 AEM 环境产生的安全影响。有关测试过程的详细信息，请参阅[了解测试结果](/help/using/code-quality-testing.md)文档。
   * **性能测试**：此步骤评估代码的性能。有关测试过程的详细信息，请参阅[了解测试结果](/help/using/code-quality-testing.md)。

### 生产部署步骤 {#production-deployment}

**生产部署**&#x200B;步骤包含以下操作：

* **申请审批**
   * 配置管道时将启用此选项。
   * 利用此选项，您可以计划生产部署，也可以单击&#x200B;**立即**&#x200B;来立即执行生产部署。
* **计划生产部署**
   * 配置管道时将启用此选项。
   * 计划的日期和时间根据用户的时区指定。
     ![计划部署](/help/assets/Production_Deployment1.png)
* **CSE 支持**（如果已启用）
* **部署到生产**

![生产部署](/help/assets/Prod_Deployment1.png)

部署完成后，代码将位于其目标环境中，并且您可以查看日志。

![部署完成](/help/assets/Production_Deployment2.png)

## 超时 {#timeouts}

如果继续等待用户反馈，则以下步骤将超时：

| 步骤 | 超时 |
|--- |--- |
| 代码质量测试 | 7 天 |
| 安全性测试 | 7 天 |
| 性能测试 | 7 天 |
| 申请审批（暂存） | 7 天 |
| 申请审批（生产） | 14 天 |
| 计划生产部署 | 14 天 |
| 托管的生产部署 | 14 天 |

## 部署过程详细信息 {#deployment-process}

Cloud Manager 将构建过程生成的所有 target/*.zip 文件上传到存储位置。在管道的部署阶段，将从该位置检索这些工件。

当 Cloud Manager 部署到非生产拓扑时，目标是尽快完成部署，因此，工件将同时部署到所有节点，如下所示：

1. Cloud Manager确定每个工件是AEM还是Dispatcher包。
1. Cloud Manager 会从负载平衡器中移除所有 Dispatcher，以在部署期间隔离环境。

   * 除非另有配置，否则您可以跳过开发和暂存部署中的负载平衡器更改。 即，对于开发环境，分离和附加非生产管道中的步骤；对于暂存环境，分离和附加生产管道中的步骤。

   ![跳过负载平衡器](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >预计1-1-1客户将使用此功能。

1. 每个 AEM 工件均通过包管理器 API 部署到每个 AEM 实例，其中包依赖关系将确定部署顺序。

   * 详细了解如何使用包安装新功能、在实例之间传输内容以及备份存储库内容。 请参阅[包管理器](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager)。

   >[!NOTE]
   >
   >所有 AEM 工件都会部署供作者和发布者使用。在需要特定于节点的配置时，应利用运行模式。要了解有关运行模式如何允许您针对特定目的调整 AEM 实例的更多信息，请参阅[“部署到 AEM as a Cloud Service”文档的“运行模式”部分](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/implementing/deploying/overview#runmodes)。

1. Dispatcher工件将部署到每个Dispatcher，如下所示：

   1. 当前配置已备份并复制到临时位置。
   1. 已删除所有配置（不可变文件除外）。有关更多详细信息，请参阅 [Dispatcher 配置](/help/getting-started/dispatcher-configurations.md)。此方法会清除目录，以确保没有留下孤立文件。
   1. 工件将提取到 `httpd` 目录。不会覆盖不可变文件。在部署时，将忽略您对Git存储库中的不可变文件所做的任何更改。 这些文件是AMS Dispatcher Framework的核心，无法更改。
   1. Apache 执行配置测试。如果未发现任何错误，则将重新加载服务。如果发生错误，则从备份中恢复配置，重新加载服务，并将错误报告回 Cloud Manager。
   1. 管道配置中指定的每个路径都将失效或从Dispatcher缓存中进行刷新。

   >[!NOTE]
   >
   >Cloud Manager希望Dispatcher工件包含完整文件集。 所有Dispatcher配置文件都必须在Git存储库中。 缺少文件或文件夹会导致部署失败。

1. 成功将所有AEM和Dispatcher包部署到所有节点后，调度程序将添加回负载平衡器，并完成部署。

   >[!NOTE]
   >
   >您可以跳过开发和暂存部署中的负载平衡器更改。 即，对于开发环境，分离和附加非生产管道中的步骤；对于暂存环境，分离和附加生产管道。

### 部署到生产阶段 {#deployment-production-phase}

部署到生产拓扑的过程略有不同，旨在尽量减小对AEM网站访客的影响。

生产部署通常遵循与上述相同的步骤，但它采用的是滚动方式：

1. 将 AEM 包部署到作者。
1. 从负载平衡器分离 dispatcher1。
1. 以并行方式将AEM包部署到publish1，并将Dispatcher包部署到dispatcher1，同时刷新Dispatcher缓存。
1. 将 dispatcher1 放回负载平衡器中。
1. 在将 dispatcher1 重新投入使用后，就会从负载平衡器中分离 dispatcher2。
1. 以并行方式将AEM包部署到publish2，并将Dispatcher包部署到dispatcher2，同时刷新Dispatcher缓存。
1. 将 dispatcher2 放回负载平衡器中。

此过程将持续进行，直到部署到达拓扑中的所有发布者和 Dispatcher 为止。

## 紧急管道执行模式 {#emergency-pipeline}

在关键情况下，AdobeManaged Services客户可能需要立即将代码更改部署到其暂存环境和生产环境。 这项功能可以让客户绕过整个Cloud Manager测试周期。

为了处理这些情况，可以在紧急模式下执行 Cloud Manager 生产管道。在使用此模式时，不执行安全性测试和性能测试步骤。所有其他步骤（包括任何已配置的审批步骤）都会像在正常管道执行模式中那样执行。

>[!NOTE]
>
>紧急管道执行模式功能基于逐个程序被激活。 激活由客户成功工程师完成。

### 使用紧急管道执行模式 {#using-emergency-pipeline}

在启动生产管道执行时，您可以从对话框中选择正常模式或紧急模式。 如果为项目激活了紧急管道执行模式功能，则此选项可用。 启用该功能后，即可使用此选项。

![运行管道选项](/help/assets/execution-emergency1.png)

在查看紧急模式下的执行运行的管道执行详细信息页面时，屏幕顶部的痕迹导航会显示一个指示器，指明管道正在紧急模式下执行。

![紧急模式痕迹导航](/help/assets/execution-emergency2.png)

要在紧急模式下执行管道，也可以通过 Cloud Manager API 或 CLI 实现。要在紧急模式下启动执行，请使用查询参数 `?pipelineExecutionMode=EMERGENCY` 或在使用 CLI 时将 `PUT` 请求提交到管道的执行端点：

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## 重新执行生产部署 {#reexecute-deployment}

在罕见的情况下，生产部署步骤可能会因短暂的原因而失败。在这些情况下，只要生产部署步骤已完成，您就可以重新执行该步骤，而不管该步骤是成功、取消还是不成功。 使用包含以下三个步骤的同一管道支持重新执行：

1. **验证步骤** — 与正常管道执行期间发生的验证相同。
1. **构建步骤** - 在重新执行的上下文中，构建步骤复制工件，但实际上并不执行新的构建过程。
1. **生产部署步骤** — 使用与正常管道执行中的生产部署步骤相同的配置和选项。

在此类能够重新执行的情况下，生产管道状态页面在平常的&#x200B;**下载构建日志**&#x200B;选项旁提供&#x200B;**重新执行**&#x200B;选项。

![管道概述窗口中的“重新执行”选项](/help/assets/re-execute.png)

>[!NOTE]
>
>在重新执行中，在 UI 中为构建步骤加上标签以反映它复制工件而非重新构建。

### 限制 {#limitations}

* 生产部署步骤的重新执行仅适用于上一次执行。
* 重新执行不适用于回滚执行或“推送更新”执行。
* 如果上一次执行在生产部署步骤前的任何时间点失败，则无法重新执行。


### 重新执行 API {#reexecute-api}

除了在 UI 中可用之外，您还可以使用 [Cloud Manager API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) 触发重新执行以及标识已作为重新执行触发的执行。

#### 触发重新执行 {#triggering}

要触发重新执行，需要对生产部署步骤状态的 HAL 链接 `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` 作出 `PUT` 请求。

* 如果存在此链接，则可以从该步骤重新开始执行。
* 如果此链接不存在，则无法从该步骤重新开始执行。

此链接仅适用于生产部署步骤。

```javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

HAL 链接的 `href` 值的语法只是一个示例，应始终从 HAL 链接读取而不是生成实际值。

将`PUT`请求提交到此终结点会导致`201`响应（如果成功）。 响应正文是新执行的表示形式。 此功能类似于通过API开始常规执行。

#### 识别重新执行的执行 {#identifying}

系统通过触发器字段中的值`RE_EXECUTE`识别重新执行的执行。