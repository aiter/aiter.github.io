---
layout: post
keywords: k8s 
description: kubernetes's resource
title: "kubernetes资源"
categories: [云原生]
tags: [k8s,kubernetes,crd,resource]
---
{% include codepiano/setup %}

## resource

### Deployment

 kubectl apply -f https://k8s.io/examples/application/deployment.yaml
  kubectl describe deployment nginx-deployment

## Nodes

### components

* kubelet
* kube-proxy
* container runtime

### Node Capacity

> * 如果是自动注册入cluster，同时提交memory，cpu等node的能力
> * 如果是手动加入，那么需要手动设置
> * 调度器scheduler保证所有容器的资源需求不大于节点的资源能力
> * 总量只是被kubelet管理的容器，不包括直接启动的容器，也不包括其他非kubelet控制的进程(也占资源)

## Pods

|NAME|SHORTNAMES|purpose|
|---|---|---|
|pods|po||
|services|svc||

> k8s的最小管理和调度单元，一个pod中可以有1个或多个容器。这些容器共享网络、存储

## Volumes 存储

### Persistent Volumes(PV)

### Persistent Volumes Claim(PVC)

## Service

> 一组pods提供的服务。在你的集群中，如果有一组pods提供一种服务(比如检索服务)，但是pods会不断的更新、销毁后重启拉起，使用这组
> 服务的其他服务，如何马上切换到最新的pods机器ip上去呢？ service解决这样的问题。

* service --> Pods
* service --> your own service(like database,不是部署在k8s中的)
* service --> service(其他的Namespace)
* 非指向pods的service，需要指定Endpoints(也就是具体的ip和端口)，这里需要注意哪些ip是不能指定到Endpoints中的，比如另一个service的虚拟ip

### kube-proxy

#### iptables mode

* by Linux netfilter (不需要用户态、内核态切换)
* 可靠性高

#### IPVS proxy mode

* call netlink interface to create IPVS rules
* is based on netfilter hook function. 和iptables相似，工作于内核态，使用了hash表
* 更低的时延(lower latency)，更高的性能（better performance）
* 支持更高的吞吐量(throughput)
  * rr: round-robin  轮询
  * lc: least connection (smallest number of open connections)  最少链接
  * dh: destination hashing  目的地址hash
  * sh: source hashing  源地址hash
  * sed: shortest expected delay  最小延迟
  * nq: never queue 不进等待队列？？

> Note: IPVS是一个内核模块，启动kube-proxy之前，确保IPVS可用。

### 服务发现 Discovering services

* 环境变量
* DNS

> 更好的方式,DNS Server(CoreDNS/kube-dns),原理也是watch k8s的API

    * $service_name$.$namespace$

### Headless Services

## NetworkPolicy

> pods之间是否都运行访问呢？

* ingress
* egress

## 网络相关

* Pod 网络组件，给pod提供网络(CNI),pod之间的网络交互。 Calico
* DNS ，必须有Pod网络，DNS才能工作
* NetworkPolicy 网络的ACL 
* Calico，a networking and network policy provider.

## k8s组件

* worker node(nodes/worker machines)
* Pods

### 控制面的组件

* Master Nodes
  * kube-apiserver, 水平扩展，可部署多个
  * etcd, 保存持久化数据
  * kube-scheduler，监听没有指定具体node的Pod新建需求，调度选择一个node给这个新pod。
    * 资源需求
    * 硬件/软件/策略限制/亲和性/反亲和性/数据位置/工作负载/
  * kube-controller-manager。 本质上是多个controller,为了降低复杂度，编译成了一个二进制执行文件，并单进程运行。
    * Node controller：node节点宕机(下线)通知
    * Replication controller : 维持pods的数量
    * Endpoints controller： 加入的services和pods
    * 服务Account & Token 控制器：给新的命名空间创建默认的账号和访问tokens
* worker Nodes
  * kubelet
  * kube-proxy
  * Container runtime
    * Docker
    * containerd
    * CRI-O
    * 其他的一个对CRI的实现(只要实现Container Runtime Interface标准的都可以)

## 插件 Addons

> 利用k8s的资源(DaemonSetEnsures, Deployment等等)来实现计算特性，这些都是集群的特性，所以放在kube-system的命名空间里。

* DNS
* Web UI(Dashboard)
* 容器资源监控
* 集群级别的日志

## k8s API

> 暴露http的接口。终端用户、集群中的不同部分、其他一些组件

### API如何兼容老版本

### spec 和 status

> 申明式

## Controllers

> 在k8s中，控制器不断循环观察集群的状态。每个控制器都不断将当前的集群状态逼近期望的状态

|NAME|SHORTNAMES|purpose|
|---|---|---|
|ReplicaSet|rs|maintain a stable set of replica Pods running at any given time|
|ReplicationController|rc|a specified number of pod replicas are running at any one time|
|Deployments|deploy|provides declarative updates for Pods and ReplicaSets. 部署升级|
|HorizontalPodAutoscaler|hpa||

## CRD(Custom Resource Definition)

* 定义一个yaml文件
  * kind: CustomResourceDefinition
  * 其他信息
* $kubectl api-resources 可以看到自定义的资源类型 [doc](https://kubernetes.io/docs/tasks/access-kubernetes-api/custom-resources/custom-resource-definitions/) 

### 创建CRD的过程

1. 创建CRD, 让k8s‘认识’我们自定义的API对象
2. 编写基础代码，使用代码工具生成controller之外的代码
3. 编写controller代码
4. 编译代码

|NAME|SHORTNAMES|APIGROUP|NAMESPACED|KIND|
|---|---|---|---|---|
|nodes| no|| false| Node|
|pods|po||true|Pod|
|crontabs| ct|stable.example.com| true| CronTab|

## docker

[docker instructions](https://docs.docker.com/engine/reference/builder/#from)
