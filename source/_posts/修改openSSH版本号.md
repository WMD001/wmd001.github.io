---
title: 修改openSSH版本号
tags: [openSSH, Linux]
categories: [Linux]
date: 2024-07-02 17:39:40
description: 仅修改OpenSSH版本号
---

## 查看openSSH版本 ssh 和 sshd 都可以查看openSSH的版本
```shell 
[root@localhost ~] sshd -V
openSSH_9.6p1, OpenSSL 1.1.1p  21 Jun 2022
[root@localhost ~] ssh -V
openSSH_9.6p1, OpenSSL 1.1.1p  21 Jun 2022
```

## 查看位置
```shell 
[root@localhost ~] which ssh
/usr/bin/ssh
[root@localhost ~] which sshd
/usr/sbin/sshd
```

## 备份原文件
```shell 
[root@localhost ~] cp /usr/bin/ssh /usr/bin/ssh.bak
[root@localhost ~] cp /usr/sbin/sshd /usr/sbin/sshd.bak
```


## 查找版本号文本
```shell 
[root@localhost ~] strings /usr/bin/ssh | grep OpenSSH_9.6
OpenSSH_9.6p1
OpenSSH_9.6
[root@localhost ~] strings /usr/sbin/sshd | grep OpenSSH_9.6
OpenSSH_9.6p1
OpenSSH_9.6
```

## 修改版本号
```shell 
[root@localhost ~] sed -i 's/OpenSSH_9.6/OpenSSH_9.8/g' /usr/sbin/sshd
[root@localhost ~] sed -i 's/OpenSSH_9.6/OpenSSH_9.8/g' /usr/bin/ssh
```

## 重新查看openSSH版本
```shell 
[root@localhost ~] sshd -V
openSSH_9.8p1, OpenSSL 1.1.1p  21 Jun 2022
[root@localhost ~] ssh -V
openSSH_9.8p1, OpenSSL 1.1.1p  21 Jun 2022
```