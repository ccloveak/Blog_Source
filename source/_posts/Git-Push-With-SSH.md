---
title: Git Push With SSH
author: せいい
top: false
cover: false
toc: true
tags:
  - SSH
categories:
  - Github
date: 2021-01-26 23:04:28
summary: 用ssh进行自动部署
---

## 背景
* 有个需求是通过ssh连接github，必须是ssh

## 步骤

1. 生成公私密钥（一路回车）
```bash
ssh-keygen -t rsa -b 4096 -C "superstarzsw@gamil.com"

```
2. 读取公钥
```bash
~/.ssh
cat id_rsa.pub
```
3. 复制到[github](https://github.com/settings/keys)

4. 测试连接
```bash
ssh -T git@github.com
```


## 参考
* [文档](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

## 本地信息
* macOS
