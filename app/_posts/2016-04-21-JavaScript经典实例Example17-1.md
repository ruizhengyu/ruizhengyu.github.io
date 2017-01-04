---
date: 2016-04-21 13:56:30+00:00
layout: post
title: JavaScript经典实例 示例17-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
带有方法的简单JavaScript对象
----------------

源码如下：

``` javascript
var BBTest = {
    concatWithSpace : function(string1, string2) {
        return string1 + ' ' + string2;
    },
    discoverNumber : function(string, number) {
        return string.indexOf(number);
    },
    divideNumbers : function(value1, value2) {
        return value1 / value2;
    },
    addAndRound : function(value1, value2) {
        return Math.round(value1 + value2);
    }
    
}
``` 
