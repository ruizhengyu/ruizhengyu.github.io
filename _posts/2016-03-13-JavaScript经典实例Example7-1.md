---
date: 2016-03-13 10:26:30+00:00
layout: post
title: JavaScript经典实例 示例7-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

捕获鼠标点击位置并将元素移动到该位置
----------------

<html xmlns = "http://www.w3.org/1999/xhtml">
<head>
<title>Box Click Box Move</title>
<style type="text/css">
#info
{
    width: 100px; height: 100px;
    background-color: #ff0000;
    position: absolute;
    top: 0;
    left: 0;
}
</style>
<script type="text/javascript">

window.onload = function(){
    document.onclick = processClick;
}

function processClick(evt){
    evt = evt || window.event;
    var x = 0,
        y = 0;
    if(evt.pageX){
        x = evt.pageX;
        y = evt.pageY;
    }else if(evt.clientX){
        var offsetX = 0,
            offsetY = 0;
        if(document.documentElement.scrollLeft){
            offsetX = document.documentElement.scrollLeft;
            offsetY = document.documentElement.scrollTop;
        }else if(document.body){
            offsetX = document.body.scrollLeft;
            offsetY = document.body.scrollTop;
        }
        x = evt.clientX + offsetX;
        y = evt.clientY + offsetY;
    }
    var style = "left:" + x + "px; top:" + y + "px";
    var box = document.getElementById("info");
    box.setAttribute("style", style);
}

//--><!]]>
</script>
</head>
<body>
<div id="info"></div>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns = "http://www.w3.org/1999/xhtml">
<head>
<title>Box Click Box Move</title>
<style type="text/css">
#info
{
    width: 100px; height: 100px;
    background-color: #ff0000;
    position: absolute;
    top: 0;
    left: 0;
}
</style>
<script type="text/javascript">

window.onload = function(){
    document.onclick = processClick;
}

function processClick(evt){
    evt = evt || window.event;
    var x = 0,
        y = 0;
    if(evt.pageX){
        x = evt.pageX;
        y = evt.pageY;
    }else if(evt.clientX){
        var offsetX = 0,
            offsetY = 0;
        if(document.documentElement.scrollLeft){
            offsetX = document.documentElement.scrollLeft;
            offsetY = document.documentElement.scrollTop;
        }else if(document.body){
            offsetX = document.body.scrollLeft;
            offsetY = document.body.scrollTop;
        }
        x = evt.clientX + offsetX;
        y = evt.clientY + offsetY;
    }
    var style = "left:" + x + "px; top:" + y + "px";
    var box = document.getElementById("info");
    box.setAttribute("style", style);
}

//--><!]]>
</script>
</head>
<body>
<div id="info"></div>
</body>
</html>
``` 