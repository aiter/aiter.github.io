---
layout: post
keywords: tty console terminal 
description: 
title: "tty console terminal"
categories: [tool]
tags: [tty, console, terminal]
---
{% include codepiano/setup %}

## 历史
* 1830s年代，出现了电报，后面出现发送电报使用的teleprinter (teletypewriter, teletype or TTY)，用来发送和接手信息。
* 1950s年代，大型机出现，只有console操作面板(没有键盘、没有显示器)
<img src="/image/tty_console_terminal_1.jpg" />
图片[来源](https://www.zhihu.com/question/21711307)
* 1960s年代，小型机出现
* 使用teletypewriter作为大型机和小型机的输入、输出设备
    * 使用物理线缆连接TTY和机器的物理插口
    * 给机器的系统写一个驱动器(driver，这里留意一下这个TTY driver)
* 微型机的出现，键盘、服务器的出现，不在需要TTY。操作系统在内核中，写了一个terminal emulator。不再使用TTY这样的物理设备。
    * 终端模拟软件
    * VT100 VT220  XTerm等
* 现在常用ssh登录到一台远程服务器上。pseudo terminal的出现
    * pseudo terminal分为2部分，master部分(ptmx)，slave部分(pts/0,pts/1)

## 定义
console
> 最开始的大型机、小型机，机器上有自有的控制台
> a flat board that contains the controls for a machine, piece of electrical equipment, computer etc
> 机器、电器设备、电脑的控制台、操作台
<img src="/image/tty_console_terminal_1.jpg" />
图片[来源](https://www.zhihu.com/question/21711307)

tty
```
+----------+     Physical Line     +----------+
| teletype |<--------------------->| teletype |
+----------+                       +----------+
```
> tty本身就是一种终端，teletypewriter。
> 一种特定的设备文件(一切皆是文件)，基本和terminal相同的意思。tty是计算机系统操作的文件,terminal是文件另一端的设备。
> 内核提供一些针对键盘、显示器这样的tty。另一些是伪tty,有仿真终端程序提供。
tty 子系统
```
    +-----------------------------------------------+
    |                    Kernel                     |
    |                                 +--------+    |
    |   +--------+   +------------+   |        |    |       +----------------+
    |   |  UART  |   |    Line    |   |  TTY   |<---------->| User process A |
<------>|        |<->|            |<->|        |    |       +----------------+
    |   | driver |   | discipline |   | driver |<---------->| User process B |
    |   +--------+   +------------+   |        |    |       +----------------+
    |                                 +--------+    |
    |                                               |
    +-----------------------------------------------+
```
TTY设备
```
                      +----------------+
                      |   TTY Driver   |
                      |                |
                      |   +-------+    |       +----------------+
 +------------+       |   |       |<---------->| User process A |
 | Terminal A |<--------->| ttyS0 |    |       +----------------+
 +------------+       |   |       |<---------->| User process B |
                      |   +-------+    |       +----------------+
                      |                |
                      |   +-------+    |       +----------------+
 +------------+       |   |       |<---------->| User process C |
 | Terminal B |<--------->| ttyS1 |    |       +----------------+
 +------------+       |   |       |<---------->| User process D |
                      |   +-------+    |       +----------------+
                      |                |
                      +----------------+
```

键盘显示器连接
> 使用 Terminal Emulator 
```
                   +-----------------------------------------+
                   |          Kernel                         |
                   |                           +--------+    |       +----------------+ 
 +----------+      |   +-------------------+   |  tty1  |<---------->| User processes |
 | Keyboard |--------->|                   |   +--------+    |       +----------------+
 +----------+      |   | Terminal Emulator |<->|  tty2  |<---------->| User processes |
 | Monitor  |<---------|                   |   +--------+    |       +----------------+
 +----------+      |   +-------------------+   |  tty3  |<---------->| User processes |
                   |                           +--------+    |       +----------------+
                   |                                         |
                   +-----------------------------------------+
```

SSH连接方式
```
 +----------+       +------------+
 | Keyboard |------>|            |
 +----------+       |  Terminal  |
 | Monitor  |<------|            |
 +----------+       +------------+
                          |
                          |  ssh protocol
                          |
                          ↓
                    +------------+
                    |            |
                    | ssh server |--------------------------+
                    |            |           fork           |
                    +------------+                          |
                        |   ↑                               |
                        |   |                               |
                  write |   | read                          |
                        |   |                               |
                  +-----|---|-------------------+           |
                  |     |   |                   |           ↓
                  |     ↓   |      +-------+    |       +-------+
                  |   +--------+   | pts/0 |<---------->| shell |
                  |   |        |   +-------+    |       +-------+
                  |   |  ptmx  |<->| pts/1 |<---------->| shell |
                  |   |        |   +-------+    |       +-------+
                  |   +--------+   | pts/2 |<---------->| shell |
                  |                +-------+    |       +-------+
                  |    Kernel                   |
                  +-----------------------------+
```

键盘显示器连接(图形界面)
> 通过图形界面的Terminal软件 （注意和 键盘显示连接  的区别）
> * 使用pseudo terminal (ptmx & pts)
```
 +----------+       +------------+
 | Keyboard |------>|            |
 +----------+       |  Terminal  |--------------------------+
 | Monitor  |<------|            |           fork           |
 +----------+       +------------+                          |
                        |   ↑                               |
                        |   |                               |
                  write |   | read                          |
                        |   |                               |
                  +-----|---|-------------------+           |
                  |     |   |                   |           ↓
                  |     ↓   |      +-------+    |       +-------+
                  |   +--------+   | pts/0 |<---------->| shell |
                  |   |        |   +-------+    |       +-------+
                  |   |  ptmx  |<->| pts/1 |<---------->| shell |
                  |   |        |   +-------+    |       +-------+
                  |   +--------+   | pts/2 |<---------->| shell |
                  |                +-------+    |       +-------+
                  |    Kernel                   |
                  +-----------------------------+
```

pty
> pseudo terminal
> * PTY slave  (shell(bash/zsh...))
> * PTY master (terminal emulator (XTerm)) 监听键盘等输入、输出显示内容到XTerm等模拟终端
> * tty driver 是master和slave的桥梁
> * shell 是一个用户态的程序，可以启动子进程(如：cat)来和内核交互。

## links
[终端、Shell、tty 和控制台（console）有什么区别？](https://www.zhihu.com/question/21711307)
[命令行界面 (CLI)、终端 (Terminal)、Shell、TTY，傻傻分不清楚？](https://segmentfault.com/a/1190000016129862)
[What is the exact difference between a 'terminal', a 'shell', a 'tty' and a 'console'?](https://unix.stackexchange.com/questions/4126/what-is-the-exact-difference-between-a-terminal-a-shell-a-tty-and-a-con)
[Linux TTY、PTS、PTY详解](https://my.oschina.net/u/3477605/blog/3025534)