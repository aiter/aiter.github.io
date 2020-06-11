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

|NAME|SHORTNAMES|APIGROUP|NAMESPACED|KIND|
|---|---|---|---|---|
|nodes| no|| false| Node|
|pods|po||true|Pod|
|crontabs| ct|stable.example.com| true| CronTab|