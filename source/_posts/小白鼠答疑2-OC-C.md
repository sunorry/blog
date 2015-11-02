title: '小白鼠答疑2 - OC & C'
tags:
  - 小白鼠答疑系列
categories:
  - OC
date: 2015-10-29 12:09:00
---
本章内容总结于 《Objective-C编程》
<!-- more -->

## 守护进程(daemon)
有些程序没有图形化界面，并且会在后台长时间运行，这些程序成为**守护进程**。

以守护进程 **pboard** 为例，当读者执行复制和粘贴操作时，pboard 守护进程会保存读者拷贝的数据。


## 地址和指针
### 获取地址
变量的地址：内存中的某个位置，该位置的内存保存着变量的值。

通过 `&` 元素符，可以得到变量的地址。
```
int i = 17;
printf("%p", &i);
```
`%p` 是针对内存地址的转换说明。
### 用指针保存地址
只要是大小合适的无符号整数，就可以保存指针。

但是如果为变量声明特定的类型，编译器就能更容易发现错误。
```
float *ptr;
```
这里的 `ptr` 是变量，指向某个浮点数变量的**指针(point)**，ptr 本身不保存浮点数变量的值，而是指向某个地址，改地址对应的是保存浮点数的内存。
### 通过地址访问数据
使用 `*` 便可以反问地址中的值。
```
int i = 17;
int *num = &i;
printf("%p\n", &i);
printf("%d\n", *num);
```
这里 `*` 的两种用法
1. 声明指针，将变量 `num` 声明为 int *
2. 访问保存在 `num` 地址的 int 值。

指针也成为引用，所以通过访问某个地址中的数据这一过程，有时也称为*去引用(dereferencing)*

### 指针声明的代码规范
声明一个指向 float 的指针
```
float *powerPtr;
```
如果代码写成下面这样也能编译通过，
```
float* powerPtr;
```
但这不是一种好的编码风格。

C 允许一行代码中声明多个变量。
```
float x, y, z; // 三个变量都是 float
float* b, c;  // b 是指向 float 的指针， c 的类型却是 float
float *b, *c;
```
将`*`写在变量名这边，能让声明看上去更清楚。

## 通过引用传递
`modf()`函数:传入一个 `double` 类型的数，return 整数部分和小数部分。

C 函数只能返回一个值， `modf` 是如何做到返回两个值呢？

调用 `modf` 时，需要传入一个地址供 `modf` 保存整数部分的计算结果。准确的说，`modf`会返回小数部分，然后将整数部分拷贝到出入的地址。
```
#include <math.h>
int main(int argc, const char * argv[]) {
    double pi = 3.14;
    double integerPart, fractionPart;
    // 将 integerPart 的地址作为实参传入
    fractionPart = modf(pi, &integerPart);
    // 获取 integerPart 的地址上的值
    printf("integerPart = %.0f, fractionPart = %.2f\n", integerPart, fractionPart);
}
```
## 堆(heap)
**缓存区(buffer)**常用来表示一段连续的内存。

使用 `malloc` 函数可以得到一块内存缓冲区，这段缓冲区源自特定的内容区域--**heap**。堆和栈是分开的。当程序不再使用某块缓冲区时，须调用`free()`函数，释放相应的内存，将其返还给堆。

假设要为程序分配一块能够至少存放 1000 个 float 变量的内存。
```
#include <stdio.h>
#include <stdlib.h>  // malloc 和 free 都来自 stdlib


int main(int argc, const char * argv[]) {
    // 声明指针变量
    float *startOfBuffer; // startOfBuffer 指向缓冲区的第一个浮点数
    // 从堆分配指定字节数的内存
    startOfBuffer = malloc(1000 * sizeof(float));
    
    // 使用缓冲区 .....
    
    //释放之前分配到的内存，使之能够被重新使用
    free(startOfBuffer);
    // 将指针变量赋为空
    startOfBuffer = NULL;
    return 0;
}
```