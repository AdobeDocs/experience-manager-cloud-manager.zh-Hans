---
title: 代码质量测试
description: 了解管道代码质量测试的工作方式以及其提高部署质量的方式。
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: fadcf560f08bf16d0d18172c620a450d0cb06225
workflow-type: tm+mt
source-wordcount: '2778'
ht-degree: 61%

---


# 代码质量测试 {#code-quality-testing}

了解管道代码质量测试的工作方式以及其提高部署质量的方式。

## 简介 {#introduction}

在管道执行期间，软件会捕获多个量度。 然后，将这些量度与业务负责人定义的关键绩效指标(KPI)进行比较。 或者，可以将它们与AdobeManaged Services设置的标准进行比较。

这些结果使用三层评级系统进行报告。

## 三层评级 {#three-tiered-ratings}

管道中有三项审核：

* 代码质量
* 性能测试
* 安全性测试

对于这三项审核中的每项审核，审核所确定的问题具有一个三层结构。

* **严重** — 导致管道立即失败的问题。
* **重要信息** — 导致管道进入暂停状态的问题。 部署管理员、项目管理员或业务负责人可以覆盖这些问题。 如果是，则管道按计划运行。 或者，他们可以接受问题，从而导致管道因故障而停止。 重要故障的覆盖受[超时](/help/using/code-deployment.md#timeouts)的约束。
* **信息** — 仅供参考并且对管道执行没有影响的问题。

>[!NOTE]
>
>在仅代码质量管道中，无法覆盖代码质量审核中的重要故障，因为代码质量测试步骤是管道中的最后一个步骤。

## 代码质量测试 {#code-quality-testing-step}

此测试步骤评估应用程序代码的质量，这是仅代码质量管道的主要用途。 它紧随所有非生产和生产管道中的构建步骤执行。 要了解更多信息，请转到[配置非生产管道](/help/using/non-production-pipelines.md)。

代码质量测试会扫描源代码以确保它符合特定的质量标准。

软件使用SonarQube分析、OakPAL的内容包级别检查和使用Dispatcher优化工具的Dispatcher验证来组合实现它。

有100多条规则结合了通用Java规则和特定于AEM的规则。 一些特定于 AEM 的规则基于来自 AEM Engineering 的最佳实践而创建，这些规则称作[自定义代码质量规则](/help/using/custom-code-quality-rules.md)。

>[!TIP]
>
>可以[使用此链接](/help/assets/CodeQuality-rules-latest-AMS.xlsx)下载规则的完整列表。

代码质量测试的结果按此表中汇总的评级交付。

| 名称 | 定义 | 类别 | 故障阈值 |
|--- |--- |--- |--- |
| 安全性评级 | A = 无漏洞<br/>B = 至少 1 个次要漏洞<br/>C = 至少 1 个主要漏洞<br/>D = 至少 1 个严重漏洞<br/>E = 至少 1 个阻断漏洞 | 严重 | &lt; B |
| 可靠性评级 | A = 无错误<br/>B = 至少 1 个次要错误<br/>C = 至少 1 个主要错误<br/>D = 至少 1 个严重错误<br/>E = 至少 1 个阻断错误 | 重要 | &lt; C |
| 可维护性评级 | 定义为代码异味的未完成修复成本占应用程序已用时间的百分比<br/><ul><li>A = &lt;=5%</li><li>B = 6-10%</li><li>C = 11-20%</li><li>D = 21-50%</li><li>E = >50%</li></ul> | 重要 | &lt; A |
| 范围 | 在以下公式中结合使用单元测试行覆盖率和条件覆盖率来定义：<br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = 在运行单元测试时已评估为 `true` 至少一次的条件</li><li>`CF` = 在运行单元测试时已评估为 `false` 至少一次的条件</li><li>`LC` = 覆盖的行 = lines_to_cover - uncovered_lines</li><li>`B` = 条件总数</li><li>`EL` = 可执行的行总数 (lines_to_cover)</li></ul> | 重要 | &lt; 50% |
| 跳过的单元测试 | 跳过的单元测试数 | 信息 | > 1 |
| 未结问题 | 整体问题类型 – 漏洞、错误和代码异味 | 信息 | > 0 |
| 重复行 | 定义为重复块中涉及的行数。 在以下条件下，代码块被视为重复。<br>非 Java 项目：<ul><li>应有至少 100 个连续和重复的令牌。</li><li>这些令牌应至少分布在： </li><li>30 个代码行（对于 COBOL） </li><li>20 个代码行（对于 ABAP） </li><li>10 个代码行（对于其他语言）</li></ul>Java 项目：<ul></li><li> 无论令牌和行的数量如何，都应至少有 10 个连续和重复的语句。</li></ul>检测重复项时将忽略缩进和字符串文本的差异。 | 信息 | > 1% |
| Cloud Service 兼容性 | 确定的 Cloud Service 兼容性问题数 | 信息 | > 0 |

>[!NOTE]
>
>有关详细信息，[SonarQube的量度定义](https://docs.sonarsource.com/sonarqube/latest/user-guide/code-metrics/metrics-definition/)。

>[!NOTE]
>
>要了解有关 [!UICONTROL Cloud Manager] 执行的自定义代码质量规则的更多信息，请参阅[自定义代码质量规则文档。](custom-code-quality-rules.md)

### 处理误报 {#dealing-with-false-positives}

质量扫描过程并不完善，有时会错误地识别出实际上并不是问题的问题。 这种情况称为误报。

在这些情况下，可以使用标准 Java `@SuppressWarnings` 注释为源代码添加注释，并将规则 ID 指定为注释属性。例如，一种常见误报是用于检测硬编码密码的 SonarQube 规则可能会妨碍识别硬编码密码的方式。

以下代码在 AEM 项目中相当常见，其中包含用于连接到某些外部服务的代码。

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

然后，SonarQube会引发阻止程序漏洞。 但在查看代码后，您会发现此问题并不是漏洞，并且可以使用适当的规则ID注释代码。

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

但是，如果代码的实际情况如下：

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

那么，正确的解决方案是删除硬编码的密码。

>[!NOTE]
>
>最佳做法是使`@SuppressWarnings`注释尽可能具体。 即，仅注释导致问题的特定语句或块。 但是，可以在类级别进行注释。 这样做可以更广泛地抑制警告。

## 安全性测试 {#security-testing}

[!UICONTROL Cloud Manager] 会在部署后在暂存环境上运行现有的 AEM 安全运行状况检查，并通过 UI 报告状态。结果是由环境中的所有 AEM 实例汇总而成。

可以随时通过 Web 控制台或操作仪表板执行这些相同的运行状况检查。

如果任一实例报告未通过给定的运行状况检查，则整个环境将无法通过此运行状况检查。与代码质量和性能测试一样，这些运行状况检查将分成多个类别并通过三层审核系统进行报告。唯一的区别是，如果有安全测试，则没有阈值。 运行状况检查要么全部通过，要么全部未通过。

下表列出了运行状况检查。

| 名称 | 运行状况检查实施 | 类别 |
|---|---|---|
| 反序列化防火墙连接 API 已准备就绪处于可接受的状态。 | [反序列化防火墙连接 API 已准备就绪](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | 严重 |
| 反序列化防火墙运行正常。 | [反序列化防火墙运行正常](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | 严重 |
| 反序列化防火墙已加载。 | [反序列化防火墙已加载](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | 严重 |
| `AuthorizableNodeName` 实施不会在节点名称/路径中公开可授权 ID。 | [可授权的节点名称生成](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/security/security-checklist#security) | 严重 |
| 默认密码已更改。 | [默认登录帐户](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/security#users-and-groups-in-aem) | 严重 |
| Sling 默认 GET Servlet 可抵御 DOS 攻击。 | Sling Get Servlet | 严重 |
| Sling JavaScript处理程序已正确配置。 | Sling JavaScript处理程序 | 严重 |
| 已适当配置 Sling JSP 脚本处理程序。 | Sling JSP 脚本处理程序 | 严重 |
| 已正确配置 SSL。 | SSL 配置 | 严重 |
| 未找到明显不安全的用户配置文件策略。 | 用户配置文件默认访问 | 严重 |
| Sling引用过滤器配置为阻止CSRF攻击。 | [Sling 引用过滤器](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/security/security-checklist#security) | 重要 |
| 已适当配置 Adobe Granite HTML 库管理器。 | CQ HTML 库管理器配置 | 重要 |
| 已禁用 CRXDE 支持捆绑包。 | CRXDE 支持 | 重要 |
| 已禁用 Sling DavEx 捆绑包和 Servlet。 | DavEx 运行状况检查 | 重要 |
| 未安装示例内容。 | 示例内容包 | 重要 |
| 已禁用 WCM 请求过滤器和 WCM 调试过滤器。 | [WCM 过滤器配置](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/configuring/osgi-configuration-settings#configuring) | 重要 |
| 已适当配置 Sling WebDAV 捆绑包和 Servlet。 | WebDAV 运行状况检查 | 重要 |
| 已配置 Web 服务器来阻止点击劫持攻击。 | Web 服务器配置 | 重要 |
| 复制未使用 `admin` 用户。 | 复制和转移用户 | 信息 |

## 性能测试 {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager 对 AEM Sites 项目执行性能测试。性能测试通过启动虚拟用户（容器）来运行大约 30 分钟，这将模拟实际用户访问暂存环境中的页面来模拟流量。这些页面是使用爬网程序找到的。

#### 虚拟用户 {#virtual-users}

Cloud Manager会根据&#x200B;**业务负责人**&#x200B;角色设置的KPI（响应时间和页面查看次数/分钟）来旋转虚拟用户或容器。 这些KPI是在[创建或编辑项目](/help/getting-started/program-setup.md)时设置的。

根据定义的KPI，将旋转多达10个模拟实际用户的容器。 选择进行测试的页面将被拆分并分配给每个虚拟用户。

#### 爬网程序 {#crawler}

在30分钟的测试期开始之前，Cloud Manager使用客户成功工程师配置的一组种子URL（包含一个或多个种子URL）对暂存环境进行爬网。 从这些 URL 开始，检查每个页面的 HTML，并以广度优先的方式遍历链接。

* 默认情况下，此爬网过程最多可处理 5000 个页面。
* 可以通过设置[管道变量](/help/getting-started/build-environment.md#pipeline-variables)`CM_PERF_TEST_CRAWLER_MAX_PAGES`来覆盖要测试的页面的最大数目。
   * 允许的值为 `2000` - `7000`。
* 来自爬网程序的请求的固定超时为 10 秒。

#### 用于测试的页面集 {#page-sets}

三个页面集选择页面。 Cloud Manager 使用来自生产环境和暂存环境中的 AEM 实例的访问日志来确定以下存储桶。

* **受欢迎实时页面** — 确保对实时客户访问的最受欢迎页面进行测试。 Cloud Manager读取访问日志并确定实时客户最常访问的前25个页面，以生成前`Popular Live Pages`个页面的列表。 随后，在暂存环境中对也出现在暂存环境中的这些页面的交集进行爬网。

* **其他实时页面** — 确保对前25个受欢迎实时页面之外的页面（这些页面可能不受欢迎，但对测试很重要）进行测试。 与受欢迎实时页面类似，这些页面提取自访问日志，并且也必须存在于暂存环境中。

* **新页面** — 测试新页面，这些页面可能仅部署到暂存环境而未部署到生产环境，但必须进行测试。

##### 跨所选页面集的流量分配 {#distribution-of-traffic}

您可以在[管道配置的&#x200B;**测试**&#x200B;选项卡上，从一到三个页面集中选择任一页面集。](/help/using/production-pipelines.md)流量分配基于所选页面集数。也就是说，如果选定所有三个页面集，则每个页面集中都会获得总页面查看次数的33%。 如果选定两个页面集，则每个页面集的查看次数占总页面查看次数的 50%。如果选定一个页面集，则该页面集的查看次数占总页面查看次数的 100%。

我们来看看以下示例。

* 受欢迎实时页面集和新页面集的比例是 50/50。
* 未使用其他实时页面。
* 新页面集包含 3000 个页面。
* 每分钟&#x200B;*的KPI*&#x200B;页面查看次数设置为200。

在 30 分钟的测试期间：

* 受欢迎实时页面集中的25个页面均被点击120次： `((200 * 0.5) / 25) * 30 = 120`
* 新页面集中的3000个页面均被点击一次： `((200 * 0.5) / 3000) * 30 = 1`

#### 测试和报告 {#testing-reporting}

Cloud Manager 通过在暂存发布服务器上以未经身份验证的用户身份（默认情况下）请求页面，来对 AEM Sites 项目执行性能测试，测试期间为 30 分钟。它测量每个页面的虚拟用户生成的量度（响应时间、错误率、每分钟查看次数等），以及所有实例的各种系统级量度（CPU、内存、联网数据）。

下表总结了使用三层审核系统的性能测试矩阵。

| 量度 | 类别 | 故障阈值 |
|---|---|---|
| 页面请求错误率 | 严重 | >= 2% |
| CPU 利用率 | 严重 | >= 80% |
| 磁盘 IO 等待时间 | 严重 | >= 50% |
| 95% 响应时间 | 重要 | >= 项目级 KPI |
| 峰值响应时间 | 重要 | >= 18 秒 |
| 每分钟页面查看次数 | 重要 | &lt; 项目级 KPI |
| 磁盘带宽利用率 | 重要 | >= 90% |
| 网络带宽利用率 | 重要 | >= 90% |
| 每分钟请求数 | 信息 | >= 6000 |

请参阅[经过身份验证的性能测试](#authenticated-performance-testing)部分，了解有关将基本身份验证用于 Sites 和 Assets 的性能测试的更多详细信息。

>[!NOTE]
>
>在测试期间对创作实例和发布实例进行监控。 如果未获得某个实例的任何量度，则该量度将报告为未知，并且对应的步骤将失败。

#### 经过身份验证的性能测试 {#authenticated-performance-testing}

如有必要，拥有经过身份验证的站点的AMS客户可以指定Cloud Manager在站点性能测试期间用于访问网站的用户名和密码。

用户名和密码将指定为名为 `CM_PERF_TEST_BASIC_USERNAME` 和 `CM_PERF_TEST_BASIC_PASSWORD` 的管道变量。

用户名存储在`string`变量中，密码存储在`secretString`变量中。 如果同时指定这两个变量，则来自性能测试爬网程序和测试虚拟用户的每个请求都包含这些凭据作为HTTP基本身份验证。

要使用 Cloud Manager CLI 设置这些变量，请运行：

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

请参阅[修补用户管道变量](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables) API文档，了解如何使用该API。

### AEM Assets {#aem-assets}

Cloud Manager通过反复上传资源30分钟来运行AEM Assets项目的性能测试。

#### 新用户引导要求 {#onboarding-requirement}

对于Assets性能测试，您的客户成功工程师在暂存环境中引导作者期间创建一个`cloudmanager`用户和密码。 性能测试步骤需要一个名为`cloudmanager`的用户和由CSE设置的相关密码。

此方法应保留在创作实例中，其权限保持不变。 更改或删除它可能会导致Assets性能测试失败。

#### 用于测试的图像和资产 {#assets-for-testing}

客户可以上传自己的资产进行测试。此进程可以从&#x200B;**管道设置**&#x200B;或&#x200B;**编辑**&#x200B;屏幕完成。 支持 JPEG、PNG、GIF 和 BMP 等常见图像格式以及 Photoshop、Illustrator 和 Postscript 文件。

如果未上传图像，Cloud Manager将使用默认的图像和PDF文档进行测试。

#### 用于测试的资产的分配 {#distribution-of-assets}

在&#x200B;**管道设置**&#x200B;或&#x200B;**编辑**&#x200B;屏幕中设置每分钟上传的每种类型资产数量。

例如，如果使用70/30拆分，则每分钟上传10个资产，其中包括7个图像和3个文档。

#### 测试和报告 {#testing-and-reporting}

Cloud Manager使用CSE设置的用户名和密码在author实例上创建文件夹。 之后，使用开源库将资产上传到该文件夹中。使用[开源库编写按 Assets 测试步骤运行的测试。](https://github.com/adobe/toughday2)每个资产的处理时间以及各种系统级量度都会在 30 分钟的测试持续时间内测量。此功能可以上传图像和 PDF 文档。

>[!TIP]
>
>请参阅[配置生产管道](/help/using/production-pipelines.md)以了解详情。 请参阅[项目设置](/help/getting-started/program-setup.md)，了解如何设置项目和定义KPI。

### 性能测试结果图表 {#performance-testing-results-graphs}

**“性能测试”对话框**&#x200B;中提供了许多量度

![量度列表](/help/assets/understand_test-results-screen1.png)

可以展开量度面板来显示图表和/或提供下载链接。

![以图表形式展开的量度](/help/assets/screen_shot_2018-09-05at83933pm.png)

此功能适用于以下量度。

* **CPU 利用率** – 测试期间的 CPU 利用率图表

* **磁盘 I/O 等待时间** – 测试期间的磁盘 I/O 等待时间图表

* **页面错误率** – 测试期间的每分钟页面错误图表
   * 一个CSV文件，其中列出了测试期间产生错误的页面

* **磁盘带宽利用率** – 测试期间的磁盘带宽利用率图表

* **网络带宽利用率** – 测试期间的网络带宽利用率图表

* **峰值响应时间** – 测试期间的每分钟峰值响应时间图表

* **第 95 百分位响应时间** – 测试期间的每分钟第 95 百分位响应时间图表
   * 一个 CSV 文件，其中列出响应时间第 95 百分位数超过定义的 KPI 网页

## 内容包扫描优化 {#content-package-scanning-optimization}

在质量分析过程中，Cloud Manager 会对 Maven 构建生成的内容包进行分析。 Cloud Manager提供了优化功能以加速此过程，当遵守某些打包限制时，优化功能将生效。

关键优化适用于输出单个“所有”包的项目，其中包含构建生成的其他内容包（这些内容包标记为已跳过）。 当 Cloud Manager 检测到此情况时，它不会解压缩“所有”包，而是直接扫描各个内容包并根据依赖关系对它们进行排序。 例如，考虑以下构建输出。

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

如果 `myco-all-1.0.0-SNAPSHOT.zip` 中的唯一项目是两个跳过的内容包，则会扫描两个嵌入包而不是“所有”内容包。

对于产生数十个嵌入包的项目，此优化已被证明可将每次管道执行时间节省 10 分钟以上。

当“所有”内容包包含跳过的内容包和 OSGi 捆绑包的组合时，可能会出现特殊情况。 例如，如果 `myco-all-1.0.0-SNAPSHOT.zip` 包含前面提到的两个嵌入式包以及一个或多个 OSGi 捆绑包，则仅使用 OSGi 捆绑包构建一个新的最小内容包。 此包始终名为 `cloudmanager-synthetic-jar-package`，并且包含的捆绑包将放置在 `/apps/cloudmanager-synthetic-installer/install` 中。

>[!NOTE]
>
>* 此优化不会影响部署到AEM的包。
>* 嵌入和跳过的内容包之间的匹配基于文件名。 如果多个跳过的内容包共享相同的文件名，或者文件名在嵌入期间发生更改，则此优化会失败。
