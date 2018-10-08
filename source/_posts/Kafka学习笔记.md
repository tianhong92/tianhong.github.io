---
title: Kafka学习笔记
date: 2018-09-26 15:44:19
tags:
---

# Kafka基本概念

* Producer: 消息和数据生产者， 向Kafka的一个topic发布消息和进程/代码/服务
* Consumer: 消息和数据的消费者， 订阅数据（Topic）并且处理其发布的消息的进程/代码/服务
* Consumer Group: 逻辑概念， 对于同一个topic， 会广播给不同的group, 一个group中， 只有一个consumer可以消费该消息
* Broker: 物理概念， Kafka集群中的每个Kafka节点
* Topic：逻辑概念， Kafka消息的类别， 对数据区分， 隔离
* Partition: 物理概念， Kafka下数据存储的基本单元。 一个Topic数据， 会被分散存储到多个Partition， 每一个Partition是有序的
* Replication: 同一个Partition可能会有多个Replica， 多个Replica之间数据是一样的
* Replication Leader: 一个Partition的多个Replica上， 需要一个leader负责该Partition上的Producer和Consumer交互
* ReplicaManager: 负责管理当前Broker所有分区和副本的信息， 处理KafkaController发起的一些请求， 副本状态的切换，添加，读取消息等

