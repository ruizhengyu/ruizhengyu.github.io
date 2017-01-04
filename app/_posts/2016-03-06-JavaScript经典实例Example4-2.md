---
date: 2016-03-06 18:44:30+00:00
layout: post
title: JavaScript经典实例 示例4-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

将一个SVG圆放入一个div元素中
----------------

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Using Math method to fit a circle</title>
<style text = "text/css">
#elem
{
    width: 400px;
    height: 200px;
    border: 1px solid #000;
}
</style>
<script type="text/javascript">
//<![CDATA[

function compStyle(elemId, property){
    var elem = document.getElementById(elemId);
    var style;
    if(window.getComputedStyle)
        style = window.getComputedStyle(elem, null).getPropertyValue(property);
    else if(elem.currentStyle)
        style = elem.currentStyle[property];
    return style;
}
window.onload = function(){
    var height = parseInt(compStyle("elem", "height"));
    var width = parseInt(compStyle("elem", "width"));
    
    var x = width / 2;
    var y = height /2;
    
    var circleRadius = Math.min(width, height) / 2;
    var circ = document.getElementById("circ");
    circ.setAttribute("r", circleRadius);
    circ.setAttribute("cx", x);
    circ.setAttribute("cy", y);
}

//--><!]]>
</script>
</head>
<body>
<div id = "elem">
    <svg xlmns = "http://www.w3.org/2000/svg" width = "600" height = "600">
        <circle id = "circ" width = "10" height = "10" r = "10" fill = "red" />
    </svg>
</div>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Using Math method to fit a circle</title>
<style text = "text/css">
#elem
{
    width: 400px;
    height: 200px;
    border: 1px solid #000;
}
</style>
<script type="text/javascript">
//<![CDATA[

function compStyle(elemId, property){
    var elem = document.getElementById(elemId);
    var style;
    if(window.getComputedStyle)
        style = window.getComputedStyle(elem, null).getPropertyValue(property);
    else if(elem.currentStyle)
        style = elem.currentStyle[property];
    return style;
}
window.onload = function(){
    var height = parseInt(compStyle("elem", "height"));
    var width = parseInt(compStyle("elem", "width"));
    
    var x = width / 2;
    var y = height /2;
    
    var circleRadius = Math.min(width, height) / 2;
    var circ = document.getElementById("circ");
    circ.setAttribute("r", circleRadius);
    circ.setAttribute("cx", x);
    circ.setAttribute("cy", y);
}

//--><!]]>
</script>
</head>
<body>
<div id = "elem">
    <svg xlmns = "http://www.w3.org/2000/svg" width = "600" height = "600">
        <circle id = "circ" width = "10" height = "10" r = "10" fill = "red" />
    </svg>
</div>
</body>
</html>
``` 

一个 HTMLElement 的 style 属性是一个可读可写的 CSS2Properties 对象，就好像 CSSStyleRule 对象的 style 属性一样。不过，Window.getComputedStyle() 的返回值是一个 CSS2Properties 对象，其属性是只读的。

currentStyle获取计算后的样式，也叫当前样式、最终样式。优点：可以获取元素的最终样式，包括浏览器的默认值，而不像style只能获取行间样式，所以更常用到。注意：不能获取复合样式如background属性值，只能获取单一样式如background-color等。

parseInt() 函数可解析一个字符串，并返回一个整数。`parseInt(string, radix)`  string:必需。要被解析的字符串。
radix:可选。表示要解析的数字的基数。该值介于 2 ~ 36 之间。如果省略该参数或其值为 0，则数字将以 10 为基础来解析。如果它以 “0x” 或 “0X” 开头，将以 16 为基数。如果该参数小于 2 或者大于 36，则 parseInt() 将返回 NaN。

setAttribute() 方法添加指定的属性，并为其赋指定的值。如果这个指定的属性已存在，则仅设置/更改值。`element.setAttribute(attributename,attributevalue)`  attributename:类型为String；必需。您希望添加的属性的名称。attributevalue：类型为String；必需。您希望添加的属性值。
