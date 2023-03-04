---
layout: post
keywords: golang 
description: golang's sdk and tools 
title: "golang 开发环境"
categories: [golang]
tags: [golang]
---
{% include codepiano/setup %}

## go docs

> 表达力强、简洁、干净、高效

Module
  |__package
  |__package

## Go Modules

> [golang.org](https://blog.golang.org/using-go-modules)

### 新项目初始化Module

```shell
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

### go build/install

```shell
$go env -w GOBIN=/path/to/your/bin
$go build
$go install
$go list -f '{{.Target}}'
```

### 使用本地项目替换远程module

```shell
go mod edit -replace example.com/greetings=../greetings
```

* 这串数字代表什么？ require example.com/greetings v0.0.0-00010101000000-000000000000

The number following the module path is a *pseudo-version number* -- a generated number used in place of a *semantic version number* (which the module doesn't have yet).

### 移除不使用的

```shell
$go mod tidy
```

### go mod 还可以直接把依赖的包，复制到vendor中

```shell
$go mod vendor
```

### 让vs code 识别到vendor目录

在vscode的setting中加入配置

```json
{
    "go.toolsEnvVars": {
        "GOFLAGS": "-mod=vendor"
    }
}
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

### array & slice

* array
* slice

### channel

* channel

```golang
   ch := make(chan int)
```

* buffered channel

```golang
   ch := make(chan int, 2)
```

### pool

### system modules

### testing framework

> * Unit Test
> * Benchmark Test

### 协程与锁

* on the train

* 泛型

[Goroutines](https://golangbot.com/goroutines/)
