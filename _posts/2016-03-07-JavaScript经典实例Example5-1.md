---
date: 2016-03-07 15:54:30+00:00
layout: post
title: JavaScript经典实例 示例5-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

创建一个多维数组
----------------

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>创建一个多维数组</title>
<script type="text/javascript">
//<![CDATA[

window.onload = function(){
        
    //设置数组长度
    var arrayLength = 3;
    
    //创建数组
    var multiArray = new Array(arrayLength);
    for(var i = 0; i < multiArray.length; i++){
        multiArray[i] = new Array(arrayLength);
    }
    
    //给第一个数组索引添加项
    multiArray[0][0] = "apple";
    multiArray[0][1] = "banana";
    multiArray[0][2] = "cherry";
    
    //给第二个数组索引添加项
    multiArray[1][0] = 2;
    multiArray[1][1] = 56;
    multiArray[1][2] = 83;
    
    //给第三个数组索引添加项
    multiArray[2][0] = ['test', 'again'];
    multiArray[2][1] = ['Java', 'script'];
    multiArray[2][2] = ['read', 'books'];
    
    //alert(multiArray);
    //alert(multiArray[2]);
    //alert(multiArray[2][2][0]);
    var blk1 = document.getElementById("result1");
    blk1.innerHTML = multiArray;
    var blk2 = document.getElementById("result2");
    blk2.innerHTML = multiArray[2];
    var blk3 = document.getElementById("result3");
    blk3.innerHTML = multiArray[2][2][0];
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
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>创建一个多维数组</title>
<script type="text/javascript">
//<![CDATA[

//设置数组长度
var arrayLength = 3;

//创建数组
var multiArray = new Array(arrayLength);
for(var i = 0; i < multiArray.length; i++){
    multiArray[i] = new Array(arrayLength);
}

//给第一个数组索引添加项
multiArray[0][0] = "apple";
multiArray[0][1] = "banana";
multiArray[0][2] = "cherry";

//给第二个数组索引添加项
multiArray[1][0] = 2;
multiArray[1][1] = 56;
multiArray[1][2] = 83;

//给第三个数组索引添加项
multiArray[2][0] = ['test', 'again'];
multiArray[2][1] = ['Java', 'script'];
multiArray[2][2] = ['read', 'books'];

alert(multiArray);
alert(multiArray[2]);
alert(multiArray[2][2][0]);

//--><!]]>
</script>
</head>
<body>
</body>
</html>
``` 

