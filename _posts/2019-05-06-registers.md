---
layout: post
keywords: registers
description: registers
title: "汇编语言之寄存器"
categories: [registers]
tags: [asm,registers]
---
{% include codepiano/setup %}


## 计算机体系结构
### CPU

> [Linux C编程一站式学习](https://akaedu.github.io/book/ch17s02.html)

<img src="/image/20190506140053-cpu.jpg" />

> 计算过程中暂存数据

| 寄存器 | 64位 | 32位 | 16位| 说明 |
| --- | --- | --- | --- | --- |
| 累加寄存器 | RAX | EAX | AX  | 通用寄存器|
| 基址寄存器 | RBX | EBX | BX  | 通用寄存器|
| 计数寄存器 | RCX | ECX | AX  | 通用寄存器|
| 数据寄存器 | RDX | EDX | DX  | 通用寄存器|
| 堆栈基指针 | RBP | EBP | BP  | base point 指针变址寄存器|
| 堆栈顶指针 | RSP | ESP | SP  | stack point 指针变址寄存器|
|  | RSI | ESI | SI  | 指针变址寄存器|
|  | RDI | EDI | DI  | 指针变址寄存器|
|  | r8 |  |  |  |
|  | r9 |  |  |  |
|  | r10 |  |  |  |
|  | r11 |  |  |  |
|  | r12 |  |  |  |
|  | r13 |  |  |  |
|  | r14 |  |  |  |
|  | r15 |  |  |  |
> IP寄存器：指令指针寄存器(Instruction Pointer Register),指向代码段下一条指令的位置。

| 寄存器 | 64位 | 32位 | 16位| 说明 |
| --- | --- | --- | --- | --- |
| IP寄存器 | RIP | EIP | IP  | 指向代码段下一条指令|

>段寄存器。每个进程都分代码段和数据段，为了指向不同进程的地址空间。

| 寄存器 | 64位 | 32位 | 16位| 说明 |
| --- | --- | --- | --- | --- |
|Code Segment Register| CS | |CS|代码段寄存器，代码在内存中的位置|
| Data Segment Register | DS | |DS| 数据段寄存器，数据在内存中的位置 |
|Stack Register| SS | |SS|栈寄存器，后进先出的数据结构|
| | ES | |ES| |
|  | fs |  |  |  |
|  | gs |  |  |  |
|  | eflags |  |  | 计算过程中产生的标志位  |
如果运算中需要加载内存中的数据，需要通过DS找到内存中的数据，加载到通用寄存器中。CS、DS都存放这一个段的起始地址。代码的偏移量在IP寄存器中，数据段的偏移量会放在通用寄存器中。
> 《趣谈Linux操作系统》


寻址方式
* 直接寻址（Direct Addressing Mode）。只使用ADDRESS_OR_OFFSET寻址，例如movl ADDRESS, %eax把ADDRESS地址处的32位数传送到eax寄存器。

* 变址寻址（Indexed Addressing Mode） 。上一节的movl data_items(,%edi,4), %eax就属于这种寻址方式，用于访问数组元素比较方便。

* 间接寻址（Indirect Addressing Mode）。只使用BASE_OR_OFFSET寻址，例如movl (%eax), %ebx，把eax寄存器的值看作地址，把内存中这个地址处的32位数传送到ebx寄存器。注意和movl %eax, %ebx区分开。

* 基址寻址（Base Pointer Addressing Mode）。只使用ADDRESS_OR_OFFSET和BASE_OR_OFFSET寻址，例如movl 4(%eax), %ebx，用于访问结构体成员比较方便，例如一个结构体的基地址保存在eax寄存器中，其中一个成员在结构体内的偏移量是4字节，要把这个成员读上来就可以用这条指令。

* 立即数寻址（Immediate Mode）。就是指令中有一个操作数是立即数，例如movl $12, %eax中的$12，这其实跟寻址没什么关系，但也算作一种寻址方式。

* 寄存器寻址（Register Addressing Mode）。就是指令中有一个操作数是寄存器，例如movl $12, %eax中的%eax，这跟内存寻址没什么关系，但也算作一种寻址方式。在汇编程序中寄存器用助记符来表示，在机器指令中则要用几个Bit表示寄存器的编号，这几个Bit也可以看作寄存器的地址，但是和内存地址不在一个地址空间。
> [Linux C编程一站式学习](https://akaedu.github.io/book/ch18s04.html)
