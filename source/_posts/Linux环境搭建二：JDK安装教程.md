---
title: Linux环境搭建二：JDK安装教程
comments: true
categories:
  - Linux
tags:
  - Linux
  - 安装教程
  - 服务器
  - 运维
  - JDK
abbrlink: 47ad
date: 2022-11-10 10:45:53
top:
password:
photos:
---



### 卸载已有的OPEN JDK

```
# 输入以下命令检查是否存在open jdk
rpm -qa | grep java
# 如果存在，则删除
yum -y remove 对应open jdk的名称
```
<!-- more-->

### 下载JDK

[Oracle官网地址](https://www.oracle.com/)

我这里选择的版本是[jdk-8u341-linux-x64.tar.gz](https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html#license-lightbox)，如果要选择其他版本可自行选择下载。

下载完成后，使用fxtp工具将下载的压缩文件上传至你服务器指定的文件夹下，我这里是/home/software。

### 安装JDK

1、在/usr/local/下创建java文件夹并进入。

```
cd /usr/local/
mkdir java
cd java
```

2、将上面准备好的JDK安装包解压到/usr/lcoal/java 文件夹下。

```
tar -zxvf /home/software/jdk-8u341-linux-x64.tar.gz -C ./
```

解压完成后，/usr/local/java的文件夹下会出现一个jdk1.8.0_341的目录。

### 配置JDK环境变量

编辑/etc/profile文件

```
vim /etc/profile
```

在文件的末尾加入如下配置。

```
# Java环境变量设置
JAVA_HOME=/usr/local/java/jdk1.8.0_341
CLASSPATH=$JAVA_HOME/lib/
PATH=$PATH:$JAVA_HOME/bin
export PATH JAVA_HOME CLASSPATH
```

保存并退出（ESC+:wq）

使配置文件生效

```
source /etc/profile
```

### 验证JDK安装结果

依次输入下面的命令。

```
java
javac
java -version
```

出现下面的界面代表安装成功。

![image-20221110201901523](https://flowerunbeaten-blog-images.oss-cn-chengdu.aliyuncs.com/images/202211102019581.png)



![image-20221110201959596](https://flowerunbeaten-blog-images.oss-cn-chengdu.aliyuncs.com/images/202211102019656.png)

![image-20221110202018519](https://flowerunbeaten-blog-images.oss-cn-chengdu.aliyuncs.com/images/202211102020551.png)

