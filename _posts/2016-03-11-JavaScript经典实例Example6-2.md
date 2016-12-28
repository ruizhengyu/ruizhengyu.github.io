---
date: 2016-03-11 15:26:30+00:00
layout: post
title: JavaScript经典实例 示例6-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

使用匿名函数
----------------

<html>
<head>
<title>Function test</title>
<script type="text/javascript">
//<![CDATA

window.onload = function(){

    var func = prompt("Enter function body:", "alert(x + \"\" + y)");
    var x = prompt("Enter value for x:", "Hello");
    var y = prompt("Enter value for y:", "World");
    
    var newFun = new Function("x", "y", func);
    var result = newFun(x, y);
}

//--><!]]>
</script>
</head>
<body>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns = "http://www.w3.org/1999/xhtml">
<head>
<title>Function test</title>
<script type="text/javascript">
//<![CDATA

window.onload = function(){

    var func = prompt("Enter function body:", "alert(x + \"\" + y)");
    var x = prompt("Enter value for x:", "Hello");
    var y = prompt("Enter value for y:", "World");
    
    var newFun = new Function("x", "y", func);
    var result = newFun(x, y);
}

//--><!]]>
</script>
</head>
<body>
</body>
</html>
``` 
