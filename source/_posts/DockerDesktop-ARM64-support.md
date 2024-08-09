---
title: DockerDesktop拉取ARM64平台镜像，并启动容器
tags: [dockerDesktop, ARM64]
categories: [docker]
date: 2024-08-09 10:12:10
description: DockerDesktop拉取ARM64平台镜像，并启动容器.
---

## 修改配置

打开docker设置，选择Docker Engine，把 {% mark color:yellow experimental %} 修改为`true`。    
意思是：开启manifest的试验特性。

```json 
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "experimental": true
}
```

## 拉取镜像

使用 `docker pull` 拉取镜像时，加上 {% mark color:yellow platform %} 参数，指定要拉取的平台。

{% copy docker pull --platform linux/arm64 IMAGE_NAME prefix:$ %}

以下拉取openjdk17镜像为例：

### 拉取openjdk17镜像

```bash
docker pull --platform linux/arm64 openjdk:17
```

### 启动容器

```bash
docker run --platform linux/arm64 -d --name arm64-openjdk openjdk:17
```

发现启动后过一会就会停止，因为没有在运行的前端进程。
删除容器，重新启动容器，并添加一个进程，让容器一直运行。

```bash
docker rm <container_id>
docker run --platform linux/arm64 -d --name arm64-openjdk openjdk:17 tail -f /dev/null
```
然后可以看到容器在运行了。

使用命令进入容器，查看系统信息。
```bash
docker exec -it arm64-openjdk /bin/bash
uname -m
# aarch64
```
可以看到平台确实是arm64了。