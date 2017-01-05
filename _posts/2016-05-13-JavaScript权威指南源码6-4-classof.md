---
date: 2016-05-13 21:56:30+00:00
layout: post
title: JavaScript经典实例 源码6-3-classof
categories: JavaScript权威指南
tags:  JavaScript  JavaScript权威指南
---
classof()函数
----------------

源码如下：

``` javascript
function classof(o) {
    if (o === null) return "Null";
    if (o === undefined) return "Undefined";
    return Object.prototype.toString.call(o).slice(8,-1);
}
``` 
