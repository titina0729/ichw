# 1.作业、进程、线程
# 作业
### 基本概念
用户在一次解决或是一个事务处理过程中要求计算机系统所做的工作的集合，
它包括用户程序、所需要的数据集控制等。
作业是由一系列有序的步骤组成的。
作业的完成需要经过作业提交、作业收容、作业执行和作业完成4个阶段。
在执行一个作业可能会运行多个不同的进程。

### 解决了什么问题
######
# 进程
### 基本概念
程序在一个数据集上的一次运行过程。
是操作系统资源分配的基本单位。
Windows中进程被细化为线程，
一个进程下有多个能独立运行的更小的单位，
进程还拥有一个私有的虚拟地址空间，
该空间仅能被它所包含的线程访问。
简单来说，电脑如何来完成作业？是通过进程来完成的（作业是面向用户的，进程是面向CPU的）
### 作用
进程是一个具有一定独立功能的程序在一个数据集上的一次动态执行的过程，
是操作系统进行资源分配和调度的一个独立单元，
是应用程序的载体。
进程这一概念的提出解决了多道程序系统的问题。


# 线程
### 基本概念
是进程中的一个实体，
是被操作系统独立调度和执行的基本单位。
进程包含一个或多个线程。
线程只能归属于一个进程并且它只能访问该进程所拥有的资源。
当操作系统创建一个进程后，
该进程会自动申请一个名为主线程或首要线程的线程。
主线程将执行运行时的宿主，
运行时宿主会负责载入CLR
### 作用
解决了进程之间的切换导致的开销过大，无法满足越来越负载的程序要求的问题。
线程之间的切换不仅开销小，速度快，同时还可以做到
并发执行（甚至允许在一个进程中所有线程都能并发执行）

简单总结来说
作业是计算机提交任务的任务实体
进程是执行实体，资源分配的基本单位
线程是处理及调度的基本单位。
实际上
是应用程序的载体。
本质上来讲，不管是进程还是线程，都解决的是吞吐量的问题，
增高了CPU的效率。

# 2.虚拟存储器
# 概念
虚拟内存（virtual memory）又称虚拟存储器。电脑中所运行的程序均需要经由内存执行，若执行的程序占用内存很大或很多，则会导致内存消耗殆尽。
为解决这个问题，windows中运用了虚拟内存技术，即匀出一部分硬盘空间当作内存使用。
当内存耗尽时，电脑会自动调用硬盘来充当内存，以缓解内存的紧张。若计算机运行程序或操作所需的随机存储器（ram）不足时，windows的虚拟存储器进行补偿。
将计算机的ram和硬盘上的空间进行组合。
当ranm运行速率缓慢时，将数据哦那个ram移动到称为“分页文件”的空间中。将数据移入分页文件可释放ram，以便完成工作。
一般而言，计算机的ram容量越大，程序运行的越快。若计算机速率由于ram可用空间匮乏而减缓，则可尝试通过增加虚拟内存来进行补偿。
但是计算机从ram读取数据的速率要比硬盘读取数据的速率快，因而扩增ram容量是最佳选择。

内存在计算机中的作用很大，电脑中所有运行的程序都要经过内存来执行，如果执行的程序很大或很多，就会导致内存消耗殆尽。为了解决这个问题，windows运用了虚拟内存技术，拿出一部分硬盘空间来充当内存使用，这部分空间就被称为虚拟内存，虚拟内存在硬盘上存在的形式就是pagefiles.sys这个页面文件。

# 工作原理
虚拟存储器是由硬件和操作系统自动实现存储信息调度和管理的。它的工作过程包括六个步骤：
##### 1.中央处理器访问主存的逻辑地址分解成组号a和组内地址b，并对组号a进行地址变换，将逻辑组号a作为索引，查地址变换表，以确定改组信息是否存放于主存内。
##### 2.如该组号已经在主存内，转而执行4，如果不在主存内，则检查主存中是否有空闲去，如果没有，便将某个暂时不用的组调出送往辅存，以便将这组信息调入主存。
##### 3.从辅存读出所要的组，并送到主存空闲区，然后将那个空闲的物理号a和逻辑组号a登陆在地址变换表中。
##### 4.从地址变换表读出与逻辑组号a对应的物理组号a。
##### 5.从物理组号a和组内字节地址b得到物理地址。
##### 6.根据物理地址从主存中存取必要的信息。

