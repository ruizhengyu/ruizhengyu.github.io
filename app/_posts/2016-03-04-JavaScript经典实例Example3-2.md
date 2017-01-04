---
date: 2016-03-04 18:44:30+00:00
layout: post
title: JavaScript经典实例 示例3-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

在一个setInterval定时器参数内使用一个匿名函数
----------------

<head>
<title>interval and anonymous function</title>
<style>
#redbox
{
    position: absolute;
    left: 10px;
    top: 10px;
    width: 20px; 
    height: 20px;
    background-color: red;
}
</style>
<script>
var intervalId = null;

window.onload = function(){
    document.getElementById("redbox").onclick = stopStartElement;
}

function stopStartElement(){
    if(intervalId === null){
        var x = 100;
        intervalId = setInterval(function(){
            x += 5;
            var left = x + "px";
            document.getElementById("redbox").style.left = left;
        },100);
    }else{
        clearInterval(intervalId);
        intervalId = null;
    }
}
</script>
</head>
<body>
<div id="redbox"></div>
</body>


源码如下：

``` html
<!DOCTYPE html>
<head>
<title>interval and anonymous function</title>
<style>
#redbox
{
    position: absolute;
    left: 100px;
    top: 100px;
    width: 200px; 
    height: 200px;
    background-color: red;
}
</style>
<script>
var intervalId = null;

window.onload = function(){
    document.getElementById("redbox").onclick = stopStartElement;
}

function stopStartElement(){
    if(intervalId === null){
        var x = 100;
        intervalId = setInterval(function(){
            x += 5;
            var left = x + "px";
            document.getElementById("redbox").style.left = left;
        },100);
    }else{
        clearInterval(intervalId);
        intervalId = null;
    }
}
</script>
</head>
<body>
<div id="redbox"></div>
</body>
``` 
