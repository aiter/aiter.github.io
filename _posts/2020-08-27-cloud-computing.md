---
layout: post
keywords: Cloud 
description: Cloud computing
title: "云计算"
categories: [cloud]
tags: [cloud]
---
{% include codepiano/setup %}

* enterprise cloud (single organization)
* public cloud (man organizations)

## History

* "cloud computing" appeared as eayly as 1996.
* 2006 AWS的EC2(Elastic Compute Cloud)
* 1960s, time-sharing(时分)

## Types

### IaaS (Infrastructure as a Service)

### PaaS (Platform as a Service)

### SaaS (Software as a Service)

## Cloud Native

* Containerization
* CI/CD
* Orchestration & Application definition
* Observability & Analysis
* Service proxy, Discovery & Mesh
* Networking, Policy & Security
* Distributed database & Storage
* Streaming & Messaging
* Container Registry & Runtime
* Software distribution

### The Twelve-Factor Application

* 弹性伸缩
* 集群中Node的伸缩
* pod的伸缩
* 可观测性

* 消息队列
* request/response messaging
* request/reply
* command
* Event bus

### Cloud-native data patterns

* CAP
* Consistency
* Availability
* Partition Tolerance

* Relational database systems: CA(Consistency & Availability)
* NoSQL databases: AP(abailability * Partition Tolerance)

* Cloud-native resiliency
* Monitoring and health
* logging/monitoring/alerts
* Logging with Elastic Stack
* Monitoring in Azure Kubernetes Services(Prometheus)

* Cloud-native identity/security
* DevOps

[cloud-native](https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/definition)

## 2015-CHASE- Component High Availability-Aware Scheduler in Cloud Computing Environment

## 2013-Apache Hadoop YARN- Yet Another Resource Negotiator

* Apache Hadoop
* RM(Resource Manager)

> * tracks resource usage
> * node liveness
> * enforces allocation invariant
> * arbitrate contention

* NM(Node manager)
* AM(Application Manager)

* YARN framework/application writers

* YARN in the real-world
* YARN at Yahoo!
* MapReduce

* availability-aware scheduling technique

## Fuxi ParSync

* distributed cluster scheduler
* sharding & multiple schedulers
* Workload statistics
* 4 millon jobs & 4 billon tasks
* 87% of tasks are completed in less than 10 seconds
* Partitioned Synchronization

## Omega: flexible, scalable schedulers for large compute clusters

* Shared state
* optimistic concurrency

* 3.1 Monolithic schedulers
* 3.2 Statically partitioned schedulers
* 3.3 Two-level scheduling(Mesos) YARN
* 3.4 Shared state(Omega)
* fuxi is similar to Omega?
* how to syn state
* kubernetes's scheduler
* 异构资源 GPU

## Benefits

* 灵活 Flexible
* 弹性 Scalable
* 节约成本 Cost effective

## CDN

* Akamai
* google CDN
* microsoft azure CDN
* AWS CDN

## Compute

* CPU
* GPU
* FPGA
* TPU
* ASIC

## OpenStack

* nova(Compute)
* scheduler
  * [Scheduler Evolution](https://docs.openstack.org/nova/rocky/reference/scheduler-evolution.html)  
  * [Filter Scheduler](https://docs.openstack.org/nova/rocky/user/filter-scheduler.html)
    * filtering:一个过滤器集合
    * weighting:排序
  * nova-scheduler是nova(compute)的一部分
  * nova使用scheduler来决定怎么分发(dispatch)资源的请求。VM在那一台物理机上运行。
  * 过滤器(filters)
    * 是否在指定的AZ、CPU/Memory/disk/architecture/hypervisor/vm mode/亲和性(Affinity)/反亲和性(AntiAffinity)
* placement: 库存，提供API
  * resource provider inventories and usages. tracks the inventory and usage of each provider
  * compute node
  * shared storage pool
  * IP allocation pool
  * 有标准的DISK/MEMORY/VCPU，也可以自定义分类(custom resource classes )
  * nova-compute(注册、删除、管理) 和 nova-scheduler(调度)会和placement交互

* scheduler提供调度的服务器和备选服务器 [link](https://docs.openstack.org/nova/rocky/reference/scheduling.html)
* 组件(componets)关系
  * nova-api  ----RPC--->  super conductor
  * 还有cell conductors/cell-local conductors
  * super conductor 发送请求给 scheduler（不是cell conductors）
  * conductor 调度完成后，再发送生产请求到 nova-compute
  * 生产包含：网络port、磁盘、虚拟机
[Walkthrough of a typical Nova boot request](https://github.com/jaypipes/articles/blob/master/openstack/walkthrough-launch-instance-request.md#call-scheduler-select-destinations)

### 组件关系

* Horizon(Dashboard) / OpenAPI 对外界面
* keystone  认证
* nova 计算API、实例管理API  （计算）
* swift  对象存储    （存储-对象）
* cinder 块存储       (存储-块)
* glance 镜像服务      (镜像)
* neutron 网络        (网络)
* cells 可以部署更大的集群，每个cell是个独立的一组数据(相当于一个分片)。`It supports very large deployments.`

> 将集群中的机器分组，分组就是cell，

### NP-hard

* task scheduling
* packing
* placement

> Heuristic techniques 启发式常用于一种近似方式解决优化问题。
>
> * is not guaranteed to be optimal、perfect、rational
> * immediate、short-term goal、approximation
> * derived from previous experiences with similar problems
> * readily accessible 易接近的
> * though loosely applicable 尽管松散的适用

### computer CPU  architecture

* Branch predictor(分支预测) : 尝试猜测程序执行的逻辑，主要目的还是提速，让cpu的指令流水线(instruction pipeline)更快的执行
* Static branch prediction。编译时就确定。
* Dynamic branch prediction。运行时确定。
* Random branch prediction
* Next line prediction
* One-level branch prediction

### process schedule in OS

* Long Term or job scheduler
* Short term or CPU scheduler
* Medium-term scheduler

### cpu schedule in OS

* Arrival Time: Time at which the process arrives in the ready queue.
* Completion Time: Time at which process completes its execution.
* Burst Time: Time required by a process for CPU execution.
* Turn Around Time: Time Difference between completion time and arrival time.
* Turn Around Time = Completion Time – Arrival Time
* Waiting Time(W.T): Time Difference between turn around time and burst time.
* Waiting Time = Turn Around Time – Burst Time

### Objectives of Process Scheduling Algorithm

* Max CPU utilization [Keep CPU as busy as possible]
* Fair allocation of CPU.
* Max throughput [Number of processes that complete their execution per time unit]
* Min turn around time [Time taken by a process to finish execution]
* Min waiting time [Time a process waits in ready queue]
* Min response time [Time when a process produces first response]

### Scheduling Algorithms

* First Come First Serve (FCFS)
* Shortest Job First (SJF)
* Longest Job First (LJF)
* Shortest Remaining Time First (SRTF)
* Longest Remaining Time First (LRTF)
* Round Robin Scheduling [the time-sharing system]
* Priority Based scheduling (Non-Preemptive)
* Highest Response Ratio Next (HRRN)
* Multilevel Queue Scheduling
* Multi level Feedback Queue Scheduling

* kube-scheduler
  * List-Watch
  * scheduling
  * binding

## Guidelines to follow when creating architectural diagrams

* Keep structural and semantical consistency across diagrams/保持各图的结构和语义的一致性
* Prevent diagrams fragmentation/防止图示碎片化
* Keep traceability across diagrams/保持跨图表的可追溯性
* Add legends next to architectural diagrams/在建筑图旁添加图例

* Application architecture diagram
* Integration architecture diagram
* Deployment architecture diagram
* DevOps architecture diagram
* Data architecture diagram
* shaps lines arrow
* diagram legend

> a picture is worth a thousand words

* sh
* bash
* zsh
* ksh

### vlan & vxlan

### Function compute

### References

* [1] [Dynamic Resource Allocation by Using Elastic Compute Cloud Service](http://www.rroij.com/open-access/dynamic-resource-allocation-by-using-elasticcompute-cloud-service.pdf)
* [2] [Cloud Computing Resource Scheduling and a Survey of Its Evolutionary Approaches](https://core.ac.uk/download/pdf/296173442.pdf)
* [3] [architectural-diagrams](https://www.infoq.com/articles/crafting-architectural-diagrams/)
* [4] [Design for scalability](https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/infrastructure-resiliency-azure)
* [5] [Predictive Scaling for EC2, Powered by Machine Learning](https://aws.amazon.com/blogs/aws/new-predictive-scaling-for-ec2-powered-by-machine-learning/)
* [6][aws lambda](https://aws.amazon.com/lambda/)
* [7] [GCP Funtions]
* [8] [how exxx function works]
