title: 小白鼠答疑4 - Collection类
tags: []
categories:
  - OC
date: 2015-11-02 11:08:00
---
## NSArray/NSMutableArray

创建 `NSArray` 实例时，需要一次性设置好所有要保存的对象。
```
NSArray *color = [NSArray arrayWithObjects:@"Orange", @"red", nil];
```
`nil` 实参必须写，以便让该方法知道要加入对象的个数，新版本是写 count。

不可修改的对象(NSArray)永远无须拷贝。对于可修改对象，则可能要复制一份私有拷贝，以保证程序中的其他代码无法修改对象所保存的内容。不可修改对象则没有这样的顾虑。

也就是说，NSArray 的 copy 不会做额外的工作，仅仅返回本身的指针。 NSMutableArray 的 copy 则会制作一份自己的拷贝，并返回指向新数组对象的指针。