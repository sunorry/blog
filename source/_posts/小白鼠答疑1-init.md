title: 小白鼠答疑1 - init
tags:
  - 小白鼠答疑系列
categories:
  - OC
date: 2015-10-29 00:31:00
---
这篇不太好
<!-- more -->
Atom.m
```
#import <Foundation/Foundation.h>
@interface Atom : NSObject

@property (readonly) NSUInteger protons;
@property (readonly) NSString *chemicalElement;

- (NSUInteger) massNumber;
@end
```

类声明中添加了两个属性和一个实例方法。

属性 `chemicalElement` 的类型为 NSString *(指向文本字符串的指针)，还拥有 readonly 属性。

实例方法 `massNumber` 会返回一个非负整型值。

Atom.h
```
#import "Atom.h"
@implementation Atom
- (id) init {
    if ((self = [super init])) {
        _chemicalElement = @"none";
    }
    return self;
}

- (NSUInteger) massNumber {
    return 0;
}
@end
```
在类接口中声明的所有**方法**都必须在类的实现文件中定义。

`massNumber` 是在 Atom 接口中声明的。为啥 `init` 也要在此处定义呢？

因为 `init()` 方法是在 `NSObject` 类中声明的。

`NSObject` 类的 `init()` 方法用于在将内存分配给新对象后，立刻初始化该对象。