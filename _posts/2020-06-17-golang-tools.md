---
layout: post
keywords: golang 
description: golang's sdk and tools 
title: "golang 开发环境"
categories: [golang]
tags: [golang]
---
{% include codepiano/setup %}


```shell
// get the latest version of rsc.io/sampler
$ go get rsc.io/sampler

// list the available tagged versions of sampler
$ go list -m -versions rsc.io/sampler
rsc.io/sampler v1.0.0 v1.2.0 v1.2.1 v1.3.0 v1.3.1 v1.99.99

// get the specific version of sampler
$ go get rsc.io/sampler@v1.3.1

```