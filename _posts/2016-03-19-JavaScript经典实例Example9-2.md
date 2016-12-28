---
date: 2016-03-19 10:26:30+00:00
layout: post
title: JavaScript经典实例 示例9-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

演示防止重复表单提交
----------------

<html xmlns="http://www.w3.org/1999/xthml">
<head>
<title>Prevent Duplication Form Submission</title>
<style>
#refresh
{
    display: none;
    width: 200px;
    height: 20px;
    backgroud-color: #ffff00;
}
</style>
<script>
//<![CDTAT[

var inprocess = false;

window.onload = function(){
    document.forms["picker"].onsubmit = validateSubmit;
    document.getElementById("refresh").onclick = startOver;
}

function validateSubmit(){
    
    //防止重复的表单提交
    if(inprocess){
        return;
    }
    inprocess = true;
    document.getElementById("submitbutton").disabled = true;
    
    //只是示例
    document.getElementById("refresh").style.display = "block";
    document.getElementById("message").innerHTML = "<p>We're now processing your request, which can take a minute.<p>";
    
    //验证内容
    return false;
}

function startOver(){
    inprocess = false;
    document.getElementById("submitbutton").disabled = false;
    document.getElementById("message").innerHTML = "";
    document.getElementById("refresh").style.display = "none";
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
Input 1:<input type="text" id="intext" />
Input 2:<input type="text" id="intext2" />
Input 3:<input type="text" id="intext3" /><br /><br />
<input type="submit" id="submitbutton" value="Send form" />
</form>
<div id="refresh">
<p>Click to reset example</p>
</div>
<div id="message"></div>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xthml">
<head>
<title>Prevent Duplication Form Submission</title>
<style>
#refresh
{
    display: none;
    width: 200px;
    height: 20px;
    backgroud-color: #ffff00;
}
</style>
<script>
//<![CDTAT[

var inprocess = false;

window.onload = function(){
    document.forms["picker"].onsubmit = validateSubmit;
    document.getElementById("refresh").onclick = startOver;
}

function validateSubmit(){
    
    //防止重复的表单提交
    if(inprocess){
        return;
    }
    inprocess = true;
    document.getElementById("submitbutton").disabled = true;
    
    //只是示例
    document.getElementById("refresh").style.display = "block";
    document.getElementById("message").innerHTML = "<p>We're now processing your request, which can take a minute.<p>";
    
    //验证内容
    return false;
}

function startOver(){
    inprocess = false;
    document.getElementById("submitbutton").disabled = false;
    document.getElementById("message").innerHTML = "";
    document.getElementById("refresh").style.display = "none";
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
Input 1:<input type="text" id="intext" />
Input 2:<input type="text" id="intext2" />
Input 3:<input type="text" id="intext3" /><br /><br />
<input type="submit" id="submitbutton" value="Send form" />
</form>
<div id="refresh">
<p>Click to reset example</p>
</div>
<div id="message"></div>
</body>
</html>
``` 
