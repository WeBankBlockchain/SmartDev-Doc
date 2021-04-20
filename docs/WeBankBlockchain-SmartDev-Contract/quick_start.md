# 快速开始

## 环境要求

| 依赖软件 | 说明 |备注|
| --- | --- | --- |
| Solidity | 0.4.25 | |
| Git | 下载需要使用Git | |


## 如何获取

通过github下载源码：

```
git clone https://github.com/WeBankBlockchain/SmartDev-Contract.git
```
或者从gitee下载：

```
git clone https://gitee.com/WeBankBlockchain/SmartDev-Contract.git
```

具体使用方式请参考下文章节中的详细的API。


## 智能合约详细说明

### 基础类型层

| 库 | 功能 | 说明 | API |
| --- | --- | --- | --- |
|LibSafeMathForUint256Utils|数学运算|加减乘除、幂、最大值最小值、平均值等| [API](./api/types/LibSafeMathForUint256Utils.html) |
|LibConverter|整型转换操作|和各数据类型之间的转换等| [API](./api/types/LibConverter.html)|
|LibString|字符串操作|取长度、判断起始终止、查找子父、求子串、拼接、比较、大小写转换等|[API](./api/types/LibString.html) |
|LibAddress|地址操作|和各数据类型之间的转换；合约地址判断等|[API](./api/types/LibAddress.html)|
|LibArrayForUint256Utils|数组操作|排序、查找、去重、拼接等|[API](./api/types/LibArrayForUint256Utils.html) |

### 数据结构层

| 库 | 功能 | 说明 | API |
| --- | --- | --- | --- |
|LibMaxHeapUint256|堆|最大堆相关操作，取最值、插入、删除等| [API](./api/data_structure/LibMaxHeapUint256.html)|
|LibMinHeapUint256|堆|最小堆相关操作，取最值、插入、删除等| [API](./api/data_structure/LibMinHeapUint256.html)|
|LibStack|栈|提供栈相关操作，如进栈、出栈等|[API](./api/data_structure/LibStack.html) |
|LibQueue|队列|单向队列相关操作，入队、出队等|[API](./api/data_structure/LibQueue.html)|
|LibDeque|队列|双向队列相关操作，入队、出队等|[API](./api/data_structure/LibDeque.html)|
|LibAddressSet|address类型集合|集合操作，增删改查等| [API](./api/data_structure/LibAddressSet.html)|
|LibBytesMap|映射|映射操作，存、取、移除等|[API](./api/data_structure/LibBytesMap.html)|
|LibLinkedList|双向链表|链表相关操作|[API](./api/data_structure/LibLinkedList.html)|

### 通用功能层

| 库 | 功能 | 说明 | API |
| --- | --- | --- | --- |
|Table|CRUD合约|提供CRUD体验| [CRUD](https://fisco-bcos-documentation.readthedocs.io/zh_CN/latest/docs/articles/3_features/33_storage/crud_guidance.html)|
|Crypto|密码学|国密哈希、验签、VRF等| [API](./api/default/Crypto.html)|

### 上层业务层

| 库 | 功能 | 说明 | API |
| --- | --- | --- | --- |
|Evidence|存证|存证场景相关操作，上传、审批、修改、删除等|[API](./api/business_template/Evidence.html)|
|RewardPoint|积分|积分场景相关操作，发行、转移等|[API](./api/business_template/RewardPoint.html)|



