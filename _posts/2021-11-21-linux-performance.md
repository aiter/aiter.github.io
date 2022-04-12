---
layout: post
keywords: linux
description: linux performance
title: "linux performance"
categories: [linux]
tags: [linux,vmstat,pidstat,iostat]
---
{% include codepiano/setup %}

## linux 性能分析

## cpu 信息

us - Time spent in user space
sy - Time spent in kernel space
ni - Time spent running niced user processes (User defined priority)
id - Time spent in idle operations
wa - Time spent on waiting on IO peripherals (eg. disk)
hi - Time spent handling hardware interrupt routines. (Whenever a peripheral unit want attention form the CPU, it literally pulls a line, to signal the CPU to service it)
si - Time spent handling software interrupt routines. (a piece of code, calls an interrupt routine...)
st - Time spent on involuntary waits by virtual cpu while hypervisor is servicing another processor (stolen from a virtual machine)

* vmstat : Report virtual memory statistics

> processes, memory, paging, block IO, traps, disks and cpu activity

* mpstat
* pidstat
* iostat

* cgroup
* cfs_period/quota
* cpu shares
* Cpusets
* cfs/rt

## Gcc & Clang/LLVM

[cgroup](https://www.kernel.org/doc/html/latest/admin-guide/cgroup-v2.html)

[clang-and-llvm-and-gcc](https://stackoverflow.com/questions/24836183/what-is-the-difference-between-clang-and-llvm-and-gcc-g)

[cpusets](https://www.kernel.org/doc/Documentation/cgroup-v1/cpusets.txt)

[Creating and organizing cgroups](https://facebookmicrosites.github.io/cgroup2/docs/create-cgroups.html)

[cgroup 基本概念](https://mp.weixin.qq.com/s?__biz=MzU1MzY4NzQ1OA==&mid=2247484140&idx=1&sn=c18a86d6a2d426f4d627dafd85f5ae3a&chksm=fbee4221cc99cb370fd50af1c21d504b547b8f1e052fb16dc1755df5695b4acc34c48abd825e&token=1393898211&lang=zh_CN&scene=21#wechat_redirect)

[LVS](https://cloud.tencent.com/developer/article/1115754)

[worker_cpu_affinity](http://nginx.org/en/docs/ngx_core_module.html#worker_cpu_affinity)

[I’ll Do It Later: Softirqs, Tasklets, Bottom Halves, Task Queues,
Work Queues and Timers](https://www.cs.unca.edu/brock/classes/Spring2013/csci331/notes/paper-1130.pdf)
