---
date: 2016-05-10 14:46:30+00:00
layout: post
title: JavaScript经典实例 源码6-1-inherit
categories: JavaScript权威指南
tags:  JavaScript  JavaScript权威指南
---
通过原型继承创建一个新的对象
----------------
 


源码如下：

``` javascript
// inherit() returns a newly created object that inherits properties from the
// prototype object p.  It uses the ECMAScript 5 function Object.create() if
// it is defined, and otherwise falls back to an older technique.
function inherit(p) {
    if (p == null) throw TypeError(); // p must be a non-null object
    if (Object.create)                // If Object.create() is defined...
        return Object.create(p);      //    then just use it.
    var t = typeof p;                 // Otherwise do some more type checking
    if (t !== "object" && t !== "function") throw TypeError();
    function f() {};                  // Define a dummy constructor function.
    f.prototype = p;                  // Set its prototype property to p.
    return new f();                   // Use f() to create an "heir" of p.
}
``` 
