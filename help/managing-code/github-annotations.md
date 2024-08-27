---
title: GitHub 检查批注
description: 了解GitHub如何检查专用存储库的PR注释，以向您提供有用的反馈。
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 6f5d51ef59aef831574bd55cee6b12a29e3d70d2
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 47%

---


# GitHub检查注释 {#github-annotations}

了解GitHub如何检查专用存储库的PR注释，以向您提供有用的反馈。

## 概述 {#overview}

如果您为Cloud Manager项目使用[专用存储库](private-repositories.md)，则每个拉取请求都会自动运行GitHub签入。 这些检查带有有用信息的注释，可帮助您尽快了解代码的任何问题。

![GitHub 检查批注的示例](assets/github-check-annotations.png)

[代码质量](/help/using/code-quality-testing.md)检测到的问题 [SonarQube](/help/using/custom-code-quality-rules.md) 都清晰列出。

![代码问题批注示例](assets/github-check-annotations-example.png)

提供了存在问题的确切代码行，您可以单击该行显示相关代码。这些注释适用于所有代码问题，而不仅仅是拉取请求中更改的那些问题。

![代码问题批注示例](assets/github-check-annotations-example-code.png)

所有带批注的行都汇总在&#x200B;**已更改文件** GitHub 拉取请求上的选项卡。拉取请求中未更改文件的批注出现在其自己的部分中。

![文件更改选项卡上的批注示例](assets/github-check-annotations-files-changed.png)

## 代码质量管道 {#code-quality-pipelines}

[代码质量](/help/using/code-quality-testing.md)结果也显示在管道中，Cloud Manager将在&#x200B;**检查**&#x200B;选项卡的底部自动触发该管道。 也可以从&#x200B;**详细信息**&#x200B;对拉取请求进行检查。

![批注示例](assets/github-check-annotations-code-quality.png)

![批注示例](assets/github-check-annotations-code-quality-2.png)

您还可以以 CSV 的形式将问题可视化。可通过[查看Cloud Manager](/help/using/managing-pipelines.md)中管道执行的详细信息来检索此方法。
