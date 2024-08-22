---
title: 构建环境
description: 了解 Cloud Manager 用户可用来构建和测试代码的专用构建环境。
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 63%

---


# 构建环境 {#build-environment}

了解 Cloud Manager 用户可用来构建和测试代码的专用构建环境。

## 环境详细信息 {#details}

Cloud Manager的构建环境具有以下属性。

* 构建环境基于 Linux，并派生自 Ubuntu 22.04。
* 安装了 Apache Maven 3.9.4。
   * Adobe 建议用户[更新其 Maven 存储库以使用 HTTPS 代替 HTTP](#https-maven)。
* 安装的 Java 版本是 Oracle JDK 8u401 和 Oracle JDK 11.0.22。
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* 默认情况下，`JAVA_HOME`环境变量设置为`/usr/lib/jvm/jdk1.8.0_401`，其中包含OracleJDK 8u401。 有关更多详细信息，请参阅[替代 Maven 执行 JDK 版本](#alternate-maven)部分。
* 安装了一些其他的必要系统包。
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* 可以在构建时安装其他包，如[安装其他系统包](#installing-additional-system-packages)部分中所述。
* 每次构建都是在原始环境中完成的。 构建容器在执行之间不保留任何状态。
* Maven 始终通过以下三条命令运行：
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* 使用 `settings.xml` 文件在系统级别配置 Maven，并将自动包含使用名为 `adobe-public` 的配置文件的公共 Adobe 构件存储库。请参阅 [Adobe 公共 Maven 存储库](https://repo1.maven.org/)了解详情。
* 对于[前端管道](/help/overview/ci-cd-pipelines.md)有 Node.js 18 可用。

>[!NOTE]
>
>虽然 Cloud Manager 未定义 `jacoco-maven-plugin` 的具体版本，但使用的版本必须至少为 `0.7.5.201505241946`。

>[!TIP]
>
>请参阅以下其他资源，了解如何使用 Cloud Manager API：
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [创建 API 集成](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [API 权限](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## HTTPS Maven存储库 {#https-maven}

Cloud Manager [版本 2023.10.0](/help/release-notes/2023/2023-10-0.md) 开始了对构建环境的一项滚动更新（在发布版本 2023.12.0 时完成更新），其中包括对 Maven 3.8.8 的更新。Maven 3.8.1 中引入的一项重大更改是旨在减少潜在漏洞的一项安全增强。具体来说，Maven 现在默认禁用所有不安全的 `http://*` 镜像，如 [Maven 发行说明中所述](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291)。

此安全增强导致某些用户可能在构建步骤中遇到问题，尤其是从使用不安全 HTTP 连接的 Maven 存储库下载工件时。

为了确保更新版本的流畅体验，Adobe 建议用户更新其 Maven 存储库以使用 HTTPS 代替 HTTP。此调整与行业日益转向安全通信协议的趋势一致，并有助于构建过程保持安全可靠。

## 使用特定的Java版本 {#using-java-version}

默认情况下，通过Cloud Manager构建过程构建的项目使用Oracle8 JDK。 希望使用替代 JDK 的客户有两种选择。

* [Maven 工具链](#maven-toolchains)
* [为整个 Maven 执行过程选择替代 JDK 版本](#alternate-maven)

### Maven 工具链 {#maven-toolchains}

[Maven工具链插件](https://maven.apache.org/plugins/maven-toolchains-plugin/)允许项目选择特定的JDK（或工具链）以在工具链感知的Maven插件的上下文中使用。 通过指定供应商和版本值，在项目的`pom.xml`文件中完成此过程。 `pom.xml`文件中的示例部分如下：

```xml
        <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>
```

此过程会导致所有工具链感知的Maven插件使用OracleJDK版本11。

在使用此方法时，Maven 本身仍将使用默认 JDK (Oracle 8) 运行，并且不会更改 `JAVA_HOME` 环境变量。因此，通过[Apache Maven Enforcer插件](https://maven.apache.org/enforcer/maven-enforcer-plugin/)等插件检查或强制实施Java版本将不起作用，并且不得使用此类插件。

当前可用的供应商/版本组合是：

| 供应商 | 版本 |
|---|---|
| oracle | 1.8 |
| oracle | 1.11 |
| oracle | 11 |
| 星期日 | 1.8 |
| 星期日 | 1.11 |
| 星期日 | 11 |

>[!NOTE]
>
>从2022年4月开始，OracleJDK将成为用于开发和运行AEM应用程序的默认JDK。 Cloud Manager 构建过程会自动切换为使用 Oracle JDK，即使已在 Maven 工具链中明确选定替代选项也是如此。请参阅[四月发行说明](/help/release-notes/2022/2022-4-0.md)以了解更多信息。

### 替代Maven执行JDK版本 {#alternate-maven}

也可以选择 Oracle 8 或 Oracle 11 作为整个 Maven 执行的 JDK。与工具链选项不同，除非还设置了工具链配置（在此情况下，工具链配置仍适用于工具链感知的Maven插件），否则这将更改用于所有插件的JDK。 因此，通过[Apache Maven Enforcer插件](https://maven.apache.org/enforcer/maven-enforcer-plugin/)来检查和强制实施Java版本是可行的。

为此，请在管道使用的Git存储库分支中创建名为`.cloudmanager/java-version`的文件。 此文件可以包含内容 `11` 或 `8`。任何其他值将被忽略。如果指定了 `11`，则使用 Oracle 11，并且 `JAVA_HOME` 环境变量将设置为 `/usr/lib/jvm/jdk-11.0.22`。如果指定了 `8`，则使用 Oracle 8，并且 `JAVA_HOME` 环境变量将设置为 `/usr/lib/jvm/jdk1.8.0_401`。

## 环境变量 {#environment-variables}

### 标准环境变量 {#standard-environ-variables}

在某些情况下，您可能会发现必须根据项目或管道的相关信息来更改构建过程。

例如，当使用诸如gulp之类的工具进行JavaScript缩小时，您可能更希望为开发环境与暂存和生产环境使用不同的缩小级别。

为了支持这一点，Cloud Manager 会为每个执行将标准环境变量添加到构建容器中。

| 变量名称 | 描述 |
|---|---|
| `CM_BUILD` | 始终设置为 `true` |
| `BRANCH` | 执行的已配置分支 |
| `CM_PIPELINE_ID` | 数值管道标识符 |
| `CM_PIPELINE_NAME` | 管道名称 |
| `CM_PROGRAM_ID` | 数值项目标识符 |
| `CM_PROGRAM_NAME` | 项目名称 |
| `ARTIFACTS_VERSION` | 对于暂存或生产管道，为由 Cloud Manager 生成的合成版本 |

### 标准环境变量可用性 {#availability}

可在多个位置使用标准环境变量。

#### 创作、预览和发布环境 {#author-preview-publish}

常规环境变量和密钥均可用于创作、预览和发布环境。

#### Dispatcher {#dispatcher}

只有常规环境变量可用于[Dispatcher](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-dispatcher/using/dispatcher)。 无法使用密钥。

但是，无法在`IfDefine`指令中使用环境变量。

>[!TIP]
>
>在部署之前，在本地通过[Dispatcher](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools)验证您对环境变量的使用。

#### OSGi配置 {#osgi}

可在 [OSGi 配置](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi)中使用常规环境变量和密钥。

### 管道变量 {#pipeline-variables}

在某些情况下，您的构建过程可能取决于特定的配置变量，这些变量不适合放置在Git存储库中，或者需要在使用同一分支的不同管道执行之间发生改变。

Cloud Manager 允许通过 Cloud Manager API 或 Cloud Manager CLI 按管道配置这些变量。可将变量以纯文本或静态加密形式存储。在任一情况下，变量都将在构建环境中作为环境变量提供，然后可以从`pom.xml`文件或其他构建脚本中引用这些变量。

要使用 CLI 设置变量，请运行类似于以下内容的命令。

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

可以使用类似于以下内容的命令列出当前变量。

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

变量必须遵循特定的限制。

* 变量名只能包含字母数字字符和下划线 (`_`)。
   * 按照惯例，名称应全部大写。
* 每个管道最多有 200 个变量。
* 每个名称的长度必须少于100个字符。
* 每个字符串值的长度必须少于2048个字符。
* 每个`secretString`值的长度必须少于500个字符。

通常，在 Maven `pom.xml` 文件中使用变量时，使用与以下内容类似的语法将这些变量映射到 Maven 属性会很有用。

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## 安装其他系统包 {#installing-additional-system-packages}

为了充分发挥作用，一些构建需要安装其他系统包。 例如，构建可能会调用 Python 或 Ruby 脚本，因此，需要安装适当的语言解释程序。此方案可以通过调用[`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/)以调用APT来完成。 此执行通常应封装在特定于 Cloud Manager 的 Maven 配置文件中。例如，要安装Python，您可以执行以下操作：

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

此技术还可用于安装语言特定的包。 即，将`gem`用于RubyGems，或将`pip`用于Python包。

>[!NOTE]
>
>通过此方式安装系统包并不会将它安装在用于运行 Adobe Experience Manager 的运行时环境中。 如果您需要在 AEM 环境中安装系统包，请联系您的 Adobe 代表。
