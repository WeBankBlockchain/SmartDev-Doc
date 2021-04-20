# 快速开始

## 前置依赖

在使用本组件前，请确认已安装相关依赖软件，清单如下：

| 依赖软件 | 说明 |备注|
| --- | --- | --- |
| Java |>= JDK[1.8] | |
| Solidity | 0.4.25 | |
| Git | 下载安装包需要使用Git | |
| Gradle | >=6.0.1| |


## 下载脚手架
从github下载脚手架：

```
curl -LO https://github.com/WeBankBlockchain/SmartDev-Scaffold/releases/download/V1.0.0/SmartDev-Scaffold-V1_0_0.zip
```

下载成功后，手动或用命令行解压压缩包：
```
unzip SmartDev-Scaffold*.zip
```

或者从gitee下载：

```
git clone https://gitee.com/WeBankBlockchain/SmartDev-Scaffold.git
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
```
其中：
- contracts目录用于存放solidity合约文件，脚手架后续会读取该目录下的合约以生成对应的业务工程。请删除该目录下的默认合约，并将自己的业务合约拷贝到该目录下。
- config.ini是启动相关配置。
- run.sh是启动脚本

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
### 所支持的合约列表，通常为空即可
selector=
```

关于selector，如果需要只为指定合约进行编译输出，可以输入所需要的合约列表，按逗号分隔。例如下述代码中，只为AccountController,RoleController这两个合约：

```
selector=AccountController,RoleController
```

## 运行脚手架
可以直接启动脚本：
```
chmod +x run.sh
bash run.sh
```

运行成功后，会在tools目录下得到一个基于SpringBoot的项目工程：
```
├─contracts
├─run.sh
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
使用控制台部署HelloWorld合约
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
其中system.peers更换成实际的链节点监听地址；system.helloWorldAddress更换成前面部署过的合约地址。

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
