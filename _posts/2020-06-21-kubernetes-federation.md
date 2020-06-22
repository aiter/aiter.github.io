---
layout: post
keywords: k8s 
description: kubernetes's federation
title: "k8s federation"
categories: [云原生]
tags: [k8s,kubernetes,federation]
---
{% include codepiano/setup %}

## what is federation
> [github](https://github.com/kubernetes-sigs/kubefed)
> 
> * manage multiple, disparate Kubernetes clusters 
<img src="/image/k8s_federation.png" />

## Kubernetes Multi-cluster vs. Multi-tenant vs. Federation
* Kubernetes Multi-tenancy ： usually namespaces

### examples
```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: nginx-test
---
apiVersion: types.kubefed.io/v1beta1
kind: FederatedNamespace
metadata:
  name: nginx-test
  namespace: nginx-test
spec:
  placement:
    clusters:
    - name: cluster1
    - name: cluster2
    - name: cluster3
```

```yaml
apiVersion: types.kubefed.io/v1beta1
kind: FederatedDeployment
metadata:
  name: nginx-test
  namespace: nginx-test
spec:
  template:
    metadata:
      labels:
        app: nginx
    spec:
      replicas: 4
      selector:
        matchLabels:
          app: nginx
      template:
        metadata:
          labels:
            app: nginx
        spec:
          containers:
          - image: nginx
            name: nginx
  placement:
    clusters:
    - name: cluster1
    - name: cluster3
```
<img src="/image/k8s_federation_2.png" />