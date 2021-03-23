# FAQ
## 上层业务类
### 积分场景合约
#### admin.sol合约upgradeVersion升级时候调用RewardPointData合约为什么传入的是_dataAddress地址?
这一步是为了读取和载入所管理的数据合约。

#### admin.sol合约upgradeVersion升级时候是把新部署的controller地址传进去吗？
是的。

#### admin.sol合约初始化的时候为什么把_controllerAddress也添加为发行者？
添加msg.sender是给管理者添加了发行权限。添加controllerAddress是给控制值添加发行权限。控制者必须要有发行的权限，所有业务相关的发行是通过控制者合约调用的。如果不添加，controller合约会无权限调用发行接口，也就是其中的issue接口会失效。

#### RewardPointData.sol合约中onlyLatestVersion()是如何起作用的？upgradeVersion是如何实现的？
onlyLatestVersion是一个修饰器，可参考solidity的modifier语法的含义。upgradeVersion的require语句会检查权限，判断是否是合约初始的部署者，以验证是否为管理员调用。

#### RewardPointController.sol合约应该和admin.sol合约同一部署者吗？
不一定。业务和管理相分离。在联盟链的治理中，大多数场景下应该是不同的。

#### RewardPointController.sol合约中destroy函数是起什么作用的？
用于销毁积分，在一些场景下有特殊的用途。可按需使用。

#### BasicAuth合约的权限控制设计是如何发挥作用的？
这是Solidity经典的设计模式之一。通过onlyOwner修饰器来检查权限，setOwner来更新管理者，auth来校验权限。语义是只有本合约或本合约的owner才有权限调用，是函数访问控制的基本功能合约。

#### 发行者和普通账户的区别和联系？
发行者可以发行积分，普通账户只能转账和消费积分。


### 存证场景合约
#### EvidenceController合约不继承Authentication合约的话，Authentication合约如何发挥权限控制作用？
在EvidenceRepository和RequestRepository继承和判断权限的。也就是说将鉴权放在了流程层和数据层。