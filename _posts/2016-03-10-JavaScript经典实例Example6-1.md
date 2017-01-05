---
date: 2016-03-10 12:54:30+00:00
layout: post
title: JavaScript经典实例 示例6-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

标量参数和数组参数的功能性区别
----------------

<html xmlns = "http://www.w3.org/1999/xhtml">
<head>
<title>Function test</title>
<script type="text/javascript">
//<![CDATA

window.onload = function(){
    var items = new Array('apple', 'orange', 'cherry', 'lime');
    var sep = '*';
    var blk1 = document.getElementById("result1");
    blk1.innerHTML = items + "  " + sep;
    concatenateString(items, sep);
    var blk2 = document.getElementById("result2");
    blk2.innerHTML = items;
    var blk3 = document.getElementById("result3");
    blk3.innerHTML = sep;
    //alert(items);
    //alert(sep);
}

function concatenateString(strings, separator){
    var result = "";
    for(var i = 0; i < strings.length; i++){
        result += strings[i] + separator;
    }
    
    //将result赋值给separator
    separator = result;
    
    //和数组
    strings[strings.length] = result;
}

//--><!]]>
</script>
</head>
<body>
<div id="result1"></div>
<div id="result2"></div>
<div id="result3"></div>
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
    var items = new Array('apple', 'orange', 'cherry', 'lime');
    var sep = '*';
    concatenateString(items, sep);
    
    alert(items);
    alert(sep);
}

function concatenateString(strings, separator){
    var result = "";
    for(var i = 0; i < strings.length; i++){
        result += strings[i] + separator;
    }
    
    //将result赋值给separator
    separator = result;
    
    //和数组
    strings[strings.length] = result;
}

//--><!]]>
</script>
</head>
<body>
</body>
</html>
``` 
