---
title: Linux 上安装 Java
tags: [linux, java]
categories: [后端]
date: 2024-07-09 17:44:08
description: Ubuntu20.04 安装 Java17，配置环境变量
---

## 下载

https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html
下载压缩包
![img.png](img.png)

## 解压验证
```bash
tar -zxvf jdk-17_linux-x64_bin.tar.gz
```
解压后可以得到目录`jdk-17.0.10`，进入`bin`目录，查看java版本
```bash
cd jdk-17.0.10/bin
./java -version
java version "17.0.10" 2024-01-16 LTS
Java(TM) SE Runtime Environment (build 17.0.10+11-LTS-240)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.10+11-LTS-240, mixed mode, sharing)
```

## 配置环境变量
```bash
sudo vim /etc/profile

# 在文件末尾添加以下内容
export JAVA_HOME=/usr/local/jdk-17.0.10
export PATH=$JAVA_HOME/bin:$PATH

# 生效配置文件
source /etc/profile

#验证
echo $JAVA_HOME
/usr/local/jdk-17.0.10

java -version
java version "17.0.10" 2024-01-16 LTS
Java(TM) SE Runtime Environment (build 17.0.10+11-LTS-240)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.10+11-LTS-240, mixed mode, sharing) 
```

收工
