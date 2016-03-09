title: deferred
tags: []
categories:
  - basic
date: 2016-03-09 14:51:00
---
deferred

<!-- more -->

需求很简单：

```
function getData() {
  var d = new Deferred();
  
  // get Data ，可能异步也可能同步
  // d.resolve(data);
  
  return d;
}

getData().done(fucntion(data) {
  console.log(data)
})
```

可以是同步，也可以异步。

1. 同步

先调用了 `resolve` ,然后再 `done`,先把结果缓存，然后直接把结果给 `done` 的回调。

2. 异步

先调用了 `done`, 这时候用自定义事件把事件先 add ，当 `resolve` 的时候，再 fire 事件。

**写的好的地方**：


调用 bind ，分别是`all`, `done`, `fail`

两种情况：
 
 1. 同步，已经 relove 了
 2. 异步，结果还未返回

在 `bind` 里进行 status 判断，状态 OK ，则直接执行回调，不 OK ，自定义事件。

`all` 直接 bind(onResolvedOrRejected, onResolvedOrRejected) ,很优雅。

在 `reject`, `resolve` 中，

也是上面两种情况，

缓存结果 + fire 事件 。