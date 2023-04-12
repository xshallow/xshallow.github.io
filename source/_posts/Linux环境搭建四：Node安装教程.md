---
title: Linux环境搭建四：Node安装教程
comments: true
categories:
  - Linux
tags:
  - Linux
  - 安装教程
  - 服务器
  - 运维
  - Node
abbrlink: '5251'
date: 2022-12-01 11:37:39
top:
password:
photos:
---

### 准备Node安装包

[Node下载地址](https://nodejs.org/en/)

![image-20221201135233056](https://flowerunbeaten-blog-images.oss-cn-chengdu.aliyuncs.com/images/202212011352221.png)


<!-- more-->

![image-20221201135306594](https://flowerunbeaten-blog-images.oss-cn-chengdu.aliyuncs.com/images/202212011353704.png)

追求稳定选择左边的，想要尝试新功能的选择右边，一般推荐选择稳定版本，新版本不确定会不会有bug。选择对应的版本进行下载即可。

### 创建目录并解压

下载完成后上传至服务器指定位置，我这里是放在/home/software/文件夹下。

在/usr/local/下创建node文件夹并进入

```
cd /usr/local/
mkdir node
cd node
```

将node的安装包解压到/usr/local/node中即可。

```
tar -zxvf /home/software/node-v16.17.1-linux-x64.tar.xz -C ./
```

解压完成之后，在/usr/local/node的目录中会出现一个node-v16.17.1-linux-x64的目录。

### 配置Node系统环境变量

编辑 ~/.bash_profile ⽂件

```
vim ~/.bash_profile
```

在⽂件末尾追加如下信息:

```
# Nodejs
export PATH=/usr/local/node/node-v16.17.1-linux-x64/bin:$PATH
```

保存退出，刷新环境变量。

```、
source ~/.bash_profile
```

### 检查安装结果

```
node -v
npm version
npx -v
```

均有版本信息输出即可

![image-20221205104814718](https://flowerunbeaten-blog-images.oss-cn-chengdu.aliyuncs.com/images/202212051048798.png)