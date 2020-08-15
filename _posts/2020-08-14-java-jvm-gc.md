---
layout: post
keywords: java jvm gc
description: java jvm garbage collection 
title: "java gc"
categories: [java]
tags: [java,jvm,gc]
---
{% include codepiano/setup %}

## gc算法

* 引用计数法
> 循环引用的，孤岛问题

* 可达性分析

* 标记-清除
* 标记-复制
* 标记-整理

## 常用垃圾收集器
* Serial

* ParNew
* Parallel Scavenge
* Serial Old
* Parallel Old(Parallel Scavenge Old) 
> 多数jdk8的默认GC，也有将默认设置为CMS的，所以最好明确设置

```
-XX:+UseParallelGC 
```

* CMS
>  CMS(老年代)+ParNew(新生代)，java9不建议使用

```
-XX:+UseConcMarkSweepGC -XX:+UseParNewGC
```

* G1
> 建议堆大小>6GB时使用



