---
title: 'Pow(x, n)%10 （快速幂+大数取模问题）'
date: 2021-08-29 23:13:10
tags: [JS, 算法, 快速幂, 大数越界]
categories: [JS, 算法]
comment: true
---

## 题目描述

### 来自：Zoom2021年秋招前端工程师笔试编程题2

给定2个非负整数x, n, 需要求 x^n （x的n次方）的最后一位。 x, n都可能很大很大。

任何数的0次方都是1.

## 分析

### 思路1

不难发现规律： ((x%y)^n)%y = (x^n)%y

<!-- more -->

因此很容易想到，第一步先把题目中的底数x提取成最后一位。但如果直接用编程语言库里自带的Math.pow(x, n)，依然可能会直接得到一个很大的结果，取模依然可能不正确。因此，我们需要考虑自己实现一套幂运算，在过程中多次取最后一位，这样就会使得所有的运算都是小数取模了。

快速幂公式参考[LeetCode 50. Pow(x, n) （快速幂，清晰图解）-Krahets](https://leetcode-cn.com/problems/powx-n/solution/50-powx-n-kuai-su-mi-qing-xi-tu-jie-by-jyd/)

### 思路2

根据观察不难发现，0-9为底的幂运算取最后一位是存在一个循环的。我们先求出这个循环的规律，然后判断n是在循环的第几位，即可直接得到结果。

### 注意

由于Javascript BigInt过于复杂，没有实现x, y为大数时的算法。

## 代码

```javascript 公用方法.js
function mod10( num ) {
    return parseInt(num) % 10;
}
```

```javascript 思路1.js
function lastDigitQuickPow(str1, str2) {
    let x = mod10(str1); // x直接取最后一位
    let n = parseInt(str2); // 可能涉及大数，转成BigInt
    if (n === 0) {
        return 1; // 任何数的0次方都是1
    }
    let res = 1;
    for (let i = x; n; i = mod10(i * i), n = n >> 1) {
    	// 每次使i平方，然后n减少一位二进制位（位右移）
        if ((n & 1) == 1) {
            res = mod10(res * i); // 如果当前位是1，则在结果中增加
        }
    }
    return res;
}
```

```javascript 思路2.js
function lastDigit(str1, str2) {
    let x = mod10(str1); // x直接取最后一位
    let n = parseInt(str2); // 可能涉及大数，转成BigInt
    if (n === 0) {
        return 1; // 任何数的0次方都是1
    }
    let loopCount = 0;
    let loopNum = [x];
    for (let i = x; true;) {
        i = mod10(i * x); // 查找循环的下一位
        loopCount++;
        if (i === x) {
            break; // 得到循环的总长度loopCount和取余对应loopNum[]
        } else {
            loopNum.push(i);
        }
    }
    let resMod = (n - 1) % loopCount; // 获取循环中的余数（左移一位）
    return loopNum[resMod];
}
```