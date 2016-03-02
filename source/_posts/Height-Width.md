title: 'Height && Width'
tags:
  - JS
categories: []
date: 2015-11-16 16:19:00
---
### <code style="color: red; border-radius: 5px;">read-only</code> clientWidth
The `Element.clientWidth` property is zero for elements with no CSS or inline layout boxes, otherwise it's the inner width of an element in pixels. 

It includes padding but **not the vertical scrollbar (if present, if rendered), border or margin.**

![clientWidth && clientHeight](https://mdn.mozillademos.org/files/346/Dimensions-client.png)

### <code style="color: red; border-radius: 5px;">read-only</code> offsetWidth

returns the layout width of an element。

Typically, an element's offsetWidth is a measurement which includes the element **borders, the element horizontal padding, the element vertical scrollbar (if present, if rendered) and the element CSS width.**

![offsetWidth](https://mdn.mozillademos.org/files/347/Dimensions-offset.png)