title: ES6 - Module
tags:
  - Module
categories:
  - ES6
date: 2015-11-30 17:27:00
---
CommonJS和AMD两种。前者用于服务器，后者用于浏览器。

<!-- more -->

## export
```
// profile.js
var firstName = 'Michael';
var lastName = 'Jackson';
var year = 1958;

export {firstName, lastName, year};
// 或者, 类似与 alias
export {
	v1 as firstName,
    v2 as lastName,
    v3 as year
}
```

## import
```
import { firstName, lastName, year } from './profile';
// 或者，别名
import { lastName as surname } from './profile';
```
大括号里面的变量名，必须与被导入模块（profile.js）对外接口的名称相同。

