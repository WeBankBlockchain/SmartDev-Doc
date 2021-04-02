# 组件介绍

在原先基于控制台的编译方式下，用户不仅需要安装控制台这一组件，编译流程也相对繁复，需要拷贝solidity文件到控制台，编译合约后，还需要将java合约拷贝到本地。但如果采用合约编译插件，在完成轻量级的一次性配置后，用户只需在项目工程下运行该插件，插件即会自动从合约目录读取solidity文件并编译为java合约，并会自动拷贝到业务工程下的对应包中。整个过程既不需要安装控制台，也省去了拷贝动作。流程对比如下：

![](picture/cplugin.png)

## 前置依赖

| 依赖软件 | 说明 |备注|
| --- | --- | --- |
| Java |>= JDK[1.8] | |
| Solidity | 0.4.25 | |
| Git | 下载安装包需要使用Git | |
| Gradle | >=6.0.1| |

## 快速开始

### 创建业务工程

创建一个空的业务工程，里面的src/main/contracts里包含了智能合约：

![](picture/demo.png)

### 插件配置

业务方需要在build.gradle中按如下方式引入插件。这段代码直接放在build.gradle首部：

```
buildscript {
    repositories {
        mavenCentral()
        maven { url "http://maven.aliyun.com/nexus/content/groups/public/"}
        maven { url "https://oss.sonatype.org/content/repositories/snapshots" }
        mavenLocal()
    }
    dependencies {
        classpath 'com.webank:solc-gradle-plugin:1.0.0-SNAPSHOT'
    }
}

apply plugin: 'solc-gradle-plugin'

```

然后如下进行配置。如果要生成java合约，还需要通过pkg选项配置java合约所属包名

```
solc{
    pkg = 'org.example.contracts'
}
插件的完整配置如下：

| 配置项 | 必选 | 说明 |
| --- | --- | --- |
| pkg | 否 | java合约包名 |
| contracts | 否 | 智能合约文件路径，默认为src/main/contracts |
| output | 否 | 编译输出路径，默认为src/main |
| onlyAbiBin | 否 | 是否只输出abi和bin默认false， |

```

### 编译合约

进入java工程：
```
cd solc-plugin-example
```
执行编译:

```
gradle solc
```

编译过后，会发现abi、bin、smbin、java合约已经被拷贝到项目中src/main中：

![](picture/result.png)

- abi：编译生成的abi
- bin：二进制文件,包含国密
- java：java合约


