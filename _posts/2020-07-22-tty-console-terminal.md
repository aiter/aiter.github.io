---
layout: post
keywords: tty console terminal 
description: 
title: "tty console terminal"
categories: [tool]
tags: [tty, console, terminal]
---
{% include codepiano/setup %}

## 定义
console
> a flat board that contains the controls for a machine, piece of electrical equipment, computer etc
> 机器、电器设备、电脑的控制台、操作台
<img src="/image/tty_console_terminal_1.jpg" />
图片[来源](https://www.zhihu.com/question/21711307)

terminal
> 键盘、显示器这样的终端。text的输入输出环境

tty
> tty本身就是一种终端，teletypewriter。
> 一种特定的设备文件(一切皆是文件)，基本和terminal相同的意思。tty是计算机系统操作的文件,terminal是文件另一端的设备。
> 内核提供一些针对键盘、显示器这样的tty。另一些是伪tty,有仿真终端程序提供。

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