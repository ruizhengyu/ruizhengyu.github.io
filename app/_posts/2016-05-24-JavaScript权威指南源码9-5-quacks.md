---
date: 2016-05-24 16:16:30+00:00
layout: post
title: JavaScript经典实例 源码9-5-quacks
categories: JavaScript权威指南
tags:  JavaScript  JavaScript权威指南
---
利用鸭式辩型实现的函数
----------------

源码如下：

``` javascript
// Return true if o implements the methods specified by the remaining args.
function quacks(o /*, ... */) {
    for(var i = 1; i < arguments.length; i++) {  // for each argument after o
        var arg = arguments[i];
        switch(typeof arg) { // If arg is a:
        case 'string':       // string: check for a method with that name
            if (typeof o[arg] !== "function") return false;
            continue;
        case 'function':     // function: use the prototype object instead
            // If the argument is a function, we use its prototype object
            arg = arg.prototype;
            // fall through to the next case
        case 'object':       // object: check for matching methods
            for(var m in arg) { // For each property of the object
                if (typeof arg[m] !== "function") continue; // skip non-methods
                if (typeof o[m] !== "function") return false;
            }
        }
    }
    
    // If we're still here, then o implements everything
    return true;
}
``` 
