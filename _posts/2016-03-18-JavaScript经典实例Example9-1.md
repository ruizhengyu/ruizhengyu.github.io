---
date: 2016-03-18 10:26:30+00:00
layout: post
title: JavaScript经典实例 示例9-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

根据一个被点击的单选按钮，关闭/打开输入元素
----------------

<html>
<head>
<title>Redio Click Pick</title>

<style>
:enabled{
    border: 4px solid #ff0000;
    padding: 5px 5px 5px 15px;
}

:disabled{
    border: 2px solid #cccccc;
}
</style>
<script>

window.onload = function(){
    
    //首先，关闭所有的输入字段
    document.forms[0].elements["intext"].disabled = true;
    document.forms[0].elements["intext2"].disabled = true;
    document.forms[0].elements["intext3"].disabled = true;
    
    //接下来，给单选按钮附加一个事件处理程序
    var radios = document.forms[0].elements["group1"];
    for( var i = 0; i < radios.length; i++){
        radios[i].onclick = radioClicked;
    }
}

function radioClicked(){
    
    //找到点击了哪个单选按钮
    //关闭/打开响应的输入元素
    switch(this.value){
        case "one":
            document.forms[0].elements["intext"].disabled = false;
            document.forms[0].elements["intext2"].disabled = true;
            document.forms[0].elements["intext3"].disabled = true;
            break;
        case "two":
            document.forms[0].elements["intext"].disabled = true;
            document.forms[0].elements["intext2"].disabled = false;
            document.forms[0].elements["intext3"].disabled = true;
            break;
        case "three":
            document.forms[0].elements["intext"].disabled = true;
            document.forms[0].elements["intext2"].disabled = true;
            document.forms[0].elements["intext3"].disabled = false;
            break;
    }
}

</script>
</head>
<body>
<form id="picker">
Group 1:<input type="radio" name="group1" value="one"/><br />
Group 2:<input type="radio" name="group1" value="two"/><br />
Group 3:<input type="radio" name="group1" value="three"/><br />
<br />
<input type="text" id="intext" />
<input type="text" id="intext2" />
<input type="text" id="intext3" />
</form>
</body>
</html>

源码如下：

``` html
<html>
<head>
<title>Redio Click Pick</title>

<style>
:enabled{
    border: 4px solid #ff0000;
    padding: 5px 5px 5px 15px;
}

:disabled{
    border: 2px solid #cccccc;
}
</style>
<script>

window.onload = function(){
    
    //首先，关闭所有的输入字段
    document.forms[0].elements["intext"].disabled = true;
    document.forms[0].elements["intext2"].disabled = true;
    document.forms[0].elements["intext3"].disabled = true;
    
    //接下来，给单选按钮附加一个事件处理程序
    var radios = document.forms[0].elements["group1"];
    for( var i = 0; i < radios.length; i++){
        radios[i].onclick = radioClicked;
    }
}

function radioClicked(){
    
    //找到点击了哪个单选按钮
    //关闭/打开响应的输入元素
    switch(this.value){
        case "one":
            document.forms[0].elements["intext"].disabled = false;
            document.forms[0].elements["intext2"].disabled = true;
            document.forms[0].elements["intext3"].disabled = true;
            break;
        case "two":
            document.forms[0].elements["intext"].disabled = true;
            document.forms[0].elements["intext2"].disabled = false;
            document.forms[0].elements["intext3"].disabled = true;
            break;
        case "three":
            document.forms[0].elements["intext"].disabled = true;
            document.forms[0].elements["intext2"].disabled = true;
            document.forms[0].elements["intext3"].disabled = false;
            break;
    }
}

</script>
</head>
<body>
<form id="picker">
Group 1:<input type="radio" name="group1" value="one"/><br />
Group 2:<input type="radio" name="group1" value="two"/><br />
Group 3:<input type="radio" name="group1" value="three"/><br />
<br />
<input type="text" id="intext" />
<input type="text" id="intext2" />
<input type="text" id="intext3" />
</form>
</body>
</html>
``` 
