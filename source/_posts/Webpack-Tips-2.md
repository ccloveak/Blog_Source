---
title: Webpack Tips (2)
author: せいい
top: false
cover: false
toc: true
tags:
  - webpack
categories:
  - Frontend
date: 2021-02-07 00:45:30
summary: webpack系列学习 -- 基本配置
---

## メモ
1. entry
    * 单入口 SPA :tada: 字符串形式
    * 多入口 对象 key-value形式
2. output
    * filename
        * 通过占位符确保文件名称唯一
        * ` '[name].js' ` 这个name是1里多入口的key 单入口文件名是 `main.js`
    * path
3. loaders
    * module -> rules
    * test 指定匹配规则
    * use 指定使用的loader名称
4. Plugins
![](plugins.png)
5. Mode
6. bable
    * 支持es6
        * `@babel/core @babel/preset-env babel-loader`
    * 支持react
        * `react react-dom @babel/preset-react`
7. 解析css less
    * `style-loader css-loader less-loader`
8. 解析图片
    * `file-loader`用于处理图片
9. 解析字体
    * `file-loader`
10. 对 89 优化
    * `url-loader`
11. 文件监听
    * --watch
    * watch:true
12. 热更新
    * webpack-dev-server
    * HotModuleReplacementPlugin
    * `"dev": "webpack serve --mode development --hot-only" `
    *  槽点满满 教程里的webpack版本是3 现在都5了。。改动有点大
13. 文件指纹
    * hash
        * path.join / path.resolve
    * chunkhash
        * 主要对js
    * contenthash
        * 主要对css
        * `mini-css-extract-plugin`
        * MiniCssExtractPlugin
        * 图片的文件指纹 ![](file_hash.png)
        * 无法在热更新下使用

14. html 压缩
    * html-webpack-plugin ![](html_compression.png)

15. css 压缩
    * optimize-css-assets-webpack-plugin ![](css_compression.png)

## demo
* [github](https://github.com/ccloveak/Components_Demo/tree/main/webpack_demo/base_setting_demo)

## 小结
* 需要合理利用 stackoverflow github
* 不抛弃不放弃
