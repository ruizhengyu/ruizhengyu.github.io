---
date: 2016-02-28 13:44:30+00:00
layout: post
title: JavaScript经典实例 示例2-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

使用exec和全局标识来查找并突出显示一个文本字符串中的所有匹配
----------------

<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Searching for strings</title>
        <style type="text/css">
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
        <script type="text/javascript">
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
                
                    matchArray,
                    resultString = '<pre>',
                    first = 0,
                    last = 0;
                
                // 找到每一个匹配
                while((matchArray = re.exec(searchString)) != null) {
                    last = matchArray.index;
                    
                    // 获取所有匹配的字符串，将其连接起来
                    resultString += searchString.substring(first, last);
                
                    // 使用class，添加匹配的字符串
                    resultString += '<span class="found">' + matchArray[0] + '</span>';
                    first = re.lastIndex;a
                }
                
                // 完成字符串
                resultString += searchString.substring(first,searchString.length);
                resultString += '</pre>';
                
                // 插入到页面
                document.getElementById('searchResult').innerHTML = resultString;
            }
            
        //--><!]]>
        </script>
    </head>
    <body>
        <form id="textsearch">
            <textarea id="incoming" cols="150" rows="10">
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
        <style type="text/css">
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
        <script type="text/javascript">
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
                
                    matchArray,
                    resultString = '<pre>',
                    first = 0,
                    last = 0;
                
                // 找到每一个匹配
                while((matchArray = re.exec(searchString)) != null) {
                    last = matchArray.index;
                    
                    // 获取所有匹配的字符串，将其连接起来
                    resultString += searchString.substring(first, last);
                
                    // 使用class，添加匹配的字符串
                    resultString += '<span class="found">' + matchArray[0] + '</span>';
                    first = re.lastIndex;a
                }
                
                // 完成字符串
                resultString += searchString.substring(first,searchString.length);
                resultString += '</pre>';
                
                // 插入到页面
                document.getElementById('searchResult').innerHTML = resultString;
            }
            
        //--><!]]>
        </script>
    </head>
    <body>
        <form id="textsearch">
            <textarea id="incoming" cols="150" rows="10">
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