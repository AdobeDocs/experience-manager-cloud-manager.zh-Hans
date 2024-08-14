---
title: 使用多个Git存储库
description: 了解如何使用您自己的Git存储库或多个Git存储库，而不是直接使用Cloud Manager的Git存储库。
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 6%

---

# 使用多个源Git存储库 {#working-with-multiple-source-git-repos}

了解如何使用您自己的Git存储库或多个Git存储库，而不是直接使用Cloud Manager的Git存储库。

## 同步客户管理的Git存储库 {#syncing-customer-managed-git-repositories}

要使Cloud Manager的Git存储库保持最新，请使用您自己的一个或多个存储库来设置自动同步过程。

根据托管Git存储库的位置，可以使用GitHub操作或Jenkins等持续集成解决方案来设置自动化。 借助自动化功能，在每次推送到您自己的存储库时，都会自动转发到Cloud Manager的Git存储库。

虽然为单个客户拥有的Git存储库实施此类自动化很简单，但为多个存储库配置此类自动化则需要更复杂的初始设置。 需要将来自多个Git存储库的内容映射到单个Cloud Manager的Git存储库中的不同目录。 Cloud Manager的Git存储库需要使用根Maven `pom.xml`进行设置，并在模块部分中列出不同的子项目

以下是两个客户拥有的Git存储库的示例`pom.xml`。 第一个项目放入名为`project-a`的目录中，第二个项目放入名为`project-b`的目录中。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
  
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
  
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
  
</project>
```

此类根`pom.xml`将推送到Cloud Manager Git存储库中的分支。 然后，必须设置这两个项目以自动将更改转发到Cloud Manager的Git存储库。

例如，推送到项目A中的分支可以触发GitHub操作。 该操作会签出项目A和Cloud Manager Git存储库。 它将项目A中的所有内容复制到Cloud Manager Git存储库的`project-a`目录中。 然后提交并推送更改。

例如，对项目A中的`main`分支所做的更改将自动推送到Cloud Manager Git存储库中的`main`分支。 当然，分支之间可能会存在映射，例如在推送到项目A中名为`dev`的分支时，会推送到Cloud Manager Git存储库中名为`development`的分支。 对于项目 B，需要执行类似的步骤。

根据分支策略和工作流，可以为不同的分支配置同步。如果使用的Git存储库不提供与GitHub操作类似的概念，则也有可能通过Jenkins（或类似方法）进行集成。 在这种情况下，一个webhook将触发一个Jenkins作业来完成这项工作。

执行以下操作以添加新的（第三个）源或存储库：

1. 将新的GitHub操作添加到新存储库，以将更改从该存储库推送到Cloud Manager的Git存储库。
1. 至少执行一次该操作，以确保项目代码位于Cloud Manager的Git存储库中。
1. 在Cloud Manager Git存储库的根Maven `pom.xml`中添加对新目录的引用。

## 示例GitHub操作 {#sample-github-action}

推送到`main`分支会触发此示例GitHub操作，然后会推送到Cloud Manager Git存储库的子目录。 需提供`MAIN_USER`和`MAIN_PASSWORD`这两个密钥，GitHub操作才能连接并推送到Cloud Manager的Git存储库。

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

如上所示，使用GitHub操作是灵活的。 可以执行Git存储库的分支之间的任何映射，以及将单独的Git项目映射到主项目的目录布局中。

>[!NOTE]
>
>上述脚本使用`git add`更新存储库，假定包含移除内容。 根据Git的默认配置，此要求可能需要替换为`git add --all`。

## 示例Jenkins作业 {#sample-jenkins-job}

此脚本是一个示例，可用于Jenkins作业或类似作业。 Git存储库中的更改会触发该活动。 Jenkins 作业将签出该项目或分支的最新状态，然后触发此脚本。

此脚本依次签出Cloud Manager的Git存储库并将项目代码提交到子目录。

需提供`MAIN_USER`和`MAIN_PASSWORD`这两个密钥，Jenkins作业才能连接并推送到Cloud Manager的Git存储库。

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

如上所示，使用 Jenkins 作业是非常灵活的。可以执行Git存储库的分支之间的任何映射，以及将单独的Git项目映射到主项目的目录布局中。

>[!NOTE]
>
>上述脚本使用`git add`更新存储库，假定包含移除内容。 根据Git的默认配置，`git add`可能需要替换为`git add --all`。
