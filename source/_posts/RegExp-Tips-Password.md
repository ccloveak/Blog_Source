---
title: RegExp Tips 'Password'
author: せいい
top: false
cover: false
toc: true
tags:
  - React
categories:
  - Frontend
date: 2021-06-04 01:34:06
summary: 前端密码强度正则匹配
---

## 需求
* 展示密码强度

## 实现

```typescript
const PasswordRegExp = new RegExp('^(?=.*[a-zA-Z])(?=.*\\d)[a-zA-Z\\d\\W]{8,63}$');
const AlphanumericRegExp = new RegExp('^(?=.*[a-zA-Z])(?=.*\\d)[!-~]+$'); //英数字混在
const UpperLowerLetterRegExp = new RegExp('^(?=.*[A-Z])(?=.*[a-z])[!-~]+$'); //大文字小文字混在
const SymbolRegExp = new RegExp(
    "^(?=.*[!\"#$%&''()\\^\\-@\\[;:\\],./|`{+*}<>?_])[!-~]+$",
); //記号混在

```

## options
* escape-string-regexp npm包
* 转换后端（java）直接丢过来的正则
* 下面是核心代码：

```javascript

export default function escapeStringRegexp(string) {
	if (typeof string !== 'string') {
		throw new TypeError('Expected a string');
	}

	// Escape characters with special meaning either inside or outside character sets.
	// Use a simple backslash escape when it’s always valid, and a `\xnn` escape when the simpler form would be disallowed by Unicode patterns’ stricter grammar.
	return string
		.replace(/[|\\{}()[\]^$+*?.]/g, '\\$&')
		.replace(/-/g, '\\x2d');
}


```