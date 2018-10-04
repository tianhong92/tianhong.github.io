---
title: 线程安全-并发容器JUC
date: 2018-09-07 11:40:15
tags:
---

# ArrayList -> CopyOnWriteArrayList
读写分离， add操作被锁保护， 防止多线程操作时创建多个副本， 读在原数组上， 不用加锁； 最终一致性； 使用时另外开辟空间； 
缺点： 元素多可能写操作导致full gc； 不能用于实时读的场景， 更适合读多写少的场景； 

# HashSet, TreeSet -> CopyOnWriteArraySet, ConcurrentSkipListSet
CopyOnWriteArraySet底层基于CopyOnWriteArrayList。
ConcurrentSkipListSet基于Map集合 remove, add, contains是线程安全的， 但是removeAll， addAll不是线程安全的。 不能保证每一次批量操作都不会被其他线程打断， 需要手动加其他控制， 比如加锁。 不支持null	

# HashMap, TreeMap -> ConcurrentHashMap, ConcurrentSkipListMap
ConcurrentHashMap不允许null， 除了插入删除操作外， 读取操作效率很高。 这个类有很好的并发性。 要 *重点理解原理*
ConcurrentSkipListMap key有序的， 支持更高的并发， 存取时间和线程数没有关系。 有更好的并发度。

# 安全共享对象策略

1. 线程限制： 一个被线程限制的对象， 由线程独占， 并且只能被占有他的线程修改
2. 共享只读： 一个共享只读的对象， 在没有额外同步的情况下， 可以被多个线程并发访问， 但是任何线程都不能修改它
3. 线程安全的对象： 一个线程安全的对象或者容器， 在内部通过同步机制来保证线程安全， 所以其他线程无需额外的同步就可以通过公共接口随意访问它
4. 被守护对象： 被守护对象只能通过获取特定的锁来访问

