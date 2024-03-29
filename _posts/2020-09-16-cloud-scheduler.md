---
layout: post
keywords: scheduler, placement 
description: cloud scheduler
title: "cloud scheduler"
categories: [cloud]
tags: [cloud]
---
{% include codepiano/setup %}

### keywords

* scheduler
* placement
* allocation

### references

* dynamic placement for clustered web applications
* Entropy- a Consolidation Manager for Clusters
* A scalable application placement controller for enterprise data centers

决定每个应用启动多少实例和放在那台机器上

* A Scalable Application Placement Controller for Enterprise Data Centers
解决的问题：
  30秒内，上千的机器和上千实例高质量的放置方案。 应用的动态扩缩容。
  * 满足最大的应用放置需求
  * 最少启动、停止应用
  * 物理机的均衡度

  > The placement problem is NP hard.
  > * approximation algorithms 近似算法
  [6] A. Karve, T. Kimbrel, G. Pacifici, M. Spreitzer,
M. Steinder, M. Sviridenko, and A. Tantawi. Dynamic Application Placement for Clustered Web Applications. In the International World Wide Web Conference (WWW), May 2006.
  [8] T. Kimbrel, M. Steinder, M. Sviridenko, and A. N. Tantawi. Dynamic Application Placement Under Service and Memory Constraints. In International Workshop on Efficient and Experimental Algorithms, 2005.

#### Objective Virtual Machine Placement in Virtualized Data Center Environments

* In this paper, a two-level control system is proposed to manage the mappings of workloads to VMs and VMs to physical resources.
* a multi-objective optimization problem
  * minimizing total resource wastage  资源最小浪费
  * power consumption  电量消耗少
  * thermal dissipation costs 热能消耗(需要冷却系统来保证机房在安全温度)
* 算法
  * An improved genetic algorithm (改进的遗传算法) with fuzzy multi-objective evaluation(模糊的多目标评估？)
  * 目的是：
    * 高效的搜索大的解空间
    * 便于兼备优化的冲突目标
  * 和4个知名的装箱算法(bin-packing)/2个单目标优化方法的比较，从如下几个方面比较
    * power-consumption(电力消耗)
    * thermal-dissipation models
    * good performance
    * scalability
    * robustness
  * 优势
    * 当其他的算法无法做到时，该算法能寻找到优化冲突目标存在的均衡的解
* 使用场景
  * the problem of initial VM placement/VM的初始调度(where a number of requests for VMs are to be placed to the available physical resources.  )
  * 机房刚开始运营、重置、空置后重新启用。有一批VM需求，批量来放置。
  * 一次性放置
  * 尝试搜索最优解
* 优化目标
  * 高效实用多维度资源(CPU/Memory/disk...)
  * 避免热点(hot spots)
  * 减少能量(电能)消耗
  * [不是该论文的目标]在可接受的时间里，找到一个近视最优解(Intelligent search)
  * 目标：搜索全局最优解，模糊逻辑(fuzzy-logic)的评估方法来综合不同的优化目标。？？

* 其他场景
  * Dynamic VM placement，动态放置(迁移)

### 章节详细记录

* [2]background
* [3]framework
* [4]描述问题和提议的解法
* [5]实验结果、分析算法的性能
* [6]相关工作
* [7]总结论文

[2] background

* combinatorial optimization
* multi-objective optimization and fuzzy logic

* combinatorial optimization（组合优化） and genetic algorithms（遗传算法）
  * NP-hard:scheduling/packing/placement
  * Heuristic techniques(启发式算法/方法/技术)，求解近似解      solving optimization problems in an approximate way / global optimal solutions
  * genetic algorithms(遗传算法),能很好的解决 combinatorial problem(组合问题)

[4]

* Grouping Genetic Algorithm
* ranking-crossover, 不直接使用随机的crossover

#### 虚拟化的收益

  > 降低成本，更少的机器、更少的电力消耗，更少的冷却系统，物理空间等

  ### 启发法(Heuristic techniques)
 * 不保证最优、完美、最合理
 * 足够快速、短期目标、近似解法
 * 搜索最优解释不可能或者不可实现(NP hard),启发法可以用来加速搜索满意的解

### NP hard

  > 很多组合问题(combinatorial problems)被分类为NP-hard
  > * 调度（scheduling）
  > * 装箱(bin packing)
  > * 放置(placement)
  > 遗传算法(genetic algorithms)常被用来解决组合问题

  ### 
  * approximate global optimum 近似全局最优
  * precise local optimum 精确的局部最优

  《A Multi-objective Approach to Virtual Machine Management in Datacenters》
  * dynamic VM placement（动态放置，二次迁移）
    * ThermalEmergency
    * Resource Contention
    * Low Energy Efficiency

  * Condition Detection  （trigger a VM-migration） 
    * 怎么检测准确，避免无效的迁移
  * Virtual Machine Selection (选择要迁移的VM)
    * Thermal Emergency
    * Resource Contention 
    * Low Energy Efficiency
  * Host Selection(迁移的目标机器)
    * Temperature
    * cooling cost
    * Power
    * Performance

 * 其他相关工作
    * VMware’s Distributed Resource Scheduler (DRS) 
      * CPU & Memory
      * 不考虑温度、电力消耗
    * VMware Distributed Power Management (DPM) 
      * 物理机使用的数量
      * 关掉不使用的物理机
      * 不考虑： 资源竞争、热效应、VM迁移的影响

《Dynamic Placement for Clustered Web Applications》
  * use clustering technology to provide scalability, high availability and load balancing.

  * Placement Algorithm 
    * Residual placement
    * Incremental placement
    * Rebalancing placement

  * 评估方法  Evaluation criterion
    * Gini index

《A scalable application placement controller for enterprise data centers》
* within 30 seconds
* solutions for hard placement problems with thousands of machines and thou- sands of applications
* to maximize the total satisfied application demand
* to minimize the number of application starts and stops
* to balance the load across machines.
* 和 state-of-the-art algorithms 对比。
  * 提速 134 倍
  * 减少97%的开、停机
  * 满意度提升25% 
* request router  路由
  * admission control 访问控制
  * flow control 流量控制
  * load balancing 负载均衡
* 抽象为：多项限制的多背包问题。多个优化目标
  * 满足最大量的需求
  * 尽可能少的开、停机
  * 均衡负载
  * This problem is a variant of the Class Constrained Multiple- Knapsack problem

* 动态的启动、停止应用

* bin packing 装箱问题
* multiple knapsack 多重选择背包问题

* 流程
  * 算出一个放置方案
  * 执行器，执行停止、启动任务
  * 定时循环

* 假设
  * 应用没有请求量，也会消耗对应的内存
  * 内存的消耗，memory consumption is often related to prior application usage rather than its current load due to data caching and delayed garbage collection.
  * 

* 简化
  * 只考虑CPU和内存，当然也可以处理其他的资源
  * 

* placement algorithm 具体的放置算法
  * 定时循环优化放置问题
  * 所有的应用都满足，那么就结束
  * 有不满足的，就停止其他不需要的，然后启动需要新需求的
  * 实例运行状态分类
    * idle 空闲
    * underutilized 不完全使用
    * fully utilized  完全使用
  * Key Ideas
    * 同一时间只考虑单独的机器，降低计算时间
    * 只考虑单独机器，放置可能不合理，所以：执行多轮，前面一轮停掉的实例资源，就可以分配给后面一轮的需求
    * 考虑CPU/Memory的比例
    * 减少变更(如：pinned实例，就不会变动)
 * Proof 证明
    * contradiction 使用反正

* The placement-changing 
  * increase the total satisfied application demand

  * 第一尽可能多的满足实例的放置需求
  * 满足的数量一样的话，那就是尽可能少变动实例(不要停止、开启)

* 算法评估
  * performance 
    * execution time
    * the number of placement changes
    * the demand satisfaction
  * 可以支持上千的机器和实例(应用)
  * 实例(应用)的变化也很少(相比其他的算法)
  * 三方面的提高
    * 执行时间 （the strategy that does place- ment changes to machines one by one in an isolated fashion.）
    * 应用的需求满意度 （its load-shifting heuristics and the strategy that first does placement changes to the ma- chines with a high CPU-memory ratio. ）
    * 应用的变化数量 （Two heuristics in the new algorithm help reduce placement changes：application instance pinning and machine isola- tion.）

《Large-scale cluster management at Google with Borg》
* long-running services that should “never” go down(e.g., Gmail, Google Docs)
* for internal infrastructure services (e.g., BigTable)

* 很多系统都是建在Borg之上的
  * MapReduce system
  * FlumeJava
  * Millwheel
  * Pregel
  * GFS/CFS, BigTable
  * Megastore

* 分为两类系统
  * production（prod）
  * non-production(non-prod)

* 中等规模
  * 10k machines

* 限制/约束 分强、弱(hard/soft)

* 相关工作
  * Facebook’s Tupperware
  * Twitter's Aurora
  * Microsoft's Autopilot
  * Microsoft’s Apollo

《Borg, Omega, and Kubernetes》
> Borg 和 Kubernetes 介绍比较多。 Omega相对比较少
>
> * container 管理系统

* Borg-> Omega-> Kubernetes
* Borg 
  * long-running services
  * batch jobs

* 经验教训
  * Don’t make the container system manage port numbers
  * Don’t just number containers: give them labels
  * Be careful with ownership
  * Don’t expose raw state

 《An Overview of Openstack Architecture》

* modular & highly configurable architecture

 * Computing
  * Nova:
  * Glance: Image Service
* Networking
  * Neutron: networking
    * DHCP
    * IP's
    * VLAN's
* Storing
  * Swift:Openstack Object Storage
  * Cinder:Openstack Block Storage & Cinder Volumes
* Shared services
  *Keystone: authentication
  * Horizon：dashboard
  * Ceilometer：configurable
  * Advanced Message Queue Protocol：messaging

  《Dynamic Resource Allocation with Management Objectives— Implementation for an OpenStack Cloud》
  * a set of controllers that allocate resources to applications
  * cooperate to achieve an activated management objective
  * Management objectives define the strategies according to which resources are allocated to applications.
    * balanced load objective
    * minimizing power consumption
    * fair resource allocation
    * 【】want to satisfy several management objectives at the same time
    * an optimization problem.
      * colocation constraint
      * anti-colocation constraint

* descheduling & coscheduling

* Related work
  * VSphere’s resource management system is the Distributed Resource Scheduler (DRS)
  * Microsoft Sys- tems Center (MSC)

  * OpenStack
    * Nova 计算
      * API(http)
      * compute(Rpc)
      * conductor(Rpc)
      * Nova-scheduler(Rpc)
        * 依赖placement
        * 水平扩展能力和方案
        Both schedulers are able to scale horizontally, so for high-availability purposes, or for very large or high-schedule-frequency installations, 
        you should consider running multiple instances of each scheduler. 
        The schedulers all listen to the shared message queue, so no special load balancing is required.
      * Queue

    * placement
      * migration
    * Cinder Scheduler

    * Keystone: Authentication service.
    * Glance: mirroring service.
    * Nova: Computing services.
    * Cinder: Block storage service.
    * Neutorn: Network service.
    * Swift: Object storage service.
  
  * 无状态(stateless) & 扩展(scaling)
    [Nova](https://fuel-ccp.readthedocs.io/en/latest/design/ref_arch_100_nodes.html#openstack-compute-nova)

  * read nova source code https://www.programmersought.com/article/57984562657/

  * Distributed Computing
    * In parallel computing, all processors may have access to a shared memory to exchange information between processors.
    * In distributed computing, each processor has its own private memory (distributed memory). Information is exchanged by passing messages between the processors.

  * [CFS-Completely Fair Scheduler](https://www.kernel.org/doc/html/latest/scheduler/sched-design-CFS.html)
