---
layout: post
keywords: k8s 
description: kubernetes's scheduler
title: "kubernetes调度器scheduler"
categories: [云原生]
tags: [k8s,kubernetes,scheduler]
---
{% include codepiano/setup %}

## 默认调度器
* 可以运行在一个pod中
* 监听pod的创建需求
* 获取Node列表，并调度
* 绑定pod和Node关系(告诉给API Server)

## 和API的关系
* 独立的服务
* 通过API的结果，监听、获取数据、提交绑定关系数据

## 自定义调度器
> 常用流量

* 实现类似默认调度器的逻辑
* 运行自定义调度器(pod)方式
* 调度其他pod时，指定自定义调度器的名称

## taint & tolerant

[scheduler](https://kubernetes.io/docs/concepts/scheduling-eviction/kube-scheduler/)