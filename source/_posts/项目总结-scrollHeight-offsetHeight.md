title: '项目总结-scrollHeight && offsetHeight'
tags: []
categories:
  - 项目总结
date: 2015-11-30 11:13:00
---
bnbhybrid 的评论页面。
<!-- more -->

`ul` 设置了 `max-height`、`min-height`、`overflow`。

效果：当内容超过 `ul` 的最高高度时，显示 **fold** 按钮，设置 `min-height` 是防止只有一行的情况。

如何知道内容超过了 `max-height` 呢。

## offsetHeight `readonly`

一图顶千言。包括 `padding` , `border`。

**offsetWidth 包括了滚动条的宽度。** 

![offsetHeight](https://mdn.mozillademos.org/files/347/Dimensions-offset.png)

## scrollHeight `readonly`

高度包括了不可见的部分。

高度不包含`margin` ，包括 `padding`, `border` 不清楚。

![scrollHeight](https://mdn.mozillademos.org/files/672/scrollHeight.png)

所以只需用判断 `offsetHeight == scrollHeight` 即可。