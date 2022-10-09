---
layout: post
keywords: algorithm 
description:  common algorithms
title: "common algorithms"
categories: [algorithm]
tags: [algorithm]
---
{% include codepiano/setup %}

### 资源调度算法 Resources Scheduling algorithms

#### 最大最小公平算法(Max-Min Fairness)

> 1. 将资源平分成n份,每份都是S/n,把每份分给相应的用户
> 2. 如果超过了用户的需求，就回收超过的部分
> 3. 然后把总体回收的资源，平均分给上一轮分配中尚未得到满足的用户，依次类推，直到没有回收的资源为止

#### 加权最大最小公平算法(Weighted Max-Min Fairness)

> 1. 令W=w1 + w2+ … + wn, 将资源按照权重分成n份，每份分别是：S*w1/W, S*w2/W,…, S*wn/W。把每份分给相应的用户。
> 2. 如果超过了用户的需求，就回收超过的部分，假设有m个用户尚未得到满足
> 3. 然后把总体回收的资源，按照目前尚未满足的用户的权重分成m份，给对应的用户。依次类推，直到没有回收的资源为卡。

#### 主资源公平调度算法(Dominant Resource Fairness)

> * 主资源：用户申请的各个维度的资源无法直接比较大小，但是有一点可以比较，就是用户申请的各个维度的资源占其维度上的资源总量的百分比，主资源公平调度算法(Dominant Resource Fairness, DRF)中认为用户申请的一个资源单位中的各个维度中占维度资源总量百分比最大的是用户的主资源
> * share值：用户分得的主资源累积值占其维度资源总量的百分比

#### 加权主资源公平调度算法(Weighted Dominant Resource Fairness)

> * 主资源：与主资源公平调度算法中的主资源逻辑保持不变
> * share值：用户分得的主资源累积值占其维度资源总量的百分比，再除以用户的权重占整体权重的百分比。

### 参考 Referrences

* [DRF](https://cs.stanford.edu/~matei/papers/2011/nsdi_drf.pdf)
* [hadoop Yarn](https://github.com/apache/hadoop/tree/trunk/hadoop-yarn-project)

| English      | 中文 | 描述|
| ----------- | ----------- |----------- |
| variables      | 变量       | |
| Static variables   | 静态变量        |所有实例，能被修改，is stored on the data segment area of memory and the same value is get shared to all instances of that class|
| Constant variables | 常量/恒定变量 |每个实例"一份",但是不能修改值|
| Static Constant variables | 静态常量 |所有实例只有“一份”，而且不能修改|
| Constant pool | 常量池 |holds all the constants (integer, string, etc.);不是java对象；是在class文件中(loading过程)|
| String pool | string literal | 只有string;java对象 |

* [jvms Constant pool](https://docs.oracle.com/javase/specs/jvms/se7/html/jvms-4.html#jvms-4.4)
