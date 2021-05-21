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

.. admonition:: 更多开源项目

            - **FISCO BCOS企业级金融联盟链底层平台**: `[GitHub] <https://github.com/FISCO-BCOS/FISCO-BCOS>`_ `[Gitee] <https://gitee.com/FISCO-BCOS>`_ `[文档] <https://fisco-bcos-documentation.readthedocs.io/zh_CN/latest/index.html>`_ 
            - **WeBASE 区块链中间件平台**：`[GitHub] <https://github.com/WeBankFinTech/WeBASE>`_ `[Gitee] <https://gitee.com/WeBank/WeBASE>`_  `[文档] <https://webasedoc.readthedocs.io/>`_ 
            - **WeIdentity 基于区块链的实体身份标识及可信数据交换解决方案**: `[GitHub] <https://github.com/WeBankFinTech/WeIdentity>`_ `[Gitee] <https://gitee.com/WeBank/WeIdentity>`_ `[文档] <https://weidentity.readthedocs.io/>`_ 
            - **WeDPR 即时可用，场景式隐私保护高效解决方案套件和服务**：`[GitHub] <https://github.com/WeBankBlockchain/WeDPR-Lab-Core>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/WeDPR-Lab-Crypto>`_ `[文档] <https://wedpr-lab.readthedocs.io/>`_ 
            - **WeCross 区块链跨链协作平台**: `[GitHub] <https://github.com/WeBankBlockchain/WeCross>`_ `[Gitee] <https://gitee.com/WeBank/WeCross>`_ `[文档] <https://wecross.readthedocs.io/>`_ 
            - **Truora 可信预言机服务**：`[GitHub] <https://github.com/WeBankBlockchain/Truora>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/Truora>`_  `[文档] <https://truora.readthedocs.io/>`_ 
            - **Liquid 智能合约编程语言软件**：`[GitHub] <https://github.com/WeBankBlockchain/liquid>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/liquid>`_  `[文档] <https://liquid-doc.readthedocs.io/>`_
            - **WeBankBlockchain-Data 数据治理通用组建**：
               - Data-Stash 数据仓库组件： `[GitHub] <https://github.com/WeBankBlockchain/Data-Stash>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/Data-Stash>`_  `[文档] <https://data-doc.readthedocs.io/zh_CN/stable/docs/WeBankBlockchain-Data-Stash/index.html>`_
               - Data-Export 数据导出组件： `[GitHub] <https://github.com/WeBankBlockchain/Data-Export>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/Data-Export>`_  `[文档] <https://data-doc.readthedocs.io/zh_CN/stable/docs/WeBankBlockchain-Data-Export/index.html>`_
               - Data-Reconcile 数据对账组件：  `[GitHub] <https://github.com/WeBankBlockchain/Data-Reconcile>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/Data-Reconcile>`_  `[文档] <https://data-doc.readthedocs.io/zh_CN/stable/docs/WeBankBlockchain-Data-Reconcile/index.html>`_
            - **WeBankBlockchain-Governance 多方治理协作组建**：
               - Governance-Account 账户治理组件： `[GitHub] <https://github.com/WeBankBlockchain/Governance-Account>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/Governance-Account>`_  `[文档] <https://governance-doc.readthedocs.io/zh_CN/latest/docs/WeBankBlockchain-Governance-Acct/index.html>`_
               - Governance-Authority 权限治理组件：`[GitHub] <https://github.com/WeBankBlockchain/Governance-Authority>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/Governance-Authority>`_  `[文档] <https://governance-doc.readthedocs.io/zh_CN/latest/docs/WeBankBlockchain-Governance-Auth/index.html>`_
               - Governance-Key 私钥管理组件： `[GitHub] <https://github.com/WeBankBlockchain/Governance-Key>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/Governance-Key>`_  `[文档] <https://governance-doc.readthedocs.io/zh_CN/latest/docs/WeBankBlockchain-Governance-Key/index.html>`_
               - Governance-Cert 证书管理组件：`[GitHub] <https://github.com/WeBankBlockchain/Governance-Cert>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/Governance-Cert>`_  `[文档] <https://governance-doc.readthedocs.io/zh_CN/latest/docs/WeBankBlockchain-Governance-Cert/index.html>`_
            - **WeEvent 基于区块链的分布式事件驱动架构**：`[GitHub] <https://github.com/WeBankFinTech/WeEvent>`_ `[Gitee] <https://gitee.com/WeBank/WeEvent>`_  `[文档] <https://weevent.readthedocs.io/>`_
            - **WeBankBlockchain-SmartDev 区块链应用开发工具**：
               - SmartDev-Contract 智能合约库组件：`[GitHub] <https://github.com/WeBankBlockchain/SmartDev-Contract>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/SmartDev-Contract>`_  `[文档] <https://smartdev-doc.readthedocs.io/zh_CN/latest/docs/WeBankBlockchain-SmartDev-Contract/index.html>`_
               - SmartDev-SCGP 合约编译插件：`[GitHub] <https://github.com/WeBankBlockchain/SmartDev-SCGP>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/SmartDev-SCGP>`_  `[文档] <https://smartdev-doc.readthedocs.io/zh_CN/latest/docs/WeBankBlockchain-SmartDev-SCGP/index.html>`_
               - SmartDev-Scaffold 应用开发脚手架：`[GitHub] <https://github.com/WeBankBlockchain/SmartDev-Scaffold>`_ `[Gitee] <https://gitee.com/WeBankBlockchain/SmartDev-Scaffold>`_  `[文档] <https://smartdev-doc.readthedocs.io/zh_CN/latest/docs/WeBankBlockchain-SmartDev-Scaffold/index.html>`_

.. toctree::
   :hidden:
   :maxdepth: 3

   ./docs/WeBankBlockchain-SmartDev-Contract/index.md
   ./docs/WeBankBlockchain-SmartDev-SCGP/index.md
   ./docs/WeBankBlockchain-SmartDev-Scaffold/index.md
   ./docs/appendix.md
.. 


 
 
