---
layout: post
keywords: Cloud 
description: Cloud computing
title: "云计算"
categories: [cloud]
tags: [cloud]
---
{% include codepiano/setup %}

## 
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

## Benefits
* 灵活
* 弹性
* 节约成本

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
* nove(Compute)
* scheduler
    *  [Scheduler Evolution](https://docs.openstack.org/nova/rocky/reference/scheduler-evolution.html)  
    * [Filter Scheduler](https://docs.openstack.org/nova/rocky/user/filter-scheduler.html)
        * filtering:一个过滤器集合
        * weighting:排序

## 
### NP-hard
* task scheduling 
* packing 
* placement

> Heuristic techniques 启发式常用于一种近似方式解决优化问题。
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