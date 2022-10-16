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

#### DRF

* sharing incentive,资源要共池、共享
* strategy-proof,策略防护，用户不能通过欺骗获取更多的资源
* envy-free, 不羡慕/嫉妒其他用户分配的资源
* Pareto efficient, 别的用户不降低/释放资源的话，不能提高自己的资源分配量

##### nice-to-have

* Single resource fairness 只有一种资源，降级到Max-min
* Bottleneck fairness 都需求一种资源，降级到Max-min
* Population monotonicity 有用户退出系统、放弃拥有的资源，其他的用户不必放弃/减少自己的资源
* Resource monotonicity 有资源加入到系统/集群，其他的用户不必放弃/减少自己的资源

#### 对比

* Asset Fairness
* Competitive Equilibrium from Equal Incomes(CEEI)

#### properties

* Every user in a DRF allocation has at least one saturated resource.
* DRF satisfies the sharing incentive and bottleneck fairness properties.
* DRF is Pareto efficient.
* Every DRF allocation is envy-free.
* (Strategy-proofness) A user cannot in- crease her dominant share in DRF by altering her true demand vector.
* Given strictly positive demand vectors, DRF guarantees that every user gets the same dominant share, i.e., every DRF allocation ensures si = sj , for all users i and j .
* Given strictly positive demands, DRF sat- isfies population monotonicity.

### 参考 Referrences

* [DRF](https://cs.stanford.edu/~matei/papers/2011/nsdi_drf.pdf)
* [hadoop Yarn](https://github.com/apache/hadoop/tree/trunk/hadoop-yarn-project)
