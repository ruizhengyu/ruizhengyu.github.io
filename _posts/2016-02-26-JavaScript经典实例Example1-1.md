---
date: 2016-02-26 20:44:30+00:00
layout: post
title: JavaScript经典实例 示例1-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

展示使用String.split来获取关键字列表
----------------

<html>
<head>
<title>Example 1-1</title>
<meta http-equiv="Content-Type" content="text/html;charset=utf-8">
<script type="text/javascript">
window.onload = function(){
    var keywordList = prompt("Ente Keywords, separated by commas","1,2,3");
	var arrayList = keywordList.split(",");
	var resultString = "";
	for (var i = 0; i < arrayList.length; i++){
        resultString += "keyword:" + arrayList[i] + "<br />";
	}
	var blk = document.getElementById("result");
	blk.innerHTML = resultString;
};
</script>
</head>
<body>
<div id="result">
</div>
</body>
</html>


源码如下：

``` html
<!DOCTYPE html>
<head>
<title>Example 1-1</title>
<meta http-equiv="Content-Type" content="text/html;charset=utf-8">
<script type="text/javascript">

window.onload = function(){

    //获取关键字列表
    var keywordList = prompt("Ente Keywords, separated by commas","");
    
    //use split to create array of keywords
	var arrayList = keywordList.split(",");
    
    //构建最终HTML
	var resultString = "";
	for (var i = 0; i < arrayList.length; i++){
        resultString += "keyword:" + arrayList[i] + "<br />";
	}
    
    //打印到页面
	var blk = document.getElementById("result");
	blk.innerHTML = resultString;
};

</script>
</head>
<body>
<div id="result">
</div>
</body>
</html>
``` 

**`JavaScript split()` 方法**

定义和用法

split() 方法用于把一个字符串分割成字符串数组。

语法

``` html
stringObject.split(separator,howmany)
``` 

| 参数	        |                      描述 				                           | 
| separator     |必需。字符串或正则表达式，从该参数指定的地方分割 stringObject。                  |
| howmany       |可选。该参数可指定返回的数组的最大长度。如果设置了该参数，返回的子串不会多于这个参数指定的数组。如果没有设置该参数，整个字符串都会被分割，不考虑它的长度。 |

返回值

一个字符串数组。该数组是通过在 separator 指定的边界处将字符串 stringObject 分割成子串创建的。返回的数组中的字串不包括 separator 自身。

但是，如果 separator 是包含子表达式的正则表达式，那么返回的数组中包括与这些子表达式匹配的字串（但不包括与整个正则表达式匹配的文本）。

提示和注释

注释：如果把空字符串 ("") 用作 `separator`，那么 `stringObject` 中的每个字符之间都会被分割。

注释：`String.split()` 执行的操作与 `Array.join` 执行的操作是相反的。

**`HTML DOM prompt()` 方法**

定义和用法

prompt() 方法用于显示可提示用户进行输入的对话框。

语法
``` html
prompt(text,defaultText)
``` 

| 参数	        |                      描述 				        	| 
| text          | 可选。要在对话框中显示的纯文本（而不是 HTML 格式的文本）。    	|
| defaultText   | 可选。默认的输入文本。                                                |

说明

如果用户单击提示框的取消按钮，则返回 null。如果用户单击确认按钮，则返回输入字段当前显示的文本。
在用户点击确定按钮或取消按钮把对话框关闭之前，它将阻止用户对浏览器的所有输入。在调用 prompt() 时，将暂停对 JavaScript 代码的执行，在用户作出响应之前，不会执行下一条语句。

