---
layout: post
keywords: golang 
description: golang's sdk and tools 
title: "golang 开发环境"
categories: [golang]
tags: [golang]
---
{% include codepiano/setup %}


## Go Modules
> [golang.org](https://blog.golang.org/using-go-modules)

### 新项目初始化Module
```
$ go mod init example.com/hello

// 使用测试或者build的方式，会自动加载依赖的Module
$ go test
$ go build ./...

//查看，依赖点 Modules
$ cat go.mod

$ go list -m all
```

### 更新依赖
```shell
// get the latest version of rsc.io/sampler
$ go get rsc.io/sampler

// list the available tagged versions of sampler
$ go list -m -versions rsc.io/sampler
rsc.io/sampler v1.0.0 v1.2.0 v1.2.1 v1.3.0 v1.3.1 v1.99.99

// get the specific version of sampler
$ go get rsc.io/sampler@v1.3.1

```

### 移除不使用的

```
$ go mod tidy
```


### go mod 还可以直接把依赖的包，复制到vendor中

```
$ go mod vendor
```

## language

### struct & interface

* 用户自定义类型
* 方法
* 内置类型 & 引用类型
* 接口
* 嵌入类型(内部类型属性提升到外部类型)
* public & private

### goroutine

golang使用逻辑的处理器概念。
