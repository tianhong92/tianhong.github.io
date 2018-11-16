---
title: 使用JDK命令行工具监控
date: 2018-11-16 16:22:51
tags:
---

# 查看JVM运行时参数

	$ java -XX:+PrintFlagsFinal 查看改变后的参数
	$ jps 查看java进程 -l 参数就知道完全类名
	$ jinfo -flag MaxHeapSize PID 
	$ jinfo -flag UseConcMarkSweepGC PID 是否启用CMS
	$ jinfo -flags PID 显示Non-default VM flags

# jstat查看JVM统计信息
## 类装载 -class
	$ jstat -class PID 1000 10 间隔1s输出10次 
## 垃圾收集 -gc
	$ jstat -gc PID 1000 10
## JIT编译 -compile

