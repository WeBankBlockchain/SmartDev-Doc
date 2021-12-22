# 快速开始

## 环境要求

| 依赖软件 | 说明 |备注|
| --- | --- | --- |
| Solidity | 0.4.25 | |
| Git | 下载需要使用Git | |


## 如何获取

通过github下载[源码](https://github.com/WeBankBlockchain/SmartDev-Contract/releases/download/V1.2.0-alpha/WeBankBlockchain-SmartDev-Contract.V1.2.0-alpha.zip)：

```
curl -LO https://github.com/WeBankBlockchain/SmartDev-Contract/releases/download/V1.2.0-alpha/WeBankBlockchain-SmartDev-Contract.V1.2.0-alpha.zip
```


下载成功后，手动或用命令行解压压缩包：
```
unzip SmartDev-Contract*.zip
```

```eval_rst
.. note::
    - 如果因为网络问题导致长时间无法下载，请尝试：git clone https://gitee.com/WeBankBlockchain/SmartDev-Contract.git
```

具体使用方式请参考下文章节中的详细的API。


## 智能合约详细说明

### 基础类型层

| 库 | 功能 | 说明 | API |
| --- | --- | --- | --- |
|LibSafeMathForUint256Utils|数学运算|加减乘除、幂、最大值最小值、平均值等| [API](./api/base_type/LibSafeMathForUint256Utils.html) |
|LibSafeMathForFloatUtils|浮点数运算|提供了浮点型的相关计算操作，且保证数据的正确性和安全性，包括加法、减法、乘法、除法等操作| [API](./api/base_type/LibSafeMathForFloatUtils.html) |
|LibConverter|整型转换操作|和各数据类型之间的转换等| [API](./api/base_type/LibConverter.html)|
|LibString|字符串操作|取长度、判断起始终止、查找子父、求子串、拼接、比较、大小写转换等|[API](./api/base_type/LibString.html) |
|LibAddress|地址操作|和各数据类型之间的转换；合约地址判断等|[API](./api/base_type/LibAddress.html)|
|LibArrayForUint256Utils|数组操作|排序、查找、去重、拼接等|[API](./api/base_type/LibArrayForUint256Utils.html) |
|Lib2DArrayForUint256|数组操作|提供了Uint256二维数组的相关操作，包括增加新元素，删除元素，修改值，查找值，合并扩展数组等操作|[API](./api/base_type/Lib2DArrayForUint256.html) |
|LibBits|位操作|提供了位操作方法，例如按位非、移位、取前/后n位等方法|[API](./api/base_type/LibBits.html) |


### 数据结构层

| 库 | 功能 | 说明 | API |
| --- | --- | --- | --- |
|LibMaxHeapUint256|堆|最大堆相关操作，取最值、插入、删除等| [API](./api/data_structure/LibMaxHeapUint256.html)|
|LibMinHeapUint256|堆|最小堆相关操作，取最值、插入、删除等| [API](./api/data_structure/LibMinHeapUint256.html)|
|LibStack|栈|提供栈相关操作，如进栈、出栈等|[API](./api/data_structure/LibStack.html) |
|LibQueue|队列|单向队列相关操作，入队、出队等|[API](./api/data_structure/LibQueue.html)|
|LibDeque|队列|双向队列相关操作，入队、出队等|[API](./api/data_structure/LibDeque.html)|
|LibAddressSet|address类型集合|集合操作，增删改查等| [API](./api/data_structure/LibAddressSet.html)|
|LibBytes32Set|bytes32类型集合|提供了存储Bytes32类型的Set数据结构，支持包括add, remove, contains, getAll等| [API](./api/data_structure/LibBytes32Set.html)|
|LibBytesMap|映射|映射操作，存、取、移除等|[API](./api/data_structure/LibBytesMap.html)|
|LibLinkedList|双向链表|链表相关操作|[API](./api/data_structure/LibLinkedList.html)|
|LibSingleList|单向链表|包括链表更新、查询、迭代等|[API](./api/data_structure/LibSingleList.html)|
|DataTable|模拟数据库表的实现|提供了模拟row、table等实现|[API](./api/data_structure/DataTable.html)|
|Map|模拟映射的实现|提供了基于bytes32主键、自定义类型值的可迭代、可查询的映射|[API](./api/data_structure/Map.html)|
|LibMerkleTree|默克尔树实现|提供了默克尔树的生成和验证方法|[API](./api/data_structure/LibMerkleTree.html)|

### 通用功能层

| 库 | 功能 | 说明 | API |
| --- | --- | --- | --- |
|Table|CRUD合约|提供CRUD体验| [CRUD](https://fisco-bcos-documentation.readthedocs.io/zh_CN/latest/docs/articles/3_features/33_storage/crud_guidance.html)|
|Crypto|密码学|国密哈希、验签、VRF等| [API](./api/default/crypto/Crypto.html)|
|LibCryptoHash|内置密码相关的函数|keccak256、sha3、ripemd160等| [API](./api/default/crypto/LibCryptoHash.html)|
|LibDecode|验签|验证签名等功能等| [API](./api/default/crypto/LibDecode.html)|
|proxy|代理模式|代理执行即代理模式的实现| [API](./api/default/proxy/proxy.html)|
|internalFunction|内置相关的函数|包括block,tx相关等| [API](./api/default/internalFunction.html)|


### 常用工具层

| 库 | 功能 | 说明 | API |
| --- | --- | --- | --- |
|DateTimeContract|时间戳解析|基于时间戳计算当前的日期| [API](./api/common_tools/DateTimeContract.html)|
|DGHV|同态加密|一种基于智能合约的全同态加密方法| [API](./api/common_tools/DGHV.html)|
|FiatShamirZK|同态加密|一种零知识证明协议方法| [API](./api/common_tools/FiatShamirZK.html)|
|RBAC|基于角色的权限管理|RBAC| [API](./api/common_tools/RBAC.html)|
|RoleOperation|角色操作|RoleOperation| [API](./api/common_tools/RoleOperation.html)|
|whiteList|白名单操作|白名单管理的实现| [API](./api/common_tools/white_list_manage.html)|
|MathAdvance|数学运算|开方，平方，对数，幂| [API](./api/common_tools/math_advance.html)|


### 上层业务层

| 库 | 功能 | 说明 | API |
| --- | --- | --- | --- |
|Evidence|存证|存证场景相关操作，上传、审批、修改、删除等|[API](./api/business_template/Evidence.html)|
|evidence_plus|存证|存证合约 Plus 版本|[API](./api/business_template/evidence_plus.html)|
|MarriageEvidence|婚姻证明|结婚证书合约实例|[API](./api/business_template/MarriageEvidence.html)|
|redpacket|发红包|红包发放的场景|[API](./api/business_template/redpacket.html)|
|SimplePoint|积分|简单的积分场景|[API](./api/business_template/SimplePoint.html)|
|RewardPoint|积分|积分场景相关操作，发行、转移等|[API](./api/business_template/RewardPoint.html)|
|bill|金融票据|可以发布票据、对票据进行背书、验证背书、拒绝背书等操作|[API](./api/business_template/bill.html)|
|CarbonFrugalEvidence|共享充电积分能量存证合约|积分场景相关操作，发行、转移等|[API](./api/business_template/CarbonFrugalEvidence.html)|
|Traceability|商品溯源|实现商品溯源的案例|[API](./api/business_template/Traceability.html)|
|BookShares|股权薄记系统|实现公司股权薄记的案例|[API](./api/business_template/BookShares.html)|
|Chattel|金融动产|实现金融动产案例|[API](./api/business_template/chattel.html)|
|SharedBikes|共享单车|实现共享单车的案例|[API](./api/business_template/shared_bike.html)|
|GovOffice|政府办公|实现政府办公的案例|[API](./api/business_template/gov_office.html)|

### 合约杂谈

| 文章 | 说明 | 链接 |作者|
| --- | --- | --- | --- |
|SmartBasics|智能合约入门|[链接](https://github.com/WeBankBlockchain/SmartDev-Contract/blob/master/docs/miscs/tutorial/Solidity-basic.md)|yekai|
|ContractTips|合约开发杂谈|[链接](https://github.com/WeBankBlockchain/SmartDev-Contract/blob/master/docs/miscs/tutorial/Contract-tips.md)|江会文|