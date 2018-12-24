---
title: java取模取余的区别
date: 2018-12-24 11:31:18
tags:
---


# 一个例子

int a = -11;
int b = 3;

System.out.println(a%b); // => -2
System.out.println(Math.floorMod(a, b)); // => 1

原因是取余取模运算方法都是：
1. 求整数商： c = a/b;
2. 求模或者余数： r = a - c/*b;
但是求模余数向负无穷舍入
求余余数向0舍入
