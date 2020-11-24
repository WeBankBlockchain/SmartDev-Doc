##############################################################
WeBankBlockchain-Toolkit 技术文档
##############################################################

.. admonition:: 什么是 WeBankBlockchain-Toolkit 

    XXX。

.. admonition:: 设计目标

   XXXX

.. admonition:: 组件简介

    - **WeBankBlockchain-Data-Export  数据导出组件** 
    支持将链上数据导出到MySQL等结构化存储中，解决区块链数据复杂查询、分析和处理的问题。
    只需简单配置、无需开发、即可实时导出个性化的业务数据，实现将裸数据转化为标准化、结构化、有序化、可视化的高价值数据。请参考 `文档 <./docs/WeBankBlockchain-Data-Export/index.html>`_
    
    - **WeBankBlockchain-Data-Stash  数据仓库组件** 
    提供FISCO BCOS节点数据扩容、备份和裁剪的能力。
    可基于binlog协议同步区块链底层节点数据，支持断点续传，数据可信验证，并提供快速同步机制。请参考 `文档 <./docs/WeBankBlockchain-Data-Stash/index.html>`_ 
    
   


.. toctree::
   :maxdepth: 3

   ./docs/WeBankBlockchain-Toolkit-Contract/index.md
.. 


 
 
