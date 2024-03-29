

[TOC]

--------------

# 进程

## 定义
一个具有独立功能的程序，在一个数据集合上的一次动态执行过程。它包括代码段、数据段、指令存储、寄存器、堆栈资源。
程序是产生进程的基础，每次执行构成不同的进程。
进程是程序功能的体现，多次执行一个程序，可对应多个进程，通过调用一个进程可以包含多个程序。


## 进程和程序的区别？
进程是动态的，它包括内核态和用户态，它是程序执行的一种体现，它是暂时的。它是一个状态变化的过程，它包含数据进程控制信息。
程序是静态的，是代码的集合。它是永久的，它可以长久保存。它没有进程的控制信息。

## 进程的特点
动态创建结束。
并发
独立：不同的进程工作不受影响。
制约：访问共享数据同步会产生制约。

## 进程挂起的定义：指一个进程从内存移动到外存。
当进程不占用内存空间时，它可以放到磁盘上。
进程由于阻塞态到挂起：也就是存放在外存，并等待事件的出现
进程由就绪态到挂起态，其进程存放在外存，本身已经就绪。

- 阻塞—-》阻塞挂起
- 就绪—-》就绪挂起
- 运行—-》就绪挂起

外存中的状态变化：外存中的阻塞进程得到满足。

操作系统通过状态队列来管理进程。

## 进程控制模块

进程的唯一标识

- 标识包括进程标识、产生者的标识、用户的标识。

- 处理机状态信息保存区

- 进程通信信息。

- 资源


数据结构
链表：同一个状态的进程进程，控制模块定义为链表
索引

线程的生命周期。

- 创建。操作系统初始化；用户请求创建一个进程；进程创建一个进程。
- 运行：操作系统选择一个就绪的进程。
- 等待：进程等待，周三，也就是不占用C P U从运形态到阻塞太。
- 唤醒：被其他进程唤醒了。
- 结束： 
  - 正常结束。
  - 错误结束。
  - 致命错误。被操作系统杀掉。
  - 被其他进程杀掉。

## 进程的状态：

 运行。就绪。等待

## 进程间的通信IPC

### 信号

软件级别的中断，比如  **SIGKILL, SIGFPE.**

接收到信号:

cache：操作系统可以指定调用函数

ignore：也可以忽略，

mask：阻塞信号。

实现：

先注册处理信号处理函数，收到信号时操作系统修改函数调用stack。使得指针指到对应的处理函数上。

### 管道

使得一个进程的输出，成为另一个进程的输入。比如

`0 stdin    1 stdout    2  stderr`

管道所运用的是内存中的buffer。子进程从父进程继承文件说明符。

没有父进程则无法通信。他使用的主要是字节流。

### 消息队列

### 共享内存

两个进程都可以访问到同一个内存，他们可以直接访问

优点

方便、高效、量大，

缺点

同步互斥。

实现方案

将同一块物理内存映射到不同进程的相同的逻辑地址空间

### socket通信。



优先级反转指的是低优先级影响了高优先级的任务

解决的办法是降低优先级的任务，继承了高优先级。

# 线程
进程的问题：当多进程并发时进程间的通信开销比较大。进程间的切换开销比较大。
如何解决：

- 共享相同的地址空间
- 实体的并发执行
- 线程



## 定义
进程中的一条执行流程。
从资源角度来说，进程用来管理资源
从运行角度来说，线程负责执行流程
线程有独立的线程控制模块TCB，有独立的寄存器、堆、栈。代码、数据、资源是共享
## 优点
一个进程存在多个线程
可以并发
共享地址空间及资源
## 缺点
是一个线程崩溃，所有的线程都会崩溃。
举个例子来说，Chrome浏览器开网页时，每个网页用一个进程
性能上，比如高性能计算天气预报用的就是多个线程。

## 线程分为两种：

- 用户态线程

- 内核态线程

  

### 用户态线程

优点

切换速度比较快，

缺点

一个线程阻塞后全部线程在一个线程运行，除非主动交给CPU，否则其他的线程时无法运行。

比较慢，因为时间片分给进程的每个线程比之前的时间少。

### 内核态线程

操作系统完成线程的创建、结束、管理。

线程的切换开销比较大，因为与操作系统进行交互

比较安全，因为操作系统的保护。

轻量级的进程

**linux/solaris**

操作系统支持的用户级线程。



# 进程与线程的区别



| 项目               | 进程           | 线程                                                         |
| ------------------ | -------------- | ------------------------------------------------------------ |
| 定义               | 资源分配单位， | CPU的调度单位                                                |
| 资源               | 完成资源的管理 | 独享资源有寄存器、栈。它有就绪态、阻塞态和运行态             |
| 时间开销，空间开销 |                | 并发执行的时间小，空间开销小。                               |
| 创建开销           |                | 创建的时间比较短，不用创建资源，因为进程负责创建资源。       |
| 结束开销           |                | 资源退出的时间比较小。                                       |
| 切换               |                | 切换速度比较快，因为在内存中，使用同一个页表，不用来回切换页表。 |
| 通信               |                | 线程间通信，数据交换快。因为只使用空间地址即可，不用与操作系统进行通信 |





# 同步互斥

- 静态条件。
- 原子操作。
- critical section
- 互斥：一个进程处于临界区时，没有其他的进程会处于临界区访问共享资源
- 死锁：两个以上的进程相互等待对方完成任务，而最终没法完成自身任务。
- 饥饿：一个进程持续被操作系统，忽略长期不能执行。



# 连续内存的分配策略

- 首次分配：也就是找到第一个满足的内存快的优点是简单，容易发生大块的内存分配缺点是容易造成内存碎片，因为中间一些小的内存就不能被使用，动态分配的时候会加剧内存碎片的产生。

- 最优分配：找到与当前内存差距最小的内存快进行分配优点，是不容易拆开大的内存快算法简单，再不内存碎片比较小缺点，是外部内存碎片利用率比较小，不能进行后续的内存分配。

- 最坏匹配：就是找到差距最大的内存快进行分配有点事，如果想获得最大的内存。这个方法比较快，缺点是将大块内存拆开容易导致后续像分配大的内存快就无法进行了。

## 内存碎片的整理方法。

压缩式整理：就是将现有进程的内存进行紧致，腾出一些空间。**缺点**是拷贝内存开销比较大，而且何时拷贝内存比较难。
交换式内存碎片整理：将不常用的内存或者进程拷贝到磁盘或者抢占正在处于等待的进程的内存回收。**问题**是抢占哪个进程？什么时间进行换入换出？

# 非连续内存的分配策略

由于连续地址分配有过多的内存碎片，用的比较少，所以，我们用非连续内存管理员来管理内存。这边有两个方法第一个是分段，第二个是分页。

## 分段

如下图程序，主要分为这几段：堆、栈、程序的数据、程序。这是逻辑地址，通过段地址可以映射到物理地址上。段地址包括两部分，第一个是段号、第二个是段地址。在CPU中存在着段表，表示有操作系统建立的CPU通过段地址，然后查找段标从而找到物理地址。

![](os_memory.JPG)

## 分页

分页的物理地址与逻辑地址空间一样，大都是二等幂次方个字节

实现方案

page对应frame

CPU通过查找页表来从逻辑地址映射的物理地址，页地址的话也包括页号、页偏移。帧地址包括帧号和帧偏移。

CPU查找页地址，然后通过页表找见对应的帧地址。页表在操作系统初始化的时候建立。

因为逻辑上的地址是大于物理空间上的真地址的，那么大于时候会怎么样呢？

好处

减少内存碎片。

坏处

一. 本身列表的本身会很大，比如64位的系统中，每页有1024个字节的页表大小

二. 多个应用中存在的多个页表，由于太大，所以只能将页表放到内存中，也就是说，寻址一次要先从内存空间中访问一次页表，然后在访问一次内存。这样的话时间变成两倍，

优化方法。

时间

CPU中存在TLB，缓存近期访问的页表表项，当TLB发生缺失现象时，就是应用程序编程的时候，尽量让内存属于局部性，x86由硬件完成，Mix由操作系统完成。

空间

将页表才去拆分为多级页表，如果一级业表中的映射关系不存在，那么二级页表就不用存在，从而节省内存，因为应用程序中的内存绝大部分是局部性的，所以特别适合用多级页表。

反向页表

容量小。

# 虚拟内存

由于应用程序的内存越来越大，所以需要将一些内存来虚拟化。

