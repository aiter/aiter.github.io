---
layout: post
keywords: serverless 
description: AWS Fargate
title: "AWS Fargate"
categories: [serverless]
tags: [k8s,kubernetes,serverless]
---
{% include codepiano/setup %}

## what is Farget
> AWS Fargate is a **serverless** compute engine for **containers** that works with both Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS). Fargate makes it easy for you to focus on building your applications. Fargate removes the need to provision and manage servers, lets you specify and pay for resources per application, and improves security through application isolation by design.

> * You only pay for the resources required to run your containers
> * 独立的内核 & 安全隔离 

## 收益
* 部署管理自己的应用，不在管理基础设施(VM)
* 便宜，也可以使用竞价实例(spot)，用多少付多少
* 安全隔离

## EC2对比
* 不需要管理VM(EC2 客户自己管理)
* Fargate 按每秒付费
* 运行的任务和EC2中的类似，也可以加入VPCs,LB,IAM

## 推荐场景
* Machine Learning 
* CI/CD pipelines
* Serverless 


## FireCracker
> Secure and Fast microVM for Serverless Computing

* 解决overhead (对比VM,EC2),管理成本高
* 事件驱动的场景(有事件，才需要计算，计算完成，释放资源)
* 既要安全隔离，又要小的overhead

* 使用KVM(Linux Kernel-based Virtual Machine)
* 微VM
* 安全、速度、效率
    * 只启动必须的linux内核
    * 指定特定的内核编译参数(内核编译有1000+项参数)
    * 不支持图形功能及图形加速器？
    * 不支持硬件直通？(passthrough)
    * 只支持 virtio net 和 virtio block




## links
[Secure and Fast microVM for Serverless Computing](https://aws.amazon.com/blogs/opensource/firecracker-open-source-secure-fast-microvm-serverless/)
