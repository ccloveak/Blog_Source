---
title: AWS Tips 'Upload File'
author: せいい
top: false
cover: false
toc: true
tags:
  - AWS
categories:
  - Backend
date: 2021-02-04 00:33:54
summary: 往AWS上传文件
---

## 需求
* 需要往AWS上传文件

## 操作
1. home 下新建文件夹 upload `mkdir upload`
2. 调整权限 `chmod 0777 upload`
3. 密钥对所在文件夹上传文件 
```bash
scp -i "aws.pem" initNodejs.sh ec2-user@18.183.14.245:/home/upload
```

## 小结
* 这个ip是自动生产的，貌似还能配弹性ip