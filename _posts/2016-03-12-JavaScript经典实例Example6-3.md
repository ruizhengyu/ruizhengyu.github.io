---
date: 2016-03-12 18:26:30+00:00
layout: post
title: JavaScript经典实例 示例6-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

memorization的一个演示
----------------

<html xmlns = "http://www.w3.org/1999/xhtml">
<head>
<title>Testing Memoization</title>
<script type="text/javascript">
//<![CDATA

window.onload = function(){

    //Memoized的函数
    var fibonacci = function(){
        var memo = [0, 1];
        var fib = function(n){
            var result = memo[n];
            if(typeof result !== "number"){
                result = fib(n - 1) + fib(n - 2);
                memo[n] = result;
            }
            return result;
        };
        return fib;
    }();
    
    //nonmemoized的函数
    var fib = function(n){
        return n < 2 ? n : fib(n - 1) + fib(n - 2);
    };
    
    //运行nonmemo的函数，使用一个定时器
    console.time("non-memo");
    for(var i = 0; i <= 10; i++){
        console.log(i + " " + fib(i));
    }
    console.timeEnd("non-memo");
    
    //现在，运行memo的函数，使用一个定时器
    console.time("memo");
    for(var i = 0; i <= 10; i++){
        console.log(i + " " + fibonacci(i));
    }
    console.timeEnd("memo");
    
}

//--><!]]>
</script>
</head>
<body>
<p>content</p>
</body>
</html>
运行结果如下图
[![ ](/assets/media/image/2016-03-12-JavaScript经典实例Example6-3.png)](/assets/media/image/2016-03-12-JavaScript经典实例Example6-3.png)
源码如下：

``` html
<!DOCTYPE html>
<html xmlns = "http://www.w3.org/1999/xhtml">
<head>
<title>Testing Memoization</title>
<script type="text/javascript">
//<![CDATA

window.onload = function(){

    //Memoized的函数
    var fibonacci = function(){
        var memo = [0, 1];
        var fib = function(n){
            var result = memo[n];
            if(typeof result !== "number"){
                result = fib(n - 1) + fib(n - 2);
                memo[n] = result;
            }
            return result;
        };
        return fib;
    }();
    
    //nonmemoized的函数
    var fib = function(n){
        return n < 2 ? n : fib(n - 1) + fib(n - 2);
    };
    
    //运行nonmemo的函数，使用一个定时器
    console.time("non-memo");
    for(var i = 0; i <= 10; i++){
        console.log(i + " " + fib(i));
    }
    console.timeEnd("non-memo");
    
    //现在，运行memo的函数，使用一个定时器
    console.time("memo");
    for(var i = 0; i <= 10; i++){
        console.log(i + " " + fibonacci(i));
    }
    console.timeEnd("memo");
    
}

//--><!]]>
</script>
</head>
<body>
<p>content</p>
</body>
</html>
``` 