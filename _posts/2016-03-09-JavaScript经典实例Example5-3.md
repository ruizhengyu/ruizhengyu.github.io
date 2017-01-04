---
date: 2016-03-09 12:54:30+00:00
layout: post
title: JavaScript经典实例 示例5-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

使用表单元素展示关联数组
----------------

<html xmlns = "http://www.w3.org/1999/xhtml">
<head>
<title>Associative Array</title>
<script type="text/javascript">
//<![CDATA

//获取表单元素的名称和值
function getVals(){
    var elems = document.getElementById("picker").elements;
    var elemArray = new Object();
    for(var i = 0; i < elems.length; i++){
        if(elems[i].type === "text"){
            elemArray[elems[i].id] = elems[i].value;
        }
    }
    checkVals(elemArray);
    return false;
}

//检查值
function checkVals(elemArray){
    var str = "";
    for(var key in elemArray){
        str += key + "," + elemArray[key] + " ";
    }
    document.getElementById("result").innerHTML = str;
}

//--><!]]>
</script>
</head>
<body>
<form id="picker" onsubmit="return getVals()">
<label>Value 1:</label> <input type="text" id="first" placeholder="1" value="1"/><br />
<label>Value 2:</label> <input type="text" id="second" placeholder="2" value="2"/><br />
<label>Value 3:</label> <input type="text" id="third" placeholder="3" value="3"/><br />
<label>Value 3:</label> <input type="text" id="four" placeholder="4" value="4"/><br />
<input type="submit" value="Validte" />
</form>
<div id="result"></div>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns = "http://www.w3.org/1999/xhtml">
<head>
<title>Associative Array</title>
<script type="text/javascript">
//<![CDATA

//获取表单元素的名称和值
function getVals(){
    var elems = document.getElementById("picker").elements;
    var elemArray = new Object();
    for(var i = 0; i < elems.length; i++){
        if(elems[i].type === "text"){
            elemArray[elems[i].id] = elems[i].value;
        }
    }
    checkVals(elemArray);
    return false;
}

//检查值
function checkVals(elemArray){
    var str = "";
    for(var key in elemArray){
        str += key + "," + elemArray[key] + " ";
    }
    document.getElementById("result").innerHTML = str;
}

//--><!]]>
</script>
</head>
<body>
<form id="picker" onsubmit="return getVals()">
<label>Value 1:</label> <input type="text" id="first" /><br />
<label>Value 2:</label> <input type="text" id="second" /><br />
<label>Value 3:</label> <input type="text" id="third" /><br />
<label>Value 3:</label> <input type="text" id="four" /><br />
<input type="submit" value="Validte" />
</form>
<div id="result"></div>
</body>
</html>
``` 
