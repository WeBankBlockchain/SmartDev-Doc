##############################################################
WeBankBlockchain-SmartDev 技术文档
##############################################################

.. admonition:: 什么是 WeBankBlockchain-SmartDev?

    区块链技术在经历了十余年的发展历程以后，渐呈“燎原之势”，不断在各行业落地生根。但同时，从技术角度看，区块链应用开发仍然有着较高的门槛，存在不少痛点，在应用开发各个环节上的用户体验有待提升。

    WeBankBlockchain-SmartDev应用开发组件的初衷是全方位助力开发者高效、敏捷地开发区块链应用。SmartDev包含了一套开放、轻量的开发组件集，覆盖智能合约的开发、调试、应用开发等环节，开发者可根据自己的情况自由选择相应的开发工具，提升开发效率。

.. admonition:: 设计目标

    - **轻量解耦** 所有的开发组件都是可独立使用。
    
    - **一站式** 覆盖了智能合约的研发、编译、区块链应用开发，旨在全方位助力区块链应用开发的所有环节。
        
    - **简洁易用** 致力于提供简洁的使用体验，让用户轻松上手。

.. admonition:: 组件简介

    - **SmartDev-Contract  智能合约库** 
    solidity智能合约代码库。包含基础类型、数据结构、通用功能、上层业务等智能合约库。用户可根据实际需求进行参考、复用。

    - **SmartDev-SCGP (Solidity Compiler Gradle Plugin) 智能合约编译插件** 
    将solidity智能合约代码编译为Java代码的gradle插件，可以编译项目中的智能合约，生成对应的Java文件，并自动拷贝到对应包目录下。 

    - **SmartDev-Scaffold 应用开发脚手架** 
    基于配置的智能合约文件，自动生成应用项目的脚手架代码，包含了智能合约所对应的实体类、服务类等内容，帮助用户只需要修改和编写较少量的代码，即可实现一个应用，大大简化了智能合约开发。 

.. important::
    FISCO-BCOS 2.0与3.0对比、JDK版本、WeBankBlockChain-SmartDev及其他子系统的 `兼容版本说明 <https://fisco-bcos-documentation.readthedocs.io/zh_CN/latest/docs/compatibility.html>`_

.. toctree::
   :hidden:
   :maxdepth: 3

   ./docs/WeBankBlockchain-SmartDev-Contract/index.md
   ./docs/WeBankBlockchain-SmartDev-SCGP/index.md
   ./docs/WeBankBlockchain-SmartDev-Scaffold/index.md
   ./docs/all_projects.rst
   ./docs/appendix.md
.. 


 
 
