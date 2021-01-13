---
title: Linux top命令的使用详解
name: XiaoGang
date: 2021-01-13 19:50:12
tags:
categories: [Linux]
headimg: https://s3.ax1x.com/2021/01/13/sNX3YF.png
---
>top 命令是 Linux 下最常用的系统监控命令。默认执行 top 命令之后，我们就能看到系统的许多监控指标，也可以看到进程按照 CPU 利用率从高到低排列。但是，这个只是 top 命令的最简单用法，其实 top 可以进行很多的定制。

<!--more-->
### top界面区域
[![sNjxbt.png](https://s3.ax1x.com/2021/01/13/sNjxbt.png)](https://s3.ax1x.com/2021/01/13/sNjxbt.png)
### 系统信息
系统信息区域展示了系统的全局监控信息，如下所示。整个区域从上到下分为 5个部分：平均负载，任务栈，CPU，内存，Swap分区
```bash
top - 08:01:12 up  1:42,  1 user,  load average: 0.05, 0.08, 0.07
Tasks: 113 total,   1 running, 112 sleeping,   0 stopped,   0 zombie
%Cpu0  :  1.3 us,  0.7 sy,  0.0 ni, 97.7 id,  0.0 wa,  0.0 hi,  0.3 si,  0.0 st
MiB Mem :    818.6 total,     53.3 free,    606.1 used,    159.2 buff/cache
MiB Swap:   1025.0 total,    444.2 free,    580.8 used.     87.1 avail Mem

```
#### 平均负载

```bash
top - 现在的时间  运行的时间 总用户数   平均负载：    1分钟，5分钟，15分钟
top - 08:01:12 up  1:42,  1 user,  load average: 0.05, 0.08, 0.07
```
#### 任务栈
```bash
任务栈： 总任务数 ，正在运行的任务数，休眠的任务数，停止的任务数，僵尸任务数
Tasks: 113 total,   1 running, 112 sleeping,   0 stopped,   0 zombie
```
#### CPU
```bash
%Cpu0  :  1.3 us,  0.7 sy,  0.0 ni, 97.7 id,  0.0 wa,  0.0 hi,  0.3 si,  0.0 st
```
缩写的具体含义：
- us: user, time running un-niced user processes, 普通进程的 CPU 消耗占比。
- sy: system, time running kernel processes, 内核任务的 CPU 消耗占比。
- ni: nice, time running niced user processes, 高优先级进程的 CPU 消耗占比。
- id: idle, time spent in the kernel idle handler, 空闲时间占比。
- wa: IO-wait, time waiting for I/O completion, 等待 IO 完成的 CPU 消耗占比（进程处于 D 状态）。
- hi: time spent servicing hardware interrupts, 用于处理硬中断的 CPU 消耗占比。
- si: time spent servicing software interrupts, 用于处理软中断的 CPU 消耗占比。
- st: time stolen from this vm by the hypervisor, 虚拟机管理进程从这个虚拟机偷走的 CPU 资源。
如下快捷键可以用来控制这个区域
- t: 切换 CPU 部分的展示方式，例如数值还是进度条，也可以切换到关闭这个区域。
- 1(digit one): 切换单个 CPU 和总体 CPU 的显示。
- 2: 按照 NUMA Node 展示。
- 3: 展示指定 NUMA Node 下的所有 CPU。
- H: 显示线程显示，默认是进程。

#### 内存和Swap交换分区
Memory** 的部分展示了系统的内存信息和交换分区的信息。

```bash
MiB Mem :    818.6 total,     53.3 free,    606.1 used,    159.2 buff/cache
MiB Swap:   1025.0 total,    444.2 free,    580.8 used.     87.1 avail Mem
```
- total: 总内存大小。
- free: 空闲内存大小。
- used: 已使用内存大小。
- buff/cache: block buffer + page cache 所占用的内存大小。
- avail Mem: 这个值是系统的估算值，表示可用于启动新程序的物理内存大小（不包括 swap 空间）。
如下快捷键可以用来控制这个区域：
- m: 切换 memory 部分的展示方式，例如数值还是进度条，也可以切换到关闭这个区域。
- E: 切换内存单位。
### 任务区域
任务区域包含两个部分：字段名称和任务列表（根据指定的字段排序）top 其实可以展示很多内容，我们可以定义要展示哪些字段。在全屏模式下，按 F 进入字段管理界面，如下：
[![sNvSVP.png](https://s3.ax1x.com/2021/01/13/sNvSVP.png)](https://s3.ax1x.com/2021/01/13/sNvSVP.png)
首先要注意的是第一行，这个界面可以为 4 个 window 分别设置要展示的字段，最上面一行提示当前正在为哪个 window 设置字段，以及当前使用的排序字段是哪个。同样的，可以通过可以按 a 或者 w 来切换 window。然后可以上下移动到想要处理的字段，按空格或者 d 切换是否展示，按 s 设置用该字段进行排序，按 q 或者 ESC 退出这个界面。前面型号的表示选中。要调整字段的排列顺序，先选中一个字段，按右键表示开始移动，然后上下移动，然后按左键表示移动结束。
下面来看下可用的字段。

#### 进程状态相关
- S: Process Status
- %CPU: CPU Usage
- nTH: Number of Threads
- P: Last Used Cpu (SMP)
- TIME: CPU Time。任务从启动到现在使用的 CPU 时间。
- TIME+: CPU Time, hundredths。任务从启动到现在使用的 CPU 时间，精确到百分之一秒。
- WCHAN: Sleeping in Function。对于 sleeping 的进程，当前所处的内核函数。
- Flags: Task Flags
进程状态有如下几种：
- D Uninterruptible sleep。不可中断休眠，就是等待 I/O 完成时的状态，会导致 CPU 统计的 wa 上升。
- R Running
- S Sleeping
- T Stopped by job control signal
- t Stopped by debugger during trace
- Z zombie
如下快捷键可以用来控制这些字段：
- I (upper case i): 切换 %CPU 的模式，Irix/Solaris 两个模式。Irix mode 的计算方式是跑满一个 CPU 为 100%，%CPU 可能会超过 100%。Solaris mode 则是会把总体利用率除以 CPU 核数，保证不会超过 100%。
- S: Cumulative time，off 展示两次刷新时间的即时值，而不是从进程启动到现在的累加值。
#### 进程优先级相关
- NI: Nice Value. 进程的优先级。这个是表示进程的用户态优先级，范围是 -20 到 +19，默认值是 0，值越低优先级越高。
- PR: Priority. 进程的调度优先级，这个是内核实际使用的任务的优先级，范围是 0 到 39，映射到内核的值是 100 到 139；也可以是 rt ，表示实时任务。内核表示一个 task 的优先级的范围是 0 到 139。其中，0 到 99 是实时进程的优先级，100 到 139 是非实时进程的优先级。PR 的默认值是 20，对应到内核是 120，和 NI 的关系是: PR = 20 + NI。
#### 内存相关
- %MEM: Memory Usage (RES)
- VIRT: Virtual Image (KiB)。表示一个任务使用的虚拟内存总和，包括所有的代码段、数据段、链接的共享库、已经被 swap 的页和已经被映射但是没有使用的页。
- RES: Resident Size (KiB)。表示一个任务使用的没有被 swap 的物理内存。
- SHR: Shared Memory (KiB)。表示一个任务可能和其他任务共享的内存。
- SWAP: Swapped Size (KiB)。表示一个任务的非驻留内存，也就是使用的交换空间。
- CODE: Code Size (KiB)。表示任务的代码段的大小。
- DATA: Data+Stack (KiB)。Data Resident Set size，包括了程序数据段和栈。
- USED: Res+Swap Size (KiB)。就是 RES + SWAP。
- nDRT: Dirty Pages Count。该 task 内存空间中的脏页的数量。
- nMaj: Major Page Faults。该 task 遇到的 Major Page Faults 的数量。Major Page Fault 是指需要访问通过访问 swap 分区或者硬盘（mmap 一个文件，但是还没把内容读取到内存时）来处理的缺页异常。
- nMin: Minor Page Faults。该 task 遇到的 Minor Page Faults 的数量。Minor Page Fault 是指不需要通过访问 swap 分区或者硬盘来处理的缺页异常，简单的说，没用到磁盘 I/O。
- vMj: Major Faults delta。上次 top 刷新数据依赖的 Major Page Faults 增加数量。
- vMn: Minor Faults delta。上次 top 刷新数据依赖的 Minor Page Faults 增加数量。
如下快捷键可以用来控制这些字段：
- e: 切换内存单位。
#### 只展示非空闲的任务
快捷键 i 用来切换是否只展示非空闲任务。
#### 限制展示任务的数量
快捷键 n 用于限制要展示的任务的数量，0 表示无限制。默认是全部展示（超过一页需要翻页）。
#### 只展示指定用户的任务
快捷键 u 表示要过滤的用户，可以加 ! 前缀表示反向条件。可以输入 UID 或者 username，直接回车表示取消这个过滤条件。
#### 其他定制
- R 切换排序的方向，默认是从高到底，可以切换为从低到高。
- x 切换是否高亮显示排序列。
- y 切换是否高亮显示 running 的 task。
- b bold/reverse，这个快捷键用于切换关键位置是粗体展示还是反色展示，会影响到 x, y 的展示效果，也会影响到 summary area 的 CPU 进度条 和 memory 进度条的展示效果。
- d 定时刷新间隔，默认是 3s。
#### 配置文件
上面讲的这些定制，都可以保存到一个配置文件，然后 top 每次启动都会载入它所找到的配置文件。配置文件中会保存一些全局模式，比如 Irix mode 的配置，刷新时间等，也会保存每个窗口的字段配置和颜色配置等，还会保存 inspect entries （见下文）。
生成配置文件的方式很简单，在你完成想要的定制后，按快捷键 W 即可。CentOS 7 上，配置文件的保存路径是 /root/.toprc；Ubuntu 上则是 ~/.config/procps/toprc，每次你保存的时候，top 会显示这个路径。
#### 自己定制
```bash
top's Config File (Linux processes with windows)
Id:i, Mode_altscr=0, Mode_irixps=1, Delay_time=3.0, Curwin=0
Cpu     fieldscur=ķ9')*+,-./0126<>?ABCFGHIJKLMNOPQRSTUVWXYZ[\]^_`abcdefghij
        winflags=195380, sortindx=18, maxtasks=0, graph_cpus=0, graph_mems=0
        summclr=4, msgsclr=1, headclr=3, taskclr=4
Mem     fieldscur=&97(34D')*+,-./012568>?FGHIJKLOPQRSTUVWXYZ[\]^_`abcdefghij
        winflags=195380, sortindx=21, maxtasks=0, graph_cpus=0, graph_mems=0
        summclr=6, msgsclr=6, headclr=3, taskclr=6
Sch     fieldscur=:;<=>?@AMBNC&'()*+,-./0128HIJKLOPQRSTUVWXYZ[\]^_`abcdefghij
        winflags=194868, sortindx=0, maxtasks=0, graph_cpus=0, graph_mems=0
        summclr=5, msgsclr=5, headclr=3, taskclr=5
Cgp     fieldscur=*097:D)+,-./1234568;<=>?@ABCFGIJKLMNOVWXYZ[\]^_`abcdefghij
        winflags=194868, sortindx=0, maxtasks=0, graph_cpus=0, graph_mems=0
        summclr=2, msgsclr=3, headclr=3, taskclr=2
Fixed_widest=0, Summ_mscale=0, Task_mscale=0, Zero_suppress=0

pipe    NetFiles        lsof -a -l -n -P -i4 -p %d 2>&1
pipe    OpenFiles       lsof -a -l -n -P -p %d 2>&1
file    NUMAInfo        /proc/%d/numa_maps

```
