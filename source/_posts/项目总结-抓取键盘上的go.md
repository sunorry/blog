title: 项目总结-抓取键盘上的go
tags: []
categories:
  - 项目总结
date: 2015-11-30 11:45:00
---
客栈关键字搜索页面
<!-- more -->

点击键盘上的「搜索、go、」等键时，抓取这个事件。

将上面的 `input` 标签写在 `form` 中。
```
<form method="post" id="form" action="#">
<input type="text">
</form>
```

```
form.onsubmit = function() {
    var value = self.doms.input.value;        
    return false;
};
```

搞定。
