---
title: Preparation of New Project (1)
author: せいい
top: false
cover: false
toc: true
tags:
  - VScode
  - typescript
categories:
  - メモ
date: 2022-02-20 09:24:05
summary: ESLint + Prettierを導入
---

## 开发环境
1. vscode
2. node
3. typescript

## 项目初始化
1. `npm init`
2. `npm install --save typescript`
3. `npx tsc --init`

## 导入 ESLint + Prettier
1. `npm install --save-dev eslint`
2. `npx eslint --init`
3. `npm install --save-dev prettier eslint-config-prettier`

```javascript
// .eslintrc.js
module.exports = {
  /* ****** */
  extends: [
    /* ****** */
    "prettier", //最後に追加する
  ],
};
```

## 安装插件
1. ESLint(`dbaeumer.vscode-eslint`)
2. Prettier(`esbenp.prettier-vscode`)

## 设定vscode
```json
// .vscode/settings.json rootに
{
  "editor.defaultFormatter": "esbenp.prettier-vscode", 
  "editor.formatOnSave": true
}

```

## demo
[github repo](https://github.com/ccloveak/ts_project_demo)