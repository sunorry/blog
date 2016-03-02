title: main() 与 UIApplication
date: 2015-11-21 17:59:38
tags:
---
```
int main(int argc, char *arv[]) {
	@autoreleasepool {
		return UIApplicationMain(argc, argv, nil, NSStringFromClass([AppDelegate class]));
	}
}
```

`UIApplicationMain` 函数会创建一个 `UIApplication` 对象。每个 iOS 应用都有且只有一个 `UIApplication` 对象，该对象的作用是维护运行循环。一旦程序创建了某个 `UIApplication` 对象，该对象的运行就会一直循环下去， `main()` 的执行也会因此阻塞。

此外，`UIApplicationMain` 函数还会创建某个指定类的对象，并将其设置为 `UIApplication` 的 delegate。该对象的类是由 `UIApplicationMain` 函数的最后一个参数指定的，该参数的类型是 `NSString` 对象，代表的是某个类的类名。

在应用启动运行循环并开始接受事件前，`UIApplication` 对象会向其委托发送一个特定的消息，使应用能有机会完成相应的初始化工作。这个消息的名称是 `application:didFinishLaunchingWithOptions:` 。

每个 iOS 应用都有一个 `main（）` ，完成的都是相同的任务。