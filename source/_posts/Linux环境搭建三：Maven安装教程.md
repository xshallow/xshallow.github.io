---
title: Linux环境搭建三：Maven安装教程
comments: true
categories:
  - Linux
tags:
  - Linux
  - 安装教程
  - 服务器
  - 运维
  - Maven
abbrlink: 89c2
date: 2022-11-22 10:19:18
top:
password:
photos:
---

### 准备Maven安装资源

[Maven3下载地址](https://archive.apache.org/dist/maven/maven-3/)，我这里选择的版本是 apache-maven-3.6.3-bin.tar.gz。

将下载好的压缩文件上传至服务器指定目录下，我这里是上传到/home/software目录下。

<!-- more-->

### 安装Maven

安装Maven需要依赖Java环境，如果没有安装Java环境会导致安装不成功。如果没有安装Java环境请参考 [Linux JDK安装教程](https://blog.flowerunbeaten.top/post/47ad.html)。

在/usr/local/目录下新建一个maven文件夹并进入该文件目录下，将我们刚刚准备好的压缩文件解压到该目录下。

```
cd /usr/local/
mkdir maven
cd maven
tar -zxvf apache-maven-3.6.3-bin.tar.gz -C ./
```

### 配置阿里云镜像

```
# 进入到maven的配置文件夹下
cd /usr/local/maven/apache-maven-3.6.3/conf
# 编辑配置文件
vim settings.xml
# 在 <mirrors></mirrors> 标签对⾥添加如下内容即可：
<mirror>
 <id>alimaven</id>
 <name>aliyun maven</name>
 <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
 <mirrorOf>central</mirrorOf>
</mirror>
```

![image-20221122104447453](https://flowerunbeaten-blog-images.oss-cn-chengdu.aliyuncs.com/images/202211221044636.png)

### 配置Maven环境变量

```
# 编辑环境变量配置文件
vim /etc/profile
# 在文件尾部加入如下配置，保存并退出（ESC+:wq）。
# Maven环境变量配置
export MAVEN_HOME=/usr/local/maven/apache-maven-3.6.3
export PATH=$MAVEN_HOME/bin:$PATH
```

![image-20221122105010856](https://flowerunbeaten-blog-images.oss-cn-chengdu.aliyuncs.com/images/202211221050947.png)

刷新配置文件，使配置文件生效。

```
source /etc/profile
```

### 检验安装结果

```
mvn -v
```

![image-20221122105233906](https://flowerunbeaten-blog-images.oss-cn-chengdu.aliyuncs.com/images/202211221052956.png)

如图所示表示安装成功。