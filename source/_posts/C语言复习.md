title: C语言复习
tags:
  - C
categories:
  - C
date: 2015-10-27 21:28:00
---
[原文链接](http://cocoadevcentral.com/articles/000081.php)

学习`Objective-C`中顺便复习下C语言。

文件后缀形式 .c 。

<!--more-->

## A Sample C Program


```
#include <stdio.h>
main () {
	printf("I'm a C program\n");
}

```

`<stdio.h>`处理输入和输出，`printf`就是它的方法。
所有的C程序都会有一个 main 函数。

## Use Gcc to Complie

```
gcc test.c -o test
```

## Basic C Concepts

### Typed Variables
kind of data that a variable contains.

Have to **declare the type** of data, can't change type.
```
int num1 = 2;
float num2 = 1.65;
char vari = 'A';
```

### Available Types

* int
* unsigned int(no negatives)
* float
* double, long (no often see)
* char

c also allows you to create your own variable types.

### Typed Functions
```
// 必须由返回值
int numberOfPeople() {
	return 3;
}

void printHello() {
	printf("Hello!\n")
}
```

### Types For Parameters
参数的类型也必须声明
```
init difference(int val1, int val2) {
	return val1 - val2;
}
```

### Declaring Functions

```
#include <stdio.h>
	
int sum ( int x, int y );

main (){
  int theSum = sum (10, 11);
  printf ( "Sum: %i\n", theSum );
}

int sum ( int x, int y ){
  return x + y;
}
```

### Format String
```
int var1 = 3;
printf("value is %i", var1);
```
* int -> %i/%d
* unsigned int -> %u
* float -> %f
* char -> %c

### Type Casting
```
int   trips           = 6;
float distance        = 4.874;
int   approxDistance  = (int)distance;
```

### Create a Header File
就和 OC 中的添加一个文件（某种方式），出来一个 .h 一个 .m 文件。
```
// math_functions.h
int sum (int x, int y);
```

function implementations.

math_function.c
```
int sum (int x, int y) {
	return (x + y)
}
```

using Header File
```
#include <stdio.h>
#include <math_functions.h>

main() {
	int theSum = sum(8, 12);
}
```

### Structs
**structured groups of variables**
```
typedef struct {
	int length;
    int year;
} Song;
```

看起来是声明了两个变量，其实是创造了一种新的变量类型。
`typedef` 给 `struct` 一个名字， -Song.
```
Song song1;

song1.lengthInSeconds =  213;
song1.yearRecorded    = 1994;

Song song2;

song2.lengthInSeconds =  248;
song2.yearRecorded    = 1998;
```

#### Structs in Functions
Functions can specify structs as input or output. These function declarations and the struct itself can be put in a header file. 

***song.h**
```
typedef struct {
	int length;
    int year;
} Song;

Song make_song (int second, int year);
void display_song (Song theSong);
```

**Song.c**
```
#include <stdio.h>
#include "song.h"

Song make_song (int seconds, int year) {
  Song newSong;

  newSong.lengthInSeconds = seconds;
  newSong.yearRecorded    = year;
  display_song (newSong);

  return newSong;
}

void display_song (Song theSong) {
  printf ("the song is %i seconds long ", theSong.lengthInSeconds);
  printf ("and was made in %i\n", theSong.yearRecorded);
}

```

#### Structs in Use
Now we need a program that uses the song.h and song.c files. 
```
#include <stdio.h>
#include "song.h"

main() {
  Song firstSong  = make_song (210, 2004);
  Song secondSong = make_song (256, 1992);

  Song thirdSong  = { 223, 1997 };
  display_song ( thirdSong );

  Song fourthSong = { 199, 2003 };
}
```

### Constants
```
const int age = 123;
```

###Enums
Apple uses enums in Cocoa to group a series of related constants. 
```
enum {
  NSCaseInsensitiveSearch = 1,
  NSLiteralSearch = 2,
  NSBackwardsSearch = 4,
  NSAnchoredSearch = 8,
  NSNumericSearch = 64
};
```