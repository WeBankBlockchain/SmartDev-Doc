# LibConverter.sol

LibConverter提供各类solidity数据基本类型的转换，包括uint256转uint128、uint64、uint32等，uint256转bytes，int转bytes，bytes转int等转换方法。

## 使用方法

首先需要通过import引入LibConverter类库，调用库的相关方法：

```
pragma solidity ^0.4.25;

import "./LibConverter.sol"

contract test {
    
    function f() public view{
        uint256 a = 25;
        uint16 b = LibConverter.toUint16(a);
        //TODO:
    }
}
```


## API列表

编号 | API | API描述
---|---|---
1 | *toUint128(uint256 value) internal pure returns (uint128)* | 将uint256转为uint128类型
2 | *toUint8(uint256 value) internal pure returns (uint8)* | 将uint256转为uint8类型
3 | *uintToBytes(uint v) internal pure returns (bytes)* | 将uint转为bytes类型
4 | *bytesToInt(bytes b) internal pure returns (int result)* | 将bytes转为int类型
5 | *intToBytes(int v) internal pure returns (bytes)* | 将int转为bytes类型

## API详情

### ***1. toUint128 方法***

将uint256转为uint128类型，如超出uint128的最大值，则报错退出。

#### 参数

- uint256：转换数

#### 返回值

- uint128：返回转换结果。

#### 实例

```
function f() public view{
    uint256 a = 25;
    uint128 b = LibConverter.toUint128(a);
    //TODO:
}
```


### ***2. toUint8 方法***

将uint256转为uint8类型，如超出uint8的最大值，则报错退出。

#### 参数

- uint256：转换数

#### 返回值

- uint8：返回转换结果。

#### 实例

```
function f() public view{
    uint256 a = 25;
    uint8 b = LibConverter.toUint8(a);
    //TODO:
}
```

### ***3. toBytes 方法***

将uint256转为bytes类型。

#### 参数

- uint：转换数

#### 返回值

- bytes：转换结果

#### 实例

```
function f() public view{
    uint256 a = 25;
    bytes memory b = LibConverter.uintToBytes(a);
    //TODO:
}
```

### ***4. bytesToInt 方法***

将bytes转为uint256类型。

#### 参数

- bytes：转换字节

#### 返回值

- int：转换结果

#### 实例

```
function f() public view{
    bytes memory a = "25";
    int b = LibConverter.bytesToInt(a);
    //TODO:
}
```

### ***5. intToBytes 方法***

将int转为bytes类型。

#### 参数

- int：转换数

#### 返回值

- bytes：转换结果

#### 实例

```
function f() public view{
    int a = 25;
    bytes memory b = LibConverter.intToBytes(a);
    //TODO:
}
```
