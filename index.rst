##############################################################
WeBankBlockchain-SmartDev 技术文档
##############################################################

.. admonition:: 什么是 WeBankBlockchain-SmartDev

    对于区块链开发者，在智能合约开发中，经常会遇到各种问题，比如如何将账户地址和字符串互转，如何通过智能合约实现数据结构或者是否有一些可复用的智能合约代码？由于智能合约开发是一个相对较新的领域，在开发过程中，如果没有一套可参考的模板和代码库，不仅会影响了开发的效率，同时可能因为对智能合约开发的不熟悉造成系统安全风险。另一方面，当开发智能合约应用的时候，如果从头自己编写，会花费很多时间；此外，智能合约如果需要编译，首先需要安装控制台，然后在调试阶段，需要把合约导入控制台，编译后再把java合约拷贝出来调试，只要合约有变更，此流程就需要重新跑一边，非常的繁琐，严重影响开发效率。基于上述问题，我们编写了一套智能合约工具库，在减少合约漏洞的同时，提升智能合约的开发效率。目前，我们提供了智能合约库、dapp脚手架、合约编译插件这几个工具，覆盖dapp开发全生命周期。未来还会提供更多工具。

.. admonition:: 设计目标

    - 提供智能合约库SmartDev-Contract，覆盖基础类型到上层业务
    - DAPP开发脚手架SmartDev-Scaffold，轻松生成DAPP项目模板
    - 合约编译插件SmartDev-Compiler，本地编译智能合约

.. admonition:: 组件简介

    - **Contract  智能合约开源模板工具库** 
    包含基础类型、数据结构、通用功能、上层业务的solidity代码模板。
    
    - **Scaffold DAPP开发脚手架** 
    用于根据智能合约文件，得到DAPP项目模板，里面包含了合约函数的交易、调用功能。 

    - **SCGP solidity gradle编译插件** 
    一个gradle插件，可以编译项目中的智能合约，并拷贝到对应包目录下。 

.. toctree::
   :maxdepth: 3

   ./docs/WeBankBlockchain-Toolkit-Contract/index.md
   ./docs/WeBankBlockchain-Toolkit-SCGP/index.md
   ./docs/WeBankBlockchain-Toolkit-Scaffold/index.md
.. 


 
 
