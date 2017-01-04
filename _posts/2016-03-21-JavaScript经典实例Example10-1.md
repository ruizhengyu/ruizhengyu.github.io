---
date: 2016-03-21 14:26:30+00:00
layout: post
title: JavaScript经典实例 示例10-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

如果脚本关闭的话，表单元素默认地设置为显示，如果支持脚本的话，则会隐藏
----------------

<html xmlns="http://www.w3.org/1999/xthml">
<head>
<title>Populating Selection Lists</title>
<script>
//<![CDTAT[

var inprocess = false;

window.onload = function(){
    document.getElementById("hidden_elements").style.display = "none";
    
    // 把点击事件处理程序绑定到按钮
    var radios = document.forms[0].elements["group1"];
    for (var i = 0; i < radios.length; i++) {
        radios[i].onclick = radioClicked;
    }
}

function radioClicked() {
    if (this.value == "two") {
        document.getElementById("hidden_elements").style.display = "block";
    } else {
        document.getElementById("hidden_elements").style.display = "none";
    }
}

//--><!]]>
</script>
</head>
<body>
<form id="picker" method="post" action="">
Group 1:<input type="radio" name="group1" value="one"/><br />
Group 2:<input type="radio" name="group1" value="two"/><br />
Group 3:<input type="radio" name="group1" value="three"/><br />
<br />
<div id="hidden_elements">
Input 1:<input type="text" id="intext" />
Input 2:<input type="text" id="intext2" />
Input 3:<input type="text" id="intext3" /><br /><br />
</div>
<input type="submit" id="submitbutton" value="Send form" />
</form>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xthml">
<head>
<title>Populating Selection Lists</title>
<script>
//<![CDTAT[

var inprocess = false;

window.onload = function(){
    document.getElementById("hidden_elements").style.display = "none";
    
    // 把点击事件处理程序绑定到按钮
    var radios = document.forms[0].elements["group1"];
    for (var i = 0; i < radios.length; i++) {
        radios[i].onclick = radioClicked;
    }
}

function radioClicked() {
    if (this.value == "two") {
        document.getElementById("hidden_elements").style.display = "block";
    } else {
        document.getElementById("hidden_elements").style.display = "none";
    }
}

//--><!]]>
</script>
</head>
<body>
<form id="picker" method="post" action="">
Group 1:<input type="radio" name="group1" value="one"/><br />
Group 2:<input type="radio" name="group1" value="two"/><br />
Group 3:<input type="radio" name="group1" value="three"/><br />
<br />
<div id="hidden_elements">
Input 1:<input type="text" id="intext" />
Input 2:<input type="text" id="intext2" />
Input 3:<input type="text" id="intext3" /><br /><br />
</div>
<input type="submit" id="submitbutton" value="Send form" />
</form>
</body>
</html>
``` 
