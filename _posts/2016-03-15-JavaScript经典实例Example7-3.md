---
date: 2016-03-15 21:26:30+00:00
layout: post
title: JavaScript经典实例 示例7-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

根据按键的ASCII值阻止一个按键值
----------------

<html>
<head>
<title>Filtering Input</title>
<script>

var badChar;

function listenEvent(eventTarget, eventType, eventHandler){
    if(eventTarget.addEventListener){
        eventTarget.addEventListener(eventType, eventHandler, false);
    }else if(eventTarget.attachEvent){
        eventType = "on" + eventType;
        eventTarget.attachEvent(eventType, eventHandler);
    }else{
        eventTarget["on" + eventType] = eventHandler;
    }
}

//取消事件
function cancelEvent(event){
    if(event.preventDefault){
        event.preventDefault();
        event.stopPropagation();
    }else{
        event.returnValue = false;
        event.cancelBubble = true;
    }    
}

window.onload = function(){
    badChar = prompt("Enter the ASCII value of the keyboard key you want to filter", "97");
    var inputTA = document.getElementById("source");
    listenEvent(inputTA, "keypress", processClick);
}

function processClick(evt){
    evt = evt || window.event;
    var key = evt.charCode ? evt.charCode : evt.keyCode;
    //赶走坏孩子
    if(key == badChar){
        cancelEvent(evt);
    }
}

</script>
</head>
<body>
<form>
<textarea id="source" rows="20" cols="50"></textarea>
</form>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<head>
<title>Filtering Input</title>
<script>

var badChar;

function listenEvent(eventTarget, eventType, eventHandler){
    if(eventTarget.addEventListener){
        eventTarget.addEventListener(eventType, eventHandler, false);
    }else if(eventTarget.attachEvent){
        eventType = "on" + eventType;
        eventTarget.attachEvent(eventType, eventHandler);
    }else{
        eventTarget["on" + eventType] = eventHandler;
    }
}

//取消事件
function cancelEvent(event){
    if(event.preventDefault){
        event.preventDefault();
        event.stopPropagation();
    }else{
        event.returnValue = false;
        event.cancelBubble = true;
    }    
}

window.onload = function(){
    badChar = prompt("Enter the ASCII value of the keyboard key you want to filter", "");
    var inputTA = document.getElementById("source");
    listenEvent(inputTA, "keypress", processClick);
}

function processClick(evt){
    evt = evt || window.event;
    var key = evt.charCode ? evt.charCode : evt.keyCode;
    //赶走坏孩子
    if(key == badChar){
        cancelEvent(evt);
    }
}

</script>
</head>
<body>
<form>
<textarea id="source" rows="20" cols="50"></textarea>
</form>
</body>
</html>
``` 

event.stopPropagation() 方法阻止事件冒泡到父元素，阻止任何父事件处理程序被执行。

event.preventDefault() 方法阻止元素发生默认的行为。
