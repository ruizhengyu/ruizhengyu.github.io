---
date: 2016-03-17 23:26:30+00:00
layout: post
title: JavaScript经典实例 示例8-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

通过链接上的hash保存页面状态
----------------

<html xmls="http://ww.w3.org/1999/xhtml">
<head>
<title>Remember me?</title>
<script>

window.onload = function(){
    
    //设置按钮
    document.getElementById("next").onclick = nextPanel;
    
    //检查hash，如果找到的话，重新载入状态
    var hash = window.location.hash.split("#")[1];
    switch(hash){
        case "one":
            functionOne();
            break;
        case "two":
            functionOne();
            functionTwo();
            break;
        case "three":
            functionOne();
            functionTwo();
            functionThree();
    }
}

//根据按钮的类，显示下一个面板
function nextPanel(){
    var classNm = this.getAttribute("class");
    switch(classNm){
        case "zero":
            functionOne();
            break;
        case "one":
            functionTwo();
            break;
        case "two":
            functionThree();
    }
}
//设置按钮类，并创建状态链接
//添加到页面
function setPage(page){
    document.getElementById("next").setAttribute("class", page);
    var link = document.getElementById("link");
    var path = location.protocol + "//" + location.hostname + "/" + location.pathname + "#" + page;
    link.innerHTML = "<p><a href='" + path + "'>link</a><p>";
}

//one、two、three的函数来修改div，设置按钮和链接
function functionOne(){
    var square = document.getElementById("square");
    square.style.backgroundColor = "#ffff00";
    square.style.width = "200px";
    square.style.height = "200px";
    square.style.padding = "10px";
    square.style.margin = "20px";
    setPage("one");
}

function functionTwo(){
    var square = document.getElementById("square");
    square.style.backgroundColor = "#ff0000";
    square.style.position = "absolute";
    square.style.left = "200px";
    setPage("two");
}

function functionThree(){
    var square = document.getElementById("square");
    square.style.width = "400px";
    square.style.height = "400px";
    square.style.backgroundColor = "#00ff00";
    square.style.left = "400px";
    setPage("three");
}

</script>
</head>
<body>
<button id="next" class="zero">Next Action</button>
<div id="square">
<p>This is the object</p>
<div id = "link"></div>
</div>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmls="http://ww.w3.org/1999/xhtml">
<head>
<title>Remember me?</title>
<script>

window.onload = function(){
    
    //设置按钮
    document.getElementById("next").onclick = nextPanel;
    
    //检查hash，如果找到的话，重新载入状态
    var hash = window.location.hash.split("#")[1];
    switch(hash){
        case "one":
            functionOne();
            break;
        case "two":
            functionOne();
            functionTwo();
            break;
        case "three":
            functionOne();
            functionTwo();
            functionThree();
    }
}

//根据按钮的类，显示下一个面板
function nextPanel(){
    var classNm = this.getAttribute("class");
    switch(classNm){
        case "zero":
            functionOne();
            break;
        case "one":
            functionTwo();
            break;
        case "two":
            functionThree();
    }
}
//设置按钮类，并创建状态链接
//添加到页面
function setPage(page){
    document.getElementById("next").setAttribute("class", page);
    var link = document.getElementById("link");
    var path = location.protocol + "//" + location.hostname + "/" + location.pathname + "#" + page;
    link.innerHTML = "<p><a href='" + path + "'>link</a><p>";
}

//one、two、three的函数来修改div，设置按钮和链接
function functionOne(){
    var square = document.getElementById("square");
    square.style.backgroundColor = "#ffff00";
    square.style.width = "200px";
    square.style.height = "200px";
    square.style.padding = "10px";
    square.style.margin = "20px";
    setPage("one");
}

function functionTwo(){
    var square = document.getElementById("square");
    square.style.backgroundColor = "#ff0000";
    square.style.position = "absolute";
    square.style.left = "200px";
    setPage("two");
}

function functionThree(){
    var square = document.getElementById("square");
    square.style.width = "400px";
    square.style.height = "400px";
    square.style.backgroundColor = "#00ff00";
    square.style.left = "400px";
    setPage("three");
}

</script>
</head>
<body>
<button id="next" class="zero">Next Action</button>
<div id="square">
<p>This is the object</p>
<div id = "link"></div>
</div>
</body>
</html>
``` 

`hash` 属性是一个可读可写的字符串，该字符串是 URL 的锚部分（从 # 号开始的部分）。
