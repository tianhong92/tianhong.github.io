---
title: HashMap和ConcurrentHashMap
date: 2018-10-08 09:19:50
tags:
---

# HashMap
* 初始容量 - 哈希表中桶的数量
* 加载因子

默认大小为16， 当条目数超过12（16乘以0.75）时， 调用resize方法

## 寻址 
key值算出哈希值对数组长度进行取模作为index。因为取模代价远远大于位运算。 hashmap要求数组长度必须为2的n次方。
key的哈希值与2的n-1次方进行与运算， 结果与取模的结果是相同的。

## 线程不安全
rehash过程不是线程安全的， 多线程调用过程中可能出现死循环。
fast fail问题： 使用迭代器过程中hashmap被修改了， 就会抛出concurrent modification exception。
可以使用collections里面的synchMap方法构造同步map或者ConcurrentHashMap来避免fast fail

# ConcurrentHashMap
线程安全， 根据哈希码高位决定segment数组， 再根据哈希码决定hash entry数组的index， segment上面加了reentrant lock。
hashmap允许key和value为空， ConcurrentHashMap不允许。 

Java7为实现并行访问实现了segment分段锁，理论上最大并发度和segment的个数相等。 
Java8废弃了分段锁，直接使用大的数组。 当链表长度超过8（默认）， 链表转化为红黑树。

