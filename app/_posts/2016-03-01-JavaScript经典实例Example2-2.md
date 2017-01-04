---
date: 2016-03-01 14:44:30+00:00
layout: post
title: JavaScript经典实例 示例2-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

使用String.replace和特殊模式在字符串中查找文本并突出显示
----------------

<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Searching for strings</title>
        <style>
            #searchSubmit
            {
                background-color: #ff0;
                width: 200px;
                text-align: center;
                padding: 10px;
                border: 2px inset #ccc;
            }
            
            .found
            {
                background-color: #ff0;
            }
            
        </style>
        <script>
        //<![CDATA[
            
            window.onload = function() {
                document.getElementById('searchSubmit').onclick = doSearch;
            }
            
            function doSearch() {
                
                // 获取模式
                var pattern = document.getElementById('pattern').value,
                    re = new RegExp(pattern,'g'),
                
                // 获取字符串
                    searchString = document.getElementById('incoming').value,
                
                // 替换
                    resultString = searchString.replace(re,'<span class="found">$&</span>');
                
                // 插入到页面
                document.getElementById('searchResult').innerHTML = resultString;
            }
            
        //--><!]]>
        </script>
    </head>
    <body>
        <form id="textsearch">
            <textarea id="incoming" cols="100" rows="10">
            </textarea>
            <p>
                Search pattern: <input id="pattern" type="text" />
            </p>
        </form>
        <p id="searchSubmit">Search for pattern</p>
        <div id="searchResult"></div>
    </body>
</html>


源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Searching for strings</title>
        <style>
            #searchSubmit
            {
                background-color: #ff0;
                width: 200px;
                text-align: center;
                padding: 10px;
                border: 2px inset #ccc;
            }
            
            .found
            {
                background-color: #ff0;
            }
            
        </style>
        <script>
        //<![CDATA[
            
            window.onload = function() {
                document.getElementById('searchSubmit').onclick = doSearch;
            }
            
            function doSearch() {
                
                // 获取模式
                var pattern = document.getElementById('pattern').value,
                    re = new RegExp(pattern,'g'),
                
                // 获取字符串
                    searchString = document.getElementById('incoming').value,
                
                // 替换
                    resultString = searchString.replace(re,'<span class="found">$&</span>');
                
                // 插入到页面
                document.getElementById('searchResult').innerHTML = resultString;
            }
            
        //--><!]]>
        </script>
    </head>
    <body>
        <form id="textsearch">
            <textarea id="incoming" cols="100" rows="10">
            </textarea>
            <p>
                Search pattern: <input id="pattern" type="text" />
            </p>
        </form>
        <p id="searchSubmit">Search for pattern</p>
        <div id="searchResult"></div>
    </body>
</html>
``` 