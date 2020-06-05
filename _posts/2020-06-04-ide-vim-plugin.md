---
layout: post
keywords: vim 
description: ide、vim
title: "vim开发环境"
categories: [tools]
tags: [vim，tools，ide]
---
{% include codepiano/setup %}



## ctags 
* 使用`ctrl+]` 跳到方法定义或实现的地方    # cscope也提供
* 输入一个”对象“时 `foo. or foo->` 自动提示  # cscope不提供

### 使用方式
> ctags -R  #将源文件(.c .cpp), 构建成tag文件
* 使用`ctrl+]`跳到方法定义或实现的地方,`ctrl+t`返回
* :tag tag1 直接跳到对应的tag
* vim -t main   直接vim打开对应的tag文件，并将光标跳转到对应的行位置

## cscope
> [Cscope](http://cscope.sourceforge.net/)
### cscope特性
* 像ctags一样 `ctrl+]`,使用 `set cscopetag`
* 还提供当前方法，被调用的地方，可以跳转到调用位置
* 搜索
    * 文本
    * 正则
    * 文件
    * 函数及调用函数
### 使用方式
> cscope -Rbq  ## 产生对应的文件，供vim使用



## golang 开发插件
### vim-go
> * [vim-go github](https://github.com/fatih/vim-go)
> * vim-go requires at least Vim 8.0.1453 or Neovim 0.4.0.
#### 主要功能
> 本身go命令有很多功能，比如：go doc fmt  / go doc fmt.Print，将一些功能直接添加到vim中。
* 编译: Build/Install/Test/TestFUnc
> go build/ go install /go test /go testfunc
* 运行: Run 当前文件  `go run`
* 语法高亮 & 代码折叠
* 调试工具   delve(:GoDebugStart)
* gopls工具集合
* :GoDef  跳到定义的地方(变量、方法定义)
> * vim 里面支持的Ctrl+]，原理是vim的tag(:help tag)，我们可以添加很多的tag，比如，一个程序里的方法名就可以是一个tag，但是生效之前，你必须生成tag(tag和文件的关系)，可以使用`ctags`来生成这个tags。要返回原来标签的位置使用`Ctrl+T or Ctrl+O`
> * go源文件支持的'ctrl+]'不是tags来支持，但是要使用`:tag tag1`，这里是根据tags文件来定位的
* 文档 :GoDoc or :GoDocBrowser
* 依赖包引入   :GoImport     :GoDrop
* 其他
```shell
    :GoRename
    :GoCoverage
    :GoAddTags  :goRemoveTags
    :GoLint  :GoVet  :GoErrCheck
    source analysis tools  guru     :GoImplements   :GoCallees   :GoReferrers
```

### 使用方法
* :GoInstallBinaries 安全vim-go依赖的一些工具
完整的文档地址[doc/vim-go.txt](https://github.com/fatih/vim-go/blob/master/doc/vim-go.txt). vim中使用 :help vim-go.

### 添加go相关的tags
修改ctags配置  ~/.ctags
```shell
--langdef=Go
--langmap=Go:.go
--regex-Go=/func([ \t]+\([^)]+\))?[ \t]+([a-zA-Z0-9_]+)/\2/d,func/
--regex-Go=/var[ \t]+([a-zA-Z_][a-zA-Z0-9_]+)/\1/d,var/
--regex-Go=/type[ \t]+([a-zA-Z_][a-zA-Z0-9_]+)/\1/d,type/
```


## 怎样生成tags
* ctags -R

### tags文件格式
> 可以认为是tag对应文件及位置的关系(tag1-->file1.line20)。然后就可以直接跳转到对应的位置。
```cpp
StringUtils StringUtils.cpp /^    StringUtils::StringUtils()$/;"    f   class:lang3::StringUtils
StringUtils StringUtils.h   /^    class StringUtils{$/;"    c   namespace:lang3
 _LANG3_STRINGUTILS_ StringUtils.h   2;" d
isBlank StringUtils.cpp /^    bool StringUtils::isBlank(const std::string &text){$/;"   f   class:lang3::StringUtils
 isEmpty StringUtils.cpp /^    bool StringUtils::isEmpty(const std::string &text){$/;"   f   class:lang3::StringUtils
isNotBlank  StringUtils.cpp /^    bool StringUtils::isNotBlank(const std::string &text){$/;"    f   class:lang3::StringUtils
isNotEmpty  StringUtils.cpp /^    bool StringUtils::isNotEmpty(const std::string &text){$/;"    f   class:lang3::StringUtils
lang3   StringUtils.cpp /^namespace lang3{$/;"  n   file:
lang3   StringUtils.h   /^namespace lang3{$/;"  n
main    StringUtils.cpp /^int main(){$/;"   f
~StringUtils    StringUtils.cpp /^    StringUtils::~StringUtils()$/;"   f   class:lang3::StringUtils
```

```c
CLIF_argument_struct    traceroute-2.1.0/libsupp/clif.h /^struct CLIF_argument_struct {$/;" s
CLIF_call_func  traceroute-2.1.0/libsupp/clif.c /^int CLIF_call_func (CLIF_option *optn, char *arg) {$/;"   f
```

## 最小工具集
* taglist
* minibufexpl
* winmanager