title: '+(class method) & -(instance method)'
tags:
  - 知识点积累
categories:
  - OC
date: 2015-10-28 16:04:00
---
[原文链接](http://stackoverflow.com/questions/1053592/what-is-the-difference-between-class-and-instance-methods)

<!-- more -->

实例方法使用一个 class 的实例的方法。
class 方法是调用用方法名。

```
@interface MyClass : NSObject

+ (void)aClassMethod;
- (void)anInstanceMethd

@end
```

use:
```
[MyClass aClassMethod];
MyClass *object = [[MyClass alloc] init];
[object anInstanceMethod];
```

Foundation classes like NSString's +stringWithFormat: or NSArray's +arrayWithArray:. An instance method would be NSArray's -count method.