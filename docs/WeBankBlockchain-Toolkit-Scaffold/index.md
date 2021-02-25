# 应用开发脚手架

[![License](https://img.shields.io/badge/license-Apache%202-4EB1BA.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)

```eval_rst
.. admonition:: **简介**

    智能合约脚手架用于一键式生成DAPP应用开发工程，从而降低应用开发的难度。用户将自己的合约导入脚手架，即可生成对应的应用开发模板工程，包含了java合约、测试代码等。此外，当用户修改了合约时，不必再使用控制台重新编译，而是可通过植入项目的gradle插件进行编译，新编译的java合约会被更新到项目中。
```

```eval_rst
.. toctree::
   :maxdepth: 3
   
   intro.md
```
```
package org.example.demo.service;

import java.lang.Exception;
import java.lang.String;
import java.util.Arrays;
import org.example.demo.model.bo.HelloWorldSetInputBO;
import org.fisco.bcos.sdk.client.Client;
import org.fisco.bcos.sdk.transaction.manager.AssembleTransactionProcessor;
import org.fisco.bcos.sdk.transaction.manager.TransactionProcessorFactory;
import org.fisco.bcos.sdk.transaction.model.dto.CallResponse;
import org.fisco.bcos.sdk.transaction.model.dto.TransactionResponse;

public class HelloWorldService {
  public static final String ABI = org.example.demo.contracts.HelloWorld.ABI;

  public static final String BINARY = org.example.demo.contracts.HelloWorld.BINARY;

  public static final String SM_BINARY = org.example.demo.contracts.HelloWorld.BINARY;

  private String address;

  private Client client;

  AssembleTransactionProcessor txProcessor;

  public HelloWorldService(String address, Client client) throws Exception {
    this.client = client;
    this.txProcessor = TransactionProcessorFactory.createAssembleTransactionProcessor(this.client, this.client.getCryptoSuite().getCryptoKeyPair());
    this.address = address;
  }

  public HelloWorldService(Client client) throws Exception {
    this.client = client;
    this.txProcessor = TransactionProcessorFactory.createAssembleTransactionProcessor(this.client, this.client.getCryptoSuite().getCryptoKeyPair());
    this.address = this.txProcessor.deployAndGetResponse(ABI,this.client.getCryptoType()==0?BINARY:SM_BINARY).getContractAddress();
  }

  public TransactionResponse set(HelloWorldSetInputBO input) throws Exception {
    return this.txProcessor.sendTransactionAndGetResponse(this.address, ABI, "set", input.toArgs());
  }

  public CallResponse get() throws Exception {
    return this.txProcessor.sendCall(this.client.getCryptoSuite().getCryptoKeyPair().getAddress(), this.address, ABI, "get", Arrays.asList());
  }
}

```