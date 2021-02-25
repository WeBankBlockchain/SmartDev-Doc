# 快速开始

智能合约脚手架用于一键式生成DAPP应用开发工程，从而降低应用开发的难度。用户将自己的合约导入脚手架，即可生成对应的应用开发模板工程，包含了java合约、测试代码等。此外，当用户修改了合约时，不必再使用控制台重新编译，而是可通过植入项目的gradle插件进行编译，新编译的java合约会被更新到项目中。

## 前置依赖

在使用本组件前，请确认已安装相关依赖软件，清单如下：

| 依赖软件 | 说明 |备注|
| --- | --- | --- |
| FISCO-BCOS | >= 2.7.1 | |
| Java | JDK[1.8] | |
| Solidity | 0.4.25 | |
| Git | 下载安装包需要使用Git | |



## 快速开始
目前支持基于命令行的方式，后续会推出基于可视化的使用方式，进一步降低用户使用的难度。


### 安装脚手架
目前支持从源码安装。

```
git clone https://github.com/WeBankBlockchain/SmartDev-Scaffold.git
cd SmartDev-Scaffold/tools
```

tools目录包含了执行环境，其结构为：
```
├── tools
│   ├── contracts
│   ├──── HelloWorld.sol
│   ├── run.sh
```
其中contracts目录用于存放solidity合约文件，脚手架后续会读取该目录下的合约以生成对应的业务工程。请删除该目录下的默认合约，并将自己的业务合约拷贝到该目录下。

### 运行脚手架

```
chmod +x run.sh
bash run.sh
```

用户可以指定artifact和group，例如
```
bash run.sh myProject com.webank
```

如果用户不指定，则项目名默认采用demo，group默认采用org.example。

### 生成效果
运行成功后，会在目录下得到一个项目工程项目：
```
├─contracts
├─run.sh
└─myProject
```
其中生成项目的具体内容如下：
![](image/Sample.png)

其中：
- conf目录包含区块链链接配置。关于配置的信息更多请见[说明](https://fisco-bcos-documentation.readthedocs.io/zh_CN/latest/docs/sdk/java_sdk/configuration.html)
- bo目录包含了合约函数输入参数的封装POJO类。
- service目录包含了每个智能合约的输入参数。

### 后续合约开发

请将配置文件拷贝到生成工程的conf目录下。conf包含证书和配置信息，

当用户基于生成的项目进行开发时，若需要修改合约，用户在修改完合约后，可在项目工程目录下直接编译合约：
```
cd [demo directory]
gradle solc
```

新的abi、bin会被刷新到目录下。

### 后续项目开发

用户可调用生成的Service类，例如：

```
    @Test
    public void test() throws Exception {

        BcosSDK bcosSDK = BcosSDK.build("conf/config.toml");
        Client client = bcosSDK.getClient(1);

        //方式1：自动部署一个合约
        HelloWorldService service
                = new HelloWorldService(client);//替换成实际生成项目中的对应合约
        //方式2：从指定地址加载合约
        HelloWorldService service2
                = new HelloWorldService(service.getAddress(), client);//替换成实际生成项目中的对应合约
        TransactionResponse setResponse = service.set(new HelloWorldSetInputBO("hello"));
        CallResponse callResponse = service.get();
    }
```
