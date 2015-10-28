title: Learn Objective-C
tags:
  - OC
categories:
  - iOS
date: 2015-10-28 09:47:00
---
三小时搞定语法。
<!-- more ->


## Calling Methods

### 调用对象与类的方法
```
[object method];
[object mehtodWithInput:input];
// Methods can return a value
output = [object methodWidthOutput];

// 调用 NSString 类的 string 方法，return 一个新的 NSString 对象
id myObject = [NSSting string];

```

#### id

The id type means that the `myObject` variable can refer to any kind of object, so the actual class and the methods it implements aren't known when you compile the app.

上面的例子，返回的明显是 `NSString` 类型，所以：
```
NSString* myObject = [NSString string];
```
上面的星号(`*` asterisk)

All Objective-C object variables are pointers types. The id type is predefined as a pointer type, so there's no need to add the asterisk.


[stackoverflow](http://stackoverflow.com/questions/7987060/what-is-the-meaning-of-id)

	id is a pointer to any type, but unlike void * it always points to an Objective-C object. For example, you can add anything of type id to an NSArray, but those objects must respond to retain and release.

	The compiler is totally happy for you to implicitly cast any object to id, and for you to cast id to any object. This is unlike any other implicit casting in Objective-C, and is the basis for most container types in Cocoa.
    
#### release && retain
Swift所用的内存管理技术是ARC  也就是自动引用计数器，所以不会有retain和release这两个方法了.
这两个方法  是OC在MRC（手动引用计数器）时代的方法, `retain`是增加一次引用，`release`是释放一次引用，OC

### Nested Messages
就像在 `js` 中的函数式参数。
```
func1( func2() );
```
func2 的返回值给 func1 当参数。
```
// OC
[NSString stringWithFormat:[prefs format]];
```

### Multi-Input Methods
有许多方法接受多个 input 值。
a multi-input method looks like this:
```
-(BOOL)writeToFile:(NSString *)path atomically:(BOOL)useAuxiliaryFile;
```
调用
```
BOOL result = [myData writeToFile:@"/tmp/log.txt" atomically:NO];
```
These are not just named arguments. The method name is actually writeToFile:atomically: in the runtime system.

## Accessors
All instance variables are **private** in Objective-C by default, so you should use accessors to get and set values in most cases.

*This is the traditional 1.x syntax:*
```
[photo setCaption:@"Day at the Beach"];
output = [photo caption];
```
The code on the second line is `not` reading the instance variable directly. It's actually calling a method named caption. In most cases, you don't add the "get" prefix to getters in Objective-C. 

**Whenever you see code inside square brackets, you are sending a message to an object or a class.**

### Dot Syntax
OC 2.0
```
photo.caption = @"Day at the Beach";
output = photo.caption;
```

## Creating Objects
The First way:

**create an autoreleased object**
```
NSString* myString = [NSString string];
```

The Second way: 

**create an object using the manual style**
```
NSString* myString = [[NSString alloc] init];
```
This is a nested method call.
`allco` method called on NSString itself.

`init` The second piece is a call to init on the new object. The init implementation usually does basic setup, such as creating instance variables. The details of that are unknown to you as a client of the class. 

调用不同版本的 init, OC
```
NSNumber* value = [[NSNumber alloc] initWithFloat: 1.0];
```

## Basic Memory Management
如过你用 `alloc` 手动创建一个 `object` ,你需要手动释放(release)这个对象。

```
// string1将会自动释放
NSString* string1 = [NSString string];
// 必须手动释放 when down
NSString* string2 = [[NSString alloc] init];
[sting2 release];
```

## Designing a Class Interface
interface一般为 ClassName.h 文件，定义实例变量和公用方法。
implementation为 ClassName.m 文件，包含方法的实现代码，也能定义一些私有的方法。
```
// interface Photo.h
#import <Cocoa/Cocoa.h>
@interface Photo : NSObject {
	NSString* caption;
    NSString* photographer;
}
@end
```
两个实例变量（interface variable）caption 和 photographer 都是 NSString，但可以设置成任何类型的队形，包括 id。
### 添加方法
添加一些 getters for 实例变量
```
#import <Cocoa/Cocoa.h>
    
@interface Photo : NSObject {
    NSString* caption;
    NSString* photographer;
}

// getter
- (NSString*) caption;
- (NSString*) photographer;

// setter
- (void) setCaption: (NSString*)input;
- (void) setPhotographer: (NSString*)input;

@end 
```
OC 中，方法可以去掉'get'前缀

## Class Implementation 
```
#import "Photo.h"
@implementation Photo

- (NSString*) caption {
	return caption;
}

- (NSString*) photographer {
	return photographer;
}

- (void) setCaption: (NSString*)input {
	[caption autorelease];
    caption = [input retain];
}
- (void) setPhotographer: (NSString*)input {
    [photographer autorelease];
    photographer = [input retain];
}

@end
```

### Init
可以创建一个 `init` 方法为实例变量设置初始值。
```
- (id) init {
	if(self = [super init]) {
    	[self setCaption:@"Default Caption"];
        [self setPhotographer:@"Default Photographer"];
    }
    return self;
}
```

	This is fairly self-explanatory, though the second line may look a bit unusual. This is a single equals sign, which assigns the result of [super init] to self. 

	This essentially just asks the superclass to do its own initialization. The if statement is verifying that the initialization was successful before trying to set default values.
    
### Dealloc
`dealloc` 在一个对象将被内存销毁后调用（The dealloc method is called on an object when it is being removed from memory.）This is usually the best time to release references to all of your child instance variables:
```
- (void) dealloc {
	//On the first two lines, we just send release to each of the instance variables. 
    //We don't need to use autorelease here, and the standard release is a bit faster. 
	[caption release];
    [photographer release];
    //The last line is very important. 
    //We have to send the message [super dealloc] to ask the superclass to do its cleanup. 
    //If we don't do this, the object will not be removed, which is a memory leak. 
    [super dealloc];
}
```

## More on Memory Management
略过，以后细看

## Logging
```
NSLog ( @"The current date and time is: %@", [NSDate date] );
```

## Properties

## Calling Methods on Nil
Categories are one of the most useful features of Objective-C. Essentially, a category allows you to add methods to an existing class without subclassing it or needing to know any of the details of how it's implemented. 

```
#import <Cocoa/Cocoa.h>
            
@interface NSString (Utilities)
- (BOOL) isURL;
@end
```

```
#import "NSString-Utilities.h"
            
@implementation NSString (Utilities)

- (BOOL) isURL
{
    if ( [self hasPrefix:@"http://"] )
        return YES;
    else
        return NO;
}

@end
```