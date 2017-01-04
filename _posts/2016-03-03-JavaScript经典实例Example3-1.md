---
date: 2016-03-03 18:44:30+00:00
layout: post
title: JavaScript经典实例 示例3-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

把ISO 8601格式日期转换为JavaScript Date
----------------

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Converting ISO 8601 date</title>
<style type = "text/css">
#dateSubmit
{
    background-color: #ff0;
    width: 200px;
    text-align: center;
    border: 10px solid #ccc;
}
</style>
<script type="text/javascript">
//<![CDATA[

window.onload = function(){
    document.getElementById("dateSubmit").onclick = convertDate;
}

function convertDate(){
    var dtstr = document.getElementById("datestring").value;
    var convdate = convertISO8601toDate(dtstr);
    document.getElementById("result").innerHTML = convdate;
}

function convertISO8601toDate(dtstr){
    
    //将任何非数字的字符替换为空格
    dtstr = dtstr.replace(/\D/g," ");
    
    //清除末尾的任何空格
    dtstr = dtstr.replace(/\s+$/,"");
    
    //根据空格分割字符串
    var dtcomps = dtstr.split(" ");
    
    //并非所有的ISO 8601日期都可以转换，
    //除非月份和日期都指定了，否则是无效的
    if(dtcomps.length < 3) return "invalid date"
    //如果没有提供时间，将其设置为0
    if(dtcomps.length < 4) {
        dtcomps[3] = 0;
        dtcomps[4] = 0;
        dtcomps[5] = 0;
    }
    
    //
    dtcomps[1]--;
    var convdt = new Date(Date.UTC(dtcomps[0], dtcomps[1], dtcomps[2], dtcomps[3], dtcomps[4], dtcomps[5]));
    
    return convdt.toUTCString();
}
//--><!]]>

</script>
</head>
<body>
<form>
<p>Datestring in ISO 8601 format: <input type = "text" id = "datestring" placeholder="2009-10-15T14:42:51Z" value="2009-10-15T14:42:51Z"/></p>
</form>
<div id = "dateSubmit" ><p>Convert Date</p></div>
<div id="result"></div>
</body>
</html>


源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Converting ISO 8601 date</title>
<style type = "text/css">
#dateSubmit
{
    background-color: #ff0;
    width: 200px;
    text-align: center;
    border: 1px solid #ccc;
}
</style>
<script type="text/javascript">
//<![CDATA[

window.onload = function(){
    document.getElementById("dateSubmit").onclick = convertDate;
}

function convertDate(){
    var dtstr = document.getElementById("datestring").value;
    var convdate = convertISO8601toDate(dtstr);
    document.getElementById("result").innerHTML = convdate;
}

function convertISO8601toDate(dtstr){
    
    //将任何非数字的字符替换为空格
    dtstr = dtstr.replace(/\D/g," ");
    
    //清除末尾的任何空格
    dtstr = dtstr.replace(/\s+$/,"");
    
    //根据空格分割字符串
    var dtcomps = dtstr.split(" ");
    
    //并非所有的ISO 8601日期都可以转换，
    //除非月份和日期都指定了，否则是无效的
    if(dtcomps.length < 3) return "invalid date"
    //如果没有提供时间，将其设置为0
    if(dtcomps.length < 4) {
        dtcomps[3] = 0;
        dtcomps[4] = 0;
        dtcomps[5] = 0;
    }
    
    //
    dtcomps[1]--;
    var convdt = new Date(Date.UTC(dtcomps[0], dtcomps[1], dtcomps[2], dtcomps[3], dtcomps[4], dtcomps[5]));
    
    return convdt.toUTCString();
}
//--><!]]>

</script>
</head>
<body>
<form>
<p>Datestring in ISO 8601 format: <input type = "text" id = "datestring" /></p>
</form>
<div id = "dateSubmit" ><p>Convert Date</p></div>
<div id="result"></div>
</body>
</html>
``` 
