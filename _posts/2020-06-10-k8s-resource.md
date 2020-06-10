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