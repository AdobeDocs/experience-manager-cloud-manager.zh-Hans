---
title: 在 Cloud Manager 中添加 Adobe 存储库
description: 了解如何在 Cloud Manager 中添加 Adobe 管理的存储库。
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
TQID: https://experienceleague.adobe.com/LBI6V07enOlxe8yh-XwlkL-mdMWR0MJyKi1gUQtjtK4
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 036302d4861b59e783ac731da12078be59cdc5c4
workflow-type: tm+mt
source-wordcount: 225
ht-degree: 69%

---

# 在 Cloud Manager 中添加 Adobe 存储库 {#adobe-repositories}

了解如何在 Cloud Manager 中添加 Adobe 管理的存储库。

通过&#x200B;**存储库**&#x200B;页面，可向所选项目添加其他Adobe管理的存储库。

**在 Cloud Manager 中添加 Adobe 存储库：**

1. 在[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)上登录到 Cloud Manager，然后选择适当的组织以及您想要添加 Adobe 管理存储库的程序。

1. 在&#x200B;**项目概述**&#x200B;页面的侧菜单中，单击![文件夹图标](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **存储库**&#x200B;选项卡。

1. 在 **存储库** 页面的右上角附近，点击 **添加存储库**。

   ![添加“存储库”按钮](/help/managing-code/assets/repositories-tab.png)

1. 在 **添加存储库** 对话框中，确保选择 **Adobe 存储库** 作为存储库类型。

1. 在相应的文本字段中输入以下内容：

   * **存储库名称** — 新存储库的描述性名称。
   * **存储库URL预览** — 您无需输入URL路径或编辑现有路径，因为存储库基础结构已由Adobe配置、集成和管理。
   * **描述（可选）** - 存储库的详细描述。

   ![添加“存储库”对话框](/help/managing-code/assets/repository-add-adobe.png)

1. 单击&#x200B;**保存**。
您的新存储库显示在**存储库**&#x200B;页面上的表中。

您现在可以将 [CI/CD 管道](/help/overview/ci-cd-pipelines.md)与其关联，或在&#x200B;[**存储库**&#x200B;页面内对其进行管理](/help/managing-code/managing-repositories.md)。

>[!TIP]
>
>您还可以将自己管理的 GitHub 存储库添加为[专用存储库](/help/managing-code/private-repositories.md)。
