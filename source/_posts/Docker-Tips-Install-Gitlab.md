---
title: Docker Tips 'Install Gitlab'
author: せいい
top: false
cover: false
toc: true
tags:
  - Docker
  - Gitlab
categories:
  - インフラ
date: 2021-02-11 21:19:55
summary: 使用docker安装gitlab
---

## 背景
* 使用docker安装gitlab

## 操作
```bash
sudo docker run --detach \
  --hostname 18.179.23.91 \
  --publish 443:443 --publish 80:80 --publish 222:22 \
  --name gitlab \
  --restart always \
  --volume /srv/gitlab/config:/etc/gitlab \
  --volume /srv/gitlab/logs:/var/log/gitlab \
  --volume /srv/gitlab/data:/var/opt/gitlab \
  gitlab/gitlab-ce:latest

```

## docker command
* --detach：后台运行
* --hostname：指定运行的 hostname，可以是域名也可以是 IP。
* --publish：端口的映射，可以缩写成 -p
* --name：容器的名称
* --restart：重启的方式
  * no：默认策略，在容器退出时不重启容器
  * on-failure：在容器非正常退出时（退出状态非 0），才会重启容器
  * on-failure:3：在容器非正常退出时重启容器，最多重启 3 次
  * always：在容器退出时总是重启容器
  * unless-stopped：在容器退出时总是重启容器，但是不考虑在 Docker 守护进程启动时就已经停止了的容器
* --volume：指定本地卷，配置、日志、数据，使用本地卷后，删除容器，不会删除配置、数据

# 效果图
![](docker_gitlab.png)

## 小结
* 实例配置 2核4G
* aws得编辑出站规则 默认出站规则只有ssh的20端口开放
