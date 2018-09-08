---
title: 线程安全-并发容器JUC
date: 2018-09-07 11:40:15
tags:
---

# ArrayList -> CopyOnWriteArrayList
读写分离， add操作被锁保护， 防止多线程操作时创建多个副本， 读在原数组上， 不用加锁； 最终一致性； 使用时另外开辟空间； 
缺点： 元素多可能写操作导致full gc； 不能用于实时读的场景， 更适合读多写少的场景； 

# HashSet, TreeSet -> CopyOnWriteArraySet, ConcurrentSkipListSet
