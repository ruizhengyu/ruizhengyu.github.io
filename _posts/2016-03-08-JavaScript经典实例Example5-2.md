---
date: 2016-03-08 15:54:30+00:00
layout: post
title: JavaScript经典实例 示例5-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

使用循环和分割来替代和删除元素
----------------

<head>
<title>Looping and Splicing</title>
<meta http-equiv="Content-Type" content="text/html;charset=utf-8">
<script type="text/javascript">
window.onload = function(){
    var charSets = new Array("ab", "bb", "cd", "ab", "cc", "ab", "dd", "ab");
    var blk1 = document.getElementById("result1");
    blk1.innerHTML = charSets;
    //替换元素
    while(charSets.indexOf("ab") != -1){
        charSets.splice(charSets.indexOf("ab"), 1, "**");
    }
    //alert(charSets);
    var blk2 = document.getElementById("result2");
    blk2.innerHTML = charSets;
    
    //删除新元素
    while(charSets.indexOf("**") != -1){
        charSets.splice(charSets.indexOf("**"), 1);
    }
    //alert(charSets);
    var blk3 = document.getElementById("result3");
    blk3.innerHTML = charSets;
}
</script>
</head>
<body>
<div id="result1"></div>
<div id="result2"></div>
<div id="result3"></div>
</body>

源码如下：

``` html
<!DOCTYPE html>
<head>
<title>Looping and Splicing</title>
<meta http-equiv="Content-Type" content="text/html;charset=utf-8">
<script type="text/javascript">

var charSets = new Array("ab", "bb", "cd", "ab", "cc", "ab", "dd", "ab");

//替换元素
while(charSets.indexOf("ab") != -1){
    charSets.splice(charSets.indexOf("ab"), 1, "**");
}
alert(charSets);

//删除新元素
while(charSets.indexOf("**") != -1){
    charSets.splice(charSets.indexOf("**"), 1);
}
alert(charSets);

</script>
</head>
<body>
</body>
</html>
``` 
