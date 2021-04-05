# 附录

## Java安装

### Ubuntu环境安装Java

```
# 安装默认Java版本(Java 8或以上)
sudo apt install -y default-jdk
# 查询Java版本
java -version 
```

### CentOS环境安装Java

```
# 查询centos原有的Java版本
$ rpm -qa|grep java
# 删除查询到的Java版本
$ rpm -e --nodeps java版本
# 查询Java版本，没有出现版本号则删除完毕
$ java -version
# 创建新的文件夹，安装Java 8或以上的版本，将下载的jdk放在software目录
# 从openJDK官网(https://jdk.java.net/java-se-ri/8)或Oracle官网(https://www.oracle.com/technetwork/java/javase/downloads/index.html)选择Java 8或以上的版本下载，例如下载jdk-8u201-linux-x64.tar.gz
$ mkdir /software
# 解压jdk 
$ tar -zxvf jdk-8u201-linux-x64.tar.gz
# 配置Java环境，编辑/etc/profile文件 
$ vim /etc/profile 
# 打开以后将下面三句输入到文件里面并退出
export JAVA_HOME=/software/jdk-8u201-linux-x64.tar.gz
export PATH=$JAVA_HOME/bin:$PATH 
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
# 生效profile
$ source /etc/profile 
# 查询Java版本，出现的版本是自己下载的版本，则安装成功。
java -version 
```

## Git安装

git：用于拉取最新代码

**centos**:
```
sudo yum -y install git
```

**ubuntu**:
```
sudo apt install git
```
