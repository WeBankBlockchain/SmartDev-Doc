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
    │   │               │   ├── BcosConfig.java
    │   │               │   ├── ContractConfig.java
    │   │               │   ├── SdkBeanConfig.java
    │   │               │   └── SystemConfig.java
    │   │               ├── constants
    │   │               │   ├── ContractConstants.java
    │   │               ├── model
    │   │               │   ├── CommonResponse.java
    │   │               │   └── bo
    │   │               │       └── HelloWorldSetInputBO.java
    │   │               ├── service
    │   │               │   └── HelloWorldService.java
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
            │           └── Demos.java
            └── org.example.demo
```

其中：
- config目录包含Bean配置类
- service目录中包含了智能合约访问的Service类，一个类对应一个合约。
- bo目录包含了合约函数输入参数的封装POJO类。
- src/main/resource/conf目录用于存放证书信息
- Demos.java包含了私钥生成、部署合约等示例代码

## DAPP开发
这里介绍DAPP开发过程，以前面生成的demo项目工程为例。
### 部署合约
使用控制台部署HelloWorld合约
### 证书拷贝
请将配置文件拷贝到生成工程的conf目录或src/main/resources/conf目录下。
### 配置连接节点
请修改application.properties，该文件包含如下信息：
```
### Java sdk configuration
cryptoMaterial.certPath=conf
network.peers[0]=127.0.0.1:20200
#network.peers[1]=127.0.0.1:20201

### System configuration
system.groupId=1
system.privateKey=

### Contract configuration
contract.helloWorldAddress=

### Springboot configuration
server.port=8080
server.session.timeout=60
banner.charset=UTF-8
spring.jackson.date-format=yyyy-MM-dd HH:mm:ss
spring.jackson.time-zone=GMT+8


```
其中：
- java sdk configuration配置部分与[javasdk](https://fisco-bcos-documentation.readthedocs.io/zh_CN/latest/docs/sdk/java_sdk/configuration.html)配置一致。
    * 其中需要用户将network.peers[0]=127.0.0.1:20200更换成实际的链节点监听地址。
- System configuration包含群组、私钥等配置。
    * system.hexPrivateKey是16禁止的私钥明文。如果该选项不做配置，会走java sdk配置对应的私钥；如果私钥做了配置，那么会覆盖java sdk的私钥。
- Contract confguration包含合约配置，用户需要更换成前面部署过的合约地址。

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
### 其他
当用户基于生成的项目进行开发时，若需要修改合约，可在项目工程目录下直接编译合约：
```
cd [demo directory]
gradle solc
```

新的abi、bin会被刷新到src/main/resources目录下，但相关Service类和BO类并不会被重新生成，需要用户自行修改。
