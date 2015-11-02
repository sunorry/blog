title: BOOL VS bool
date: 2015-10-28 23:24:03
tags:
---
先来看下关于 `char` 的一些东西吧。
`char` 是字符，那 singed char 又是个啥东西呢？
在 C 语言中，我们能使用 `char` 去做数学运算。

signed char取值范围是 -128 到 127

unsigned char 取值范围是 0 到 255

BOOL - YES/NO. bool - true/false.

BOOL is a signed char. bool - type from C99 standard (int).
```
bool b1 = 2;
if (b1) printf("REAL b1 \n");
if (b1 != true) printf("NOT REAL b1 \n");

BOOL b2 = 2;
if (b2) printf("REAL b2 \n");
if (b2 != YES) printf("NOT REAL b2 \n");
```

运行结果是 
1. REAL b1
2. REAL b2
3. NOT REAL b2

```
// Add this function to the top of AppDelegate.m
static BOOL different (int thing1, int thing2) {
    return thing1 - thing2;
}
 
// Add this method inside application:didFinishLaunchingWithOptions
if (different(1, 2) == YES) {
    NSLog(@"Different!");
} else {
    NSLog(@"Not different.");
}
```
32 和 64位结果不同。
```
if (different(1, 2)) {
    NSLog(@"Different!");
} else {
    NSLog(@"Not different.");
}
```
这是一种更好的写法，看原文。