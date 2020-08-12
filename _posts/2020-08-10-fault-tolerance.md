---
layout: post
keywords: 限流,fault tolerance
description: 服务高可用 fault tolerance
title: "服务高可用，限流、降级"
categories: [service]
tags: [service,fault]
---
{% include codepiano/setup %}

## 使用场景
随着服务架构的演进，现在一项服务基本都是分布式的架构，多个微服务可能彼此调用。
限流、服务降级、服务熔断主要使用词场景和目的是什么？

+----------------+           
|                |            
|   Service  A   | -----+  
|                |      |     
+----------------+      |     +----------------+
                        |---->|                |
+----------------+            |   Service  D   |
|                |      |---->|                |
|   Service  B   | -----+     +----------------+ 
|                |            
+----------------+          

* Service D 保护自己，限流
* Service A/B 因为D的问题，要服务降级、熔断


## Hystrix
> * latency tolerance
> * fault tolerance

## 流程图
<img src="/image/hystrix-command-flow-chart.png" />


## links
[Hystrix](https://github.com/Netflix/Hystrix/wiki)
[Resilience4j](https://github.com/resilience4j/resilience4j)
