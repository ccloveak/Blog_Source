---
title: Basic Linux Commands (1)
author: せいい
top: false
cover: false
toc: true
tags:
  - Linux
categories:
  - Backend
date: 2021-01-16 23:17:35
summary: Linux 基本命令（1）
---

## 背景
* 前端开发者补充点Linux知识还是很有必要的
* 自己的小小小项目需要部署在树莓派或者aws（虽然只是停留在立案阶段）

## 基本命令
1. `cat`
* 输出整个文件的内容（适用于查看小文件）
```bash
cat 文件名
```

2. `more`
* 以分页的方式来显示内容，左下角显示百分比
```bash
more 文件名            # 基本用法     
ls -alh  /bin | more  # 分屏显示 bin 目录下内容
```

3. `less`
* 随意浏览文件，通过光标上下键查看所需内容
```bash
less 文件名
```

4. `head`
* 显示文件开头某个数量的内容 (默认前 10 行)
```bash
ps -ef | head     #显示前 10 条进程
head 文件名        #默认前 10 行
head -n 文件名     #显示文件前 n 行
```

5. `tail`
* 显示文件末尾某个数量的内容 (默认后 10 行)
```bash
tail 文件名          #默认显示文件后 10 行
tail -100 文件名     #显示后 100 行
tail -f 100 文件名   #循环读取新内容
```

6. `grep`
* 文本过滤，用于查找文件里符合条件的字符串
```bash
grep 关键字 文件名        #搜索文件里关键字
grep -v 关键字 文件名     #排除关键字内容显示
grep hexo package.json  #查找 package.json 文件中的 hexo 关键字内容
#据说egrep更好用
```

7. `wc`
* 文本统计，用于计算字数。
```bash
wc 文件名          #统计文件字节数、字数、行数
wc -l 文件名       #只统计文件行数
```

8. `sed`
* 利用 script 处理文本内容，可以对文件内容进行替换、删除空白行等正则功能
```bash
sed 's/yangyi/shengwei' test.txt    #替换文件中 yangyi 为 shengwei
sed 2g test.txt                     #删除文件第二行
sed '/^$/d' test.txt                #删除空白行
```

9. `uniq`
* 删除文本重复行，用于检测和删除文本文件中重复出现的行列
```bash
uniq test.txt       #删除重复的行
uniq -c test.txt    #统计重复的行
uniq -d test.txt    #只显示重复的行
```

10. `AWK`
* 这个命令有点复杂，所以我会把`Linux基本命令`改成 `Linux基本命令（1）。。。`

## 小结
* 先初步学一下，预计折腾树莓派或者aws的时候会轻松不少。
