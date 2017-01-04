---
date: 2016-05-07 15:16:30+00:00
layout: post
title: JavaScript经典实例 示例21-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
使用Web WorkerJavaScript反转一个数组，并且返回结果字符串
----------------

源码如下：

``` javascript
// Web Worker线程，反转数组
onmessage = function(event) {

   var reverseArray = function(x,indx,str) {
      return indx == 0 ? str : reverseArray(x, --indx, (str += ' ' + x[indx]));;
   }

   // 反转数组
   var str = reverseArray(event.data, event.data.length, '');

   // 向主应用程序返回最终的字符串
   postMessage(str);
};
``` 
