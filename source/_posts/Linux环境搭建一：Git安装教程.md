---
title: Linux环境搭建一：Git安装教程
abbrlink: '2372'
date: 2022-11-07 18:09:41
categories:
  - Linux
tags: 
  - Linux
  - 安装教程
  - 服务器
  - 运维
  - Git
---

### 前置条件

```
服务器：阿里云服务器
CentOS版本：CentOS 7.6
```

### 在线安装

```
# 安装git
yum install git
# 查看版本号
git --version
```

使用yum方法安装方式一般版本比较老

<!-- more-->

### 安装指定版本git

[git下载](https://git-scm.com/download/linux)

选择自己需要的版本进行下载，下载完成后上传至服务器指定文件下，我这里上传到/home/software目录下。

```
# 解压安装包
tar -zxvf git-2.38.0.tar.gz 
# 安装依赖
yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel gcc perl-ExtUtils-MakeMaker
# 查看git版本号
git --version
# 安装依赖时，自动安装了老的git版本，进行卸载。
yum remove git
# 进入解压后的git文件夹
cd git-2.38.0
# 执行编译
make prefix=/usr/local/git all
# 安装git至/usr/local/git目录
make prefix=/usr/local/git install
```

### 配置环境变量

编辑profile文件

```
# 编辑环境变量配置
vim /etc/profile
# 输入i，在适当位置加入
# Git环境变量配置
export GIT_HOME=/usr/local/git
export PATH=$PATH:$GIT_HOME/bin
# 保存，退出。按键盘ESC键并在命令框内输入:wq回车
```

### 刷新配置文件

刷新配置文件，使配置立即生效

```
# 刷新配置文件，使配置立即生效
source /etc/profire
# 查看git版本号
git --version
```

至此我们的git就安装好了。