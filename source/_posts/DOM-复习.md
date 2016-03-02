title: DOM 复习
tags:
  - basicFE
categories:
  - 温故知新
date: 2016-02-29 20:31:00
---
在做一个简单的 `event delegate` 例子的时候，看到了 `nodeName` 和 `tagName` 返回的结果一样，查阅了一些知识，也算是复习了。

<!-- more -->

## 节点
* HTML 元素通过元素节点表示
* 特性（attribute）通过特性节点
* 文档类型 -> 文档节点
* 注释 -> 注释节点

...

一共有 12 中节点类型。

## Node 类型
每个节点都有一共 `nodeType` 属性，用于表明节点的类型。节点类型由在 Node 类型中都由的下列 12 个数值常量来表示，任何节点类型必居其一：

* Node.ELEMENT_NODE（1） 
* Node.ATTRIBUTE_NODE (2)
* Node.TEXT_NODE (3)
* Node.CDATA_SECTION_NODE(4)
* Node.ENTITY_REFERENCE_NODE(5)
* Node.ENTITY_NODE (6)
* Node.PROCESSING_INSTRUCTION_NODE (7)
* Node.COMMENT_NODE (8)
* Node.DOCUMENT_NODE(9)
* Node.DOCUMENT_TYPE_NODE(10)
* Node.DOCUMENT_FRAGMENT_NODE(11)
* Node.NOTATION_NODE(12)

eg：确定节点类型


```JavaScript
// Node.Element_NODE 是常量
// 在 IE 中无效
if(someNode.nodeType == Node.Element_NODE) {
	alert('someNode 是一个元素');
}

// 兼容所有
if(someNode.nodeType == 1) {
	alert('someNode 是一个元素');
}
```

### 常用节点
#### nodeName && nodeVlaue
**对于元素节点**，nodeName 保存的是元素的标签名，nodeValue 是 null 。

```
if(someNode.nodeType == 1) {
	alert(someNode.nodeName); // "UL" 等
}
```

#### nodeName && tagName
要访问**元素**的标签名，可以使用 `nodeName` ，也可以使用 `tagName` 属性；这两个会返回相同的值（后者更清晰）

