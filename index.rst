##############################################################
WeBankBlockchain-SmartDev 技术文档
##############################################################

.. admonition:: 什么是 WeBankBlockchain-SmartDev

    SmartDev的初衷是全方位助力开发者高效、敏捷的开发区块链应用。SmartDev包含了一套开放、轻量的开发组件集，覆盖合约的开发、调试、应用开发各个环节，开发者可根据自己的情况选择相应开发工具，提升开发效率。

.. admonition:: 设计目标
    - **轻量解耦**。所有的开发组件都是可独立使用。
    
    - **一站式**。覆盖了智能合约的研发、合约的编译、项目工程，几乎包含区块链应用开发的所有环节。
        
    - **简洁易用**。致力于提供简洁的使用体验，让用户轻松上手。

.. admonition:: 组件简介

    - **SmartDev-Contract  智能合约开源模板工具库** 
    包含基础类型、数据结构、通用功能、上层业务的solidity代码模板。

    - **SCGP (Solidity Compiler Gradle Plugin) 合约编译插件** 
    一个gradle插件，可以编译项目中的智能合约，并拷贝到对应包目录下。 

    - **SmartDev-Scaffold 应用开发脚手架** 
    用于根据智能合约文件，生成应用项目，里面包含了合约函数对应的实体类、服务类等内容。 

.. toctree::
   :maxdepth: 3

   ./docs/WeBankBlockchain-SmartDev-Contract/index.md
   ./docs/WeBankBlockchain-SmartDev-SCGP/index.md
   ./docs/WeBankBlockchain-SmartDev-Scaffold/index.md
   ./docs/appendix.md
.. 


 
 
