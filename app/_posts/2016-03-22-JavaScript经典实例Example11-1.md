---
date: 2016-03-22 16:26:30+00:00
layout: post
title: JavaScript经典实例 示例11-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

展示getElementsByTagName和NodeList动态集合属性
----------------

<html xmlns="http://www.w3.org/1999/xthml" xml:lang="en">
<head>
<title>NodeList</title>
<script>
//<![CDTAT[

window.onload = function(){
    var imgs = document.getElementsByTagName('img');
    var blk1 = document.getElementById("result1");
    blk1.innerHTML = imgs.length;
    var p = document.createElement("p");
    var img = document.createElement("img");
    img.src = "http://lovechina.xyz/assets/media/image/orchids4.preview.jpg";
    p.appendChild(img);
    
    var paras = document.getElementsByTagName('p');
    paras[0].parentNode.appendChild(p);
    
    var blk2 = document.getElementById("result2");
    blk2.innerHTML = imgs.length;
    
}

//--><!]]>
</script>
</head>
<body>
<p><img src="http://lovechina.xyz/assets/media/image/orchids12.preview.jpg" alt="Orchid from MBG 2009 orchid show" /></p>
<p><img src="http://lovechina.xyz/assets/media/image/orchids6.preview.jpg" alt="Orchid from MBG 2009 orchid show" /></p>
<p><img src="http://lovechina.xyz/assets/media/image/orchids9.preview.jpg" alt="Orchid from MBG 2009 orchid show" /></p>
<div id="result1"></div>
<div id="result2"></div>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xthml" xml:lang="en" lang="en">
<head>
<title>NodeList</title>
<script>
//<![CDTAT[

window.onload = function(){
    var imgs = document.getElementsByTagName('img');
    alert(imgs.length);
    var p = document.createElement("p");
    var img = document.createElement("img");
    img.src = "orchids4.preview.jpg";
    p.appendChild(img);
    
    var paras = document.getElementsByTagName('p');
    paras[0].parentNode.appendChild(p);
    
    alert(imgs.length);
}

//--><!]]>
</script>
</head>
<body>
<p><img src="orchids12.preview.jpg" alt="Orchid from MBG 2009 orchid show" /></p>
<p><img src="orchids6.preview.jpg" alt="Orchid from MBG 2009 orchid show" /></p>
<p><img src="orchids9.preview.jpg" alt="Orchid from MBG 2009 orchid show" /></p>
</body>
</html>
``` 
