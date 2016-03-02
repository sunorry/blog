title: version limit
tags: []
categories:
  - 温故知新
date: 2016-03-01 11:22:00
---
版本号的限制，老是忘了，复习一次吧。


```
"grunt-contrib-copy" : "^0.7.3"
"grunt" : "~0.4.1"
```

`^` 是一种标宽松的限制，只限制主版本号，如上面的，只要 0 不变，`install` 时就会不断更新；
`~` 是最小版本号才会更新。