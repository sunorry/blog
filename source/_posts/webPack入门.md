title: webpack入门
tags:
  - webpack
categories:
  - Reactjs
date: 2015-11-30 15:07:00
---
[webpack vs grunt](http://survivejs.com/webpack_react/webpack_compared/)

里面有 [how to use Make with JavaScript](https://blog.jcoglan.com/2014/02/05/building-javascript-projects-with-make/) 可以看下，应该和普通的没差。


[webpack傻瓜式指南](http://zhuanlan.zhihu.com/FrontendMagazine/20367175)


## 什么是 webpack
webpack is a module bundler.

webpack takes modules with dependencies and generates static assets representing those modules. 他的目的就是把有依赖关系的各种文件打包成一系列的静态资源。

简单来说，它就是一个配置文件，主要分为三部分：
 - entry，入口文件
 - output，处理后的文件放在哪里
 - moudle 模块，要用什么不同的模块来处理各种类型的文件
 
 
 CommonJS和AMD是用于JavaScript模块管理的两大规范，前者定义的是模块的同步加载，主要用于NodeJS；而后者则是异步加载，通过requirejs等工具适用于前端。