# 快速开始

## 前置依赖

在使用本组件前，请确认已安装相关依赖软件，清单如下：

| 依赖软件 | 说明 |备注|
| --- | --- | --- |
| Java |>= JDK[1.8] | |
| Solidity | 0.4.25 | |
| Git | 下载安装包需要使用Git | |
| Gradle | 大于6 小于7|使用gradle7会报错 |


## 下载脚手架
从github下载[脚手架](https://github.com/WeBankBlockchain/SmartDev-Scaffold/releases/download/V1.0.0/SmartDev-Scaffold-V1_0_0.zip)：

```
curl -LO https://github.com/WeBankBlockchain/SmartDev-Scaffold/releases/download/V1.0.0/SmartDev-Scaffold-V1_0_0.zip
```

下载成功后，手动或用命令行解压压缩包：
```
unzip SmartDev-Scaffold*.zip
```

```eval_rst
.. note::
    - 如果因为网络问题导致长时间无法下载，请尝试：git clone https://gitee.com/WeBankBlockchain/SmartDev-Scaffold.git
```

进入目录：
```
cd SmartDev-Scaffold/tools
```

tools目录包含了执行环境，其结构为：
```
├── tools
│   ├── contracts
│   ├──|── HelloWorld.sol
│   ├── config.ini
│   ├── run.sh
│   ├── run.bat
```
其中：
- contracts目录用于存放solidity合约文件，脚手架后续会读取该目录下的合约以生成对应的业务工程。请删除该目录下的默认合约，并将自己的业务合约拷贝到该目录下。
- config.ini是启动相关配置。
- run.sh和run.bat分别是unix和windows下的启动脚本。

## 配置脚手架
### 合约配置
请删除contracts目录下的默认合约，并将自己的业务合约拷贝到该目录下。

### 生成配置
可以在config.ini中做生成配置，如下：
```
### 项目名称
artifact=demo
### 组名称
group=org.example
### 所支持的合约列表，默认为空表示选择所有合约
selector=
### solidity编译器版本，可选0.4.25.1, 0.5.2.0, 0.6.10.0三种
compiler=0.4.25.1
### gradle版本，支持5.6.1、gradle 6各版本。暂不支持gradle7
gradleVersion=6.3
```

关于selector，如果需要只为指定合约进行编译输出，可以输入所需要的合约列表，按逗号分隔。例如下述代码中，只为AccountController,RoleController这两个合约：

```
selector=AccountController,RoleController
```

## 运行脚手架
可以直接启动脚本（unix系统为例）
```
chmod +x run.sh
bash run.sh
```

运行成功后，会在tools目录下得到一个基于SpringBoot的项目工程：
```
├─contracts
├─run.sh
├─run.bat
└─demo
```
其中生成项目的具体内容如下：

```
.
├── build.gradle
├── gradle
│   └── wrapper
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── settings.gradle
└── src
    ├── main
    │   ├── contracts
    │   │   └── HelloWorld.sol
    │   ├── java
    │   │   └── org
    │   │       └── example
    │   │           └── demo
    │   │               ├── Application.java
    │   │               ├── config
    │   │               │   ├── ContractConfig.java
    │   │               │   ├── SdkBeanConfig.java
    │   │               │   └── SystemConfig.java
    │   │               ├── model
    │   │               │   ├── CommonResponse.java
    │   │               │   └── bo
    │   │               │       └── HelloWorldSetInputBO.java
    │   │               ├── service
    │   │               │   └── HelloWorldService.java
    │   │               └── utils
    │   │                   └── IOUtil.java
    │   └── resources
    │       ├── abi
    │       │   └── HelloWorld.abi
    │       ├── application.properties
    │       ├── bin
    │       │   ├── ecc
    │       │   │   └── HelloWorld.bin
    │       │   └── sm
    │       │       └── HelloWorld.bin
    │       └── conf
    └── test
        └── java
            ├── org
            │   └── example
            │       └── demo
            │           └── DemoPkey.java
            └── org.example.demo
```

其中：
- config目录包含Bean配置类
- service目录中包含了智能合约访问的Service类，一个类对应一个合约。
- bo目录包含了合约函数输入参数的封装POJO类。
- src/main/resource/conf目录用于存放证书信息

## DAPP开发
这里介绍DAPP开发过程，以前面生成的demo项目工程为例。
### 部署合约
使用控制台部署HelloWorld合约,或者使用部署工具
### 证书拷贝
请将配置文件拷贝到生成工程的conf目录或src/main/resources/conf目录下。该业务工程会自动在这些路径下搜索证书。
### 配置连接节点
请修改application.properties，该文件包含如下信息：
```
### Required
system.peers=127.0.0.1:20200,127.0.0.1:20201
### Required
system.groupId=1
### Optional. Default will search conf,config,src/main/conf/src/main/config
system.certPath=conf,config,src/main/resources/conf,src/main/resources/config
### Optional. If don't specify a random private key will be used
system.hexPrivateKey=
### Optional. Please fill this address if you want to use related service
contract.helloWorldAddress=
server.port=8080

```
注意：
- system.peers更换成实际的链节点监听地址；
- system.helloWorldAddress更换成前面部署过的合约地址，该地址可通过控制台或快捷工具

system.hexPrivateKey可以见使用快捷工具生成；如果为空，系统内部会生成一个随机私钥。

### 补全业务
一个完整的DAPP应包含至少三层架构，本示例补全一个Controller。
在org.example.controller下新建一个Controller类，如下：
```
@RestController
@RequestMapping("hello")
public class HelloController {

    @Autowired
    private HelloWorldService service;
    
    @GetMapping("set")
    public String set(@RequestParam("n") String n) throws Exception{
        HelloWorldSetInputBO input = new HelloWorldSetInputBO(n);
        return service.set(input).getTransactionReceipt().getTransactionHash();
    }

    @GetMapping("get")
    public String get() throws Exception{
        return service.get().getValues();
    }
}

```

### 运行jar包
```
cd demo
gradle bootJar
cd dist
```
会在dist目录生成demo-exec.jar，可执行此jar包：
```
java -jar demo-exec.jar
```
随后，可在浏览器内输入:
```
http://127.0.0.1:8080/hello/set?n=hello
```
返回示例：
```
0x1c8b283daef12b38632e8a6b8fe4d798e053feb5128d9eaf2be77c324645763b
```

```
http://127.0.0.1:8080/hello/get
```
返回示例：
```
["hello"]
```
### 快捷工具的使用
当用户需要部署合约、生成私钥等功能时，可以使用相关命令。

#### 合约部署

部署合约的快捷工具:
```
java -jar [工程jar包] deploy [合约名称] [参数列表]
```
例如，部署HelloWorld:
```
java -jar demo-exec.jar deploy HelloWorld
```
可以在日志尾部看到地址：
```
...
2021-05-12 21:38:14.657  INFO 10232 --- [           main] o.f.b.s.a.wrapper.ABIDefinitionFactory   :  contractABIDefinition org.fisco.bcos.sdk.abi.wrapper.ContractABIDefinition@6f5d0190 
2021-05-12 21:38:14.659  INFO 10232 --- [           main] o.f.b.sdk.abi.wrapper.ABIObjectFactory   :  name: null
2021-05-12 21:38:15.064  INFO 10232 --- [           main] org.example.demo.tool.DeployTool         : deploy address:0x587122b6804b68fe1d8e9ab8711ce2570fd19a52
```
#### 私钥生成

私钥生成的快捷工具：
```
java -jar [工程jar包] key
```
该工具会为国密、非国密各生成一个密钥对。

例如：
```
java -jar demo-exec.jar key
```
可以在日志尾部看到地址：
```
2021-05-12 21:36:40.652  INFO 36044 --- [           main] org.example.demo.tool.KeyTool            : ecdsa private key :bd79e88f9538f2f90654f5504b91f7266757680de5b8cecc5265942a36bbdb5e
2021-05-12 21:36:40.652  INFO 36044 --- [           main] org.example.demo.tool.KeyTool            : ecdsa public key :047d101a4ef9de322d17ef6da7c02c21e9424e38be4be9117a3ac064d3b119ccb5aa116c8e725117bc8e99a7214c7198447796c2aa78fc5211615a03ce4b4ca762
2021-05-12 21:36:40.653  INFO 36044 --- [           main] org.example.demo.tool.KeyTool            : ecdsa address :0x3ab6411439d9f851b3f7b801da01ef4bc7fa6c72
2021-05-12 21:36:40.995  INFO 36044 --- [           main] org.example.demo.tool.KeyTool            : sm2 private key :4af94cc052f56bd0e9a7d6ff50bf8bb09c8d219176f1978bfe6ae3449aca57d1
2021-05-12 21:36:40.995  INFO 36044 --- [           main] org.example.demo.tool.KeyTool            : sm2 public key :0457a96ff57a154649dfa2ce1ef783ec2dafd211e80ddb6f1fb6290835e3f9ef77f144632fea4d28e154311f22fa7e9a0f44843f1891c84a8cb8bd5861b0b13fda
2021-05-12 21:36:40.995  INFO 36044 --- [           main] org.example.demo.tool.KeyTool            : sm2 address :0x17481a7e309a5b4790dca1cd2a9ac84b9cda5631
```

