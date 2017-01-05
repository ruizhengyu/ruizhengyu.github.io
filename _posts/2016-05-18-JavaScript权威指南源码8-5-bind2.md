---
date: 2016-05-18 20:46:30+00:00
layout: post
title: JavaScript经典实例 源码8-5-bind2
categories: JavaScript权威指南
tags:  JavaScript  JavaScript权威指南
---
ECMAScript3版本的Function.bind()方法
----------------

源码如下：

``` javascript
if (!Function.prototype.bind) {
    Function.prototype.bind = function(o /*, args */) {
        // Save the this and arguments values into variables so we can
        // use them in the nested function below.
        var self = this, boundArgs = arguments;

        // The return value of the bind() method is a function
        return function() {
            // Build up an argument list, starting with any args passed
            // to bind after the first one, and follow those with all args
            // passed to this function.
            var args = [], i;
            for(i = 1; i < boundArgs.length; i++) args.push(boundArgs[i]);
            for(i = 0; i < arguments.length; i++) args.push(arguments[i]);
            
            // Now invoke self as a method of o, with those arguments
            return self.apply(o, args);
        };
    };
}
``` 
