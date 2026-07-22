---
title: 安全性和隐私
description: 了解Adobe Cloud Manager中代码和工件资源的安全性和隐私。
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: d5a34a9f6d050eaff241c0f42c9cf023cbc8036a
workflow-type: tm+mt
source-wordcount: 201
ht-degree: 26%

---

# 安全性和隐私 {#security-and-privacy}

了解Adobe Cloud Manager中代码和工件资源的安全性和隐私。

## 角色和权限 {#roles}

Cloud Manager 预配置了一些具有适当权限的角色。

要了解您可以在 Admin Console 中分配的角色和用户角色权限，请参阅[基于角色的权限](/help/requirements/role-based-permissions.md)。

## 资源隔离 {#resource-isolation}

Cloud Manager客户需要使用IMS凭据进行身份验证，因为所有与Cloud Manager关联的权限都会关联到其IMS组织。 在新用户引导过程中，配置团队需确保在Cloud Manager中实施资源隔离。

## 数据安全性 {#data-security}

对Cloud Manager代码进行传输中加密。 Cloud Manager构建二进制文件，这些文件在传输期间也进行了加密，并以加密格式存储。

每个客户都有自己的Git存储库，并且代码是安全的，不会与任何其他组织共享。

## 数据隐私 {#data-privacy}

Cloud Manager遵守Adobe制定的隐私原则。 开发人员通过 HTTPS 将代码安全地推送到 Git 存储库中。

Cloud Manager的用户界面使用符合Adobe Common Control Framework的服务。 Cloud Manager的用户界面使用来自多个云提供商的安全服务。
