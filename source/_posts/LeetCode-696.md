---
title: LeetCode 696
author: せいい
top: false
cover: false
toc: true
tags:
  - LeetCode
categories:
  - Algorithm
date: 2021-02-17 23:32:32
summary: LeetCode 696
---

## Question

* Give a string s, count the number of non-empty (contiguous) substrings that have the same number of 0's and 1's, and all the 0's and all the 1's in these substrings are grouped consecutively.

* example
```javascript
Input: "00110011"
Output: 6

Input: "10101"
Output: 4
``` 

## Answer
```Typescript
const countBinarySubstrings = (s: string): number => {
    let result: number = 0;
    let pre: number = 0;
    let cur: number = 1;
    for (let i = 0, len = s.length - 1; i < len; i++) {
        s[i] === s[i + 1] ? (cur += 1) : ((pre = cur), (cur = 1));
        if (pre >= cur) {
            result += 1;
        }
    }
    return result;
};
``` 

## Result
![](LeetCode-696.png)

## 思路
1. `pre`是上一个数字出现的次数
2. `cur`是当前数字出现的次数
3. 用了穷举法？，把每一位数符合条件的次数相加，返回`result`

### 举个🌰 ` "00110" `
1. 第0位 0  `pre = 0, cur = 0, result = 0`
2. 第1位 0  `pre = 0, cur = 2, result = 0`
3. 第2位 1  `pre = 2, cur = 1, result = 1`
4. 第3位 1  `pre = 2, cur = 2, result = 2`
5. 第4位 0  `pre = 2, cur = 1, result = 3`
