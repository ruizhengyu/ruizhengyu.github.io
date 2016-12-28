---
date: 2016-03-14 21:26:30+00:00
layout: post
title: JavaScript经典实例 示例7-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

阻止一个事件在嵌套元素之间传播
----------------

<head>
<title>Prevent Propagation</title>
<style type="text/css">
#one
{
    width: 100px;
    height: 100px;
    background-color: #0f0;
}
#two
{
    width: 50px;
    height: 50px;
    background-color: #f00;
}
#stop
{
    display: block;
}
</style>
<script type="text/javascript">

//标记取消事件传播的全局变量
var stopPropagation = false;
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

//取消传播
function cancelPropagation(event){
    if(event.stopPropagation){
        event.stopPropagation();
    }else{
        event.cancelPropagation = true;
    }    
}

listenEvent(window, "load", function(){
    listenEvent(document.getElementById("one"), "click", clickBoxOne);
    listenEvent(document.getElementById("two"), "click", clickBoxTwo);
    listenEvent(document.getElementById("stop"), "click", stopProp);
});

function stopProp(){
    stopPropagation = true;
}

function clickBoxOne(evt){
    alert("Hello from One");
}

function clickBoxTwo(evt){
    alert("Hi from Two");
    if(stopPropagation){
        cancelPropagation(evt);
    }
}

</script>
</head>
<body>
<div id="one">
<div id="two">
<p>Inner</p>
</div>
</div>
<button id="stop">Stop Propagation</button>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<head>
<title>Prevent Propagation</title>
<style type="text/css">
#one
{
    width: 100px;
    height: 100px;
    background-color: #0f0;
}
#two
{
    width: 50px;
    height: 50px;
    background-color: #f00;
}
#stop
{
    display: block;
}
</style>
<script type="text/javascript">

//标记取消事件传播的全局变量
var stopPropagation = false;
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

//取消传播
function cancelPropagation(event){
    if(event.stopPropagation){
        event.stopPropagation();
    }else{
        event.cancelPropagation = true;
    }    
}

listenEvent(window, "load", function(){
    listenEvent(document.getElementById("one"), "click", clickBoxOne);
    listenEvent(document.getElementById("two"), "click", clickBoxTwo);
    listenEvent(document.getElementById("stop"), "click", stopProp);
});

function stopProp(){
    stopPropagation = true;
}

function clickBoxOne(evt){
    alert("Hello from One");
}

function clickBoxTwo(evt){
    alert("Hi from Two");
    if(stopPropagation){
        cancelPropagation(evt);
    }
}

</script>
</head>
<body>
<div id="one">
<div id="two">
<p>Inner</p>
</div>
</div>
<button id="stop">Stop Propagation</button>
</body>
</html>
``` 

addEventListener() 方法用于向指定元素添加事件句柄。

`element.addEventListener(event, function, useCapture)`    `event`	必须。字符串，指定事件名。注意: 不要使用 "on" 前缀。 例如，使用 "click" ,而不是使用 "onclick"。 

`function`	必须。指定要事件触发时执行的函数。 当事件对象会作为第一个参数传入函数。 事件对象的类型取决于特定的事件。例如， "click" 事件属于 `MouseEvent`(鼠标事件) 对象。

`useCapture`	可选。布尔值，指定事件是否在捕获或冒泡阶段执行。可能值:
true - 事件句柄在捕获阶段执行
false- false- 默认。事件句柄在冒泡阶段执行
