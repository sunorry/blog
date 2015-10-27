title: Memory and ARRAY in C
tags:
  - C
categories:
  - C
date: 2015-10-28 00:05:00
---
[原文链接](http://theocacao.com/document.page/231)

## Basic memory
计算内存的单位是 `byte`。一个标准的 `int` 变量占用 4 个比特。

<!-- more --> 

内存可以来自 **data segment（数据段）** 或者 **stack**
    
    在采用段式内存管理的架构中，数据段（data segment）通常是指用来存放程序中已初始化的全局变量的一块内存区域。数据段属于静态内存分配。
    
在函数外声明的变量，`global`。任何 func 都能进入。它存在 data segment。
This memory is in use for as long as the program is running.

stack 用于存储在函数中的变量。它是暂时性的。

```
#include <stdio.h>
  
// this global variable resides in the data segment
int globalMonsters = 2;

void addFourMonsters ()
{
  // this variable uses memory in the stack
  int stackMonsters = 4;

  // we add the value of the stack variable
  // to the global variable
  globalMonsters += stackMonsters;  
}

main ()
{
  printf ("Global monsters: %i\n", globalMonsters);
  addFourMonsters();  
  printf ("Global monsters: %i\n", globalMonsters);
  addFourMonsters();  
  printf ("Global monsters: %i\n", globalMonsters);
}
```
output
* Global monsters: 2
* Global monsters: 6
* Global monsters: 10

create an array with **fixed** size.
```
// int (4 bytes) x 5 = 20 bytes
int myIntArray[5]
```