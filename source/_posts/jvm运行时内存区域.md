---
title: jvm运行时内存区域
date: 2020-03-10 13:22:24
tags:
- java
- jvm
---

![QQ20180624-150918](http://www.hollischuang.com/wp-content/uploads/2018/06/QQ20180624-150918.png)

# Run-Time Data Areas

​	The Java Virtual Machine defines various run-time data areas that are used during execution of a program. Some of these data areas are created on Java Virtual Machine start-up and are destroyed only when the Java Virtual Machine exits. Other data areas are per thread. Per-thread data areas are created when a thread is created and destroyed when the thread  is exits.

## The pc Register

The Java Virtual Machine can support many threads of execution at once (JLS §17). Each Java Virtual Machine thread has its own `pc` (program counter) register. At any point, each Java Virtual Machine thread is executing the code of a single method, namely the current method ([§2.6](https://docs.oracle.com/javase/specs/jvms/se8/html/jvms-2.html#jvms-2.6)) for that thread. If that method is not `native`, the `pc` register contains the address of the Java Virtual Machine instruction currently being executed. If the method currently being executed by the thread is `native`, the value of the Java Virtual Machine's `pc` register is undefined. The Java Virtual Machine's `pc` register is wide enough to hold a `returnAddress` or a native pointer on the specific platform.

## Java Virtual Machine Stacks

