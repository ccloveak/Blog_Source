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

## 小结
* 实例配置 2核4G
* aws得编辑出站规则 默认出站规则只有ssh的20端口开放
