---
layout: post
keywords: java jvm gc
description: java jvm garbage collection 
title: "java gc"
categories: [java]
tags: [java,jvm,gc]
---
{% include codepiano/setup %}

<img src="/image/java_jvm.png" /

## gc算法

* 引用计数法
> 循环引用的，孤岛问题

* 可达性分析

* 标记-清除
> 分为2个阶段
> * 标记
> * 清除
> 
> 不足
> * 标记、清除的效率问题
> * 空间碎片

* 标记-复制
> 需要双份大小的内存大小
> * 高效
> * 内存空间大
> * 新生代常用

* 标记-整理
> 分2个阶段，标记和整理
> * 整理直接将对象移动到一起

## 常用垃圾收集器
* Serial
> 单线程

* ParNew
> 新生代(young generation)，多线程(parallel threads)

* Parallel Scavenge
> 新生代，多线程，主要考虑吞吐量(throughput collector)。用户线程时间/总时间

* Serial Old
* Parallel Old(Parallel Scavenge Old) 
> * 多数jdk8的默认GC，也有将默认设置为CMS的，所以最好明确设置
> * the parallel garbage collector for full GCs

```
-XX:+UseParallelGC 
当使用ParallelGC时，可以使用-XX:+UseNUMA
```

* 设置参数
```
-XX:MaxGCPauseMillis=time  Sets a target for the maximum GC pause time (in milliseconds).JVM会努力
达到，但是不一定能达到
```

* CMS
>  CMS(老年代)+ParNew(新生代)，java9不建议使用

```
-XX:+UseConcMarkSweepGC -XX:+UseParNewGC
```

* G1
> 建议堆大小>6GB时使用

* Region。没有明确的新生代、老年代，逻辑的区分
* 初始标记 Initial Marking
* 并发标记 Concurrent Marking
* 最终标记 Final Marking
* 筛选回收 Live Data Counting and Evacuation



