---
date: 2016-03-16 23:26:30+00:00
layout: post
title: JavaScript经典实例 示例8-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

使用window.location构建一个面包屑路径
----------------

<html xmls="http://ww.w3.org/1999/xhtml">
<head>
<title>breadcrumb trail</title>
<script>
//<![CDATA

window.onload = function(){
    
    //分割相对路径
    var items = location.pathname.substr(1).split("/");
    
    //构建主路径
    var mainpath = "<a href='" + location.protocol + "//" + location.hostname + "/";
    
    //开始面包屑路径
    var breadcrumbTrail = "<p>";
    for(var i = 0; i < items.length; i++){
        
        //结尾的斜杠
        if(items[i].length == 0){
            break;
        }
        
        //将主路径扩展到一个新的层级
        mainpath += items[i];
        
        //在所有的项之后添加斜杠，最后一项除外
        if(i < items.length - 1){
            mainpath += "/"
        }
        
        //创建面包屑路径部分
        //仅对内部项添加箭头
        if(i > 0 && i < items.length){
            breadcrumbTrail += " -> ";
        }
        
        //添加面包屑
        breadcrumbTrail += mainpath + "'>" + items[i] + "</a>"
    }
    
    //插入到页面
    breadcrumbTrail += "</p>";
    document.getElementById("breadcrumb").innerHTML = breadcrumbTrail;
    
};

//--><!]]>
</script>
</head>
<body>
<div id = "breadcrumb"></div>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmls="http://ww.w3.org/1999/xhtml">
<head>
<title>breadcrumb trail</title>
<script>
//<![CDATA

window.onload = function(){
    
    //分割相对路径
    var items = location.pathname.substr(1).split("/");
    
    //构建主路径
    var mainpath = "<a href='" + location.protocol + "//" + location.hostname + "/";
    
    //开始面包屑路径
    var breadcrumbTrail = "<p>";
    for(var i = 0; i < items.length; i++){
        
        //结尾的斜杠
        if(items[i].length == 0){
            break;
        }
        
        //将主路径扩展到一个新的层级
        mainpath += items[i];
        
        //在所有的项之后添加斜杠，最后一项除外
        if(i < items.length - 1){
            mainpath += "/"
        }
        
        //创建面包屑路径部分
        //仅对内部项添加箭头
        if(i > 0 && i < items.length){
            breadcrumbTrail += " -> ";
        }
        
        //添加面包屑
        breadcrumbTrail += mainpath + "'>" + items[i] + "</a>"
    }
    
    //插入到页面
    breadcrumbTrail += "</p>";
    document.getElementById("breadcrumb").innerHTML = breadcrumbTrail;
    
};

//--><!]]>
</script>
</head>
<body>
<div id = "breadcrumb"></div>
</body>
</html>
``` 

`pathname` 属性是一个可读可写的字符串，可设置或返回当前 `URL` 的路径部分。
