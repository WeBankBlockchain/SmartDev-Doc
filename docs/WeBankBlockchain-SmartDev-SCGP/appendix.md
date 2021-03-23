# 常见问题
## solc-gradle-plugin找不到
如果业务工程中遇到下述错误：
```
Plugin id 'solc-gradle-plugin' not found
```
可尝试刷新依赖：
```
gradle solc --refresh-dependencies
```

如果还是失败，可从源码安装。

下载代码：

```
git clone https://github.com/WeBankBlockchain/SmartDev-SCGP.git
```

安装插件：

```
cd SmartDev-SCGP
gradle install
```

出现类似下面字样即为成功：
[](picture/success.png)