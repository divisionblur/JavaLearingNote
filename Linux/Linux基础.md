# Linux基础

## 虚拟机Vmware的安装

1. 虚拟机的安装网上教程一大堆，就不写了

## 下载Linux的镜像文件

1. 去一些国内的镜像网站下载会比较快比如阿里云，下载centos 8。

## 一些基本配置

### 网络连接的三种方式

1. 桥接模式
2. NAT模式
3. 自定义模式

### 虚拟机克隆

1. 手动将原来的虚拟机的安装文件拷贝一份放在其他文件夹用Vmware打开就行

   ![image-20201120092019901](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120092027.png)

2. 使用Vmware进行拷贝

   ![image-20201120092137192](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120092137.png)

### 虚拟机快照

每拍一个快照肯定会对虚拟机的空间有占用所以说不要频繁的建立快照应该在认为可能会出现错误的地方拍快照。

![image-20201120171038781](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120171038.png)

![image-20201120170800988](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120170808.png)

### 虚拟机的迁移和删除

![image-20201120171256525](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120171256.png)

## 安装Vmtools

![image-20201120171408730](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120171408.png)

![image-20201120171527665](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120171527.png)

点击重新安装Vmtools之后虚拟机的桌面就会出现install vmware tools的一个图标

点击进入之后会发现一个以tar.gz结尾的文件将这个文件拷贝到opt目录下然后在终端使用如下命令进行解压

```java
tar -zxvf vmware-tools -----xxx.tar.gz
```

解压完之后cd命令进入/opt目录下刚刚解压出的哪个文件

执行命令 ./vmware-install.pl一路回车就可以了

## Linux的目录结构

![image-20201120180555994](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120180556.png)

![image-20201120180637674](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120180637.png)

![image-20201120180737432](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120180737.png)

![image-20201120180759403](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120180759.png)

![image-20201120180833533](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120180833.png)

# Linux实操篇

1. 远程登陆到Linux

   ![image-20201120180956303](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120180956.png)

![image-20201120181031682](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120181031.png)

**Xshell连接Linux**

在终端使用命令==ifconfig==查看IP地址

![image-20201120181215275](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120181215.png)

打开Xshell

![image-20201120181302513](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120181302.png)

在主机栏输入IP地址

点确定，再点连接就可以了。

2. 远程文件传输

   使用Xftp也是配置以下IP地址就可以了  左边是windows右边是linux

## vi和vim文本编辑器的使用

![](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120183702.png)

![image-20201120183827682](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120183827.png)

![image-20201120183910853](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120183911.png)

![image-20201120183943142](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120183943.png)

## 开机重启和用户登陆注销

![image-20201120184615361](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120184615.png)

![image-20201120184701149](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120184701.png)

## 用户管理

![image-20201120190134275](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120190141.png)

![image-20201120190405227](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120190405.png)

![image-20201120190722795](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201120190722.png)

上图说明用管理员用户创建一个新的用户用的命令

```java
useradd milan
```

在这个时候根目录的home目录下就会多一个名为milan的文件夹，代表一个用户。

**删除一个用户同时删掉这个用户的家目录**，删除的时候带上-r参数 milan下面的所有东西都没有了

```java
userdel -r milan
```

**删除用户但是保留用户的家目录的命令**(一般情况下我们都保留用户的家目录)

```java
userdel milan
```

**指定和修改密码**

基本语法

```java
passwd 用户名
```

然后就会让你输入密码  注意：如果passwd后面没有写用户名那么就是给当前用户进行密码的修改。

**查询用户信息**

基本语法

```java
id 用户名
```

**切换用户**

**可以通过su - 指令，切换到高权限用户，比如root。**

基本语法

```java
su - 切换用户名
```

从权限高的用户切换到权限低的用户，不需要输入密码反之需要当需要返回到原来的用户时用命令

```java
exit或者是logout
```

查看当前用户/登录用户、

基本语法

```java
who am i
```

**用户组**

* 类似于角色，系统可以对有共性/权限的多个用户进行统一的管理

1.新增组

* groupid  组名

2.删除组

* groupdel 组名

3.增加用户时直接加上组

```java
useradd -g  用户组  用户名
```

增加一个用户zwj，直接将他指定到 wudang

先增加一个组

```java
groupadd wudang
```

创建用户时直接加入组

```java
useradd -g wudang zwj
```

4.修改用户所在的组

```java
usermod -g 组名  用户
```

**用户组和相关信息**

![image-20201121092508101](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201121092515.png)

## Linux实用指令

### 运行级别

![image-20201121093127947](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201121093128.png)

![image-20201121094300497](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201121094300.png)

如上图所示,使用命令

```java
systemctl get-default
```

获得默认的运行级别

使用命令  

```java
systemctl set-default xxx.target
```

设置默认的运行级别

### 如何找回root用户密码

### 帮助指令

![image-20201121095902779](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201121095902.png)

## 文件目录类

![image-20201124083356295](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124083403.png)

![image-20201124084034092](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124084034.png)

![image-20201124084359280](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124084359.png)

![image-20201124085438734](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124085438.png)

![image-20201124090623535](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124090623.png)

![image-20201124091048349](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124091048.png)

![image-20201124091923787](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124091923.png)

![image-20201124092733677](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124092733.png)

![image-20201124093204477](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124093204.png)

![image-20201124141740621](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124141740.png)

![image-20201124142430997](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124142431.png)

![image-20201124145850883](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124145851.png)

![image-20201124151445125](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124151445.png)

![image-20201124153244287](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124153244.png)

![image-20201124153630655](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124153630.png)

## 时间日期类

![image-20201124154439579](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124154439.png)

![image-20201124154827917](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124154828.png)

## 搜索查找类

![image-20201124160427457](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124160427.png)

![image-20201124161427776](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124161427.png)

![image-20201124162607326](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124162607.png)

![image-20201124162652547](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124162652.png)

## 压缩和解压类

![image-20201124163038598](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124163038.png)

![image-20201124164101851](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201124164102.png)