---
date: 2016-05-06 15:06:30+00:00
layout: post
title: JavaScript经典实例 示例21-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
把一个ePub章节上传到Web页面中
----------------

<html>
    <head>
        <title>ePub Reader</title>
        <meta charset="utf-8" />
        <style>
            #result
            {
                width: 500px;
                margin: 30px;
            }
            
        </style>
        <script>
            window.onload = function() {
                var inputElement = document.getElementById("file");
                
                inputElement.addEventListener('change', handleFiles, false);
            }
            
            function handleFiles() {
                var fileList = this.files,
                    reader = new FileReader();
                    
                reader.onload = loadFile;
                reader.readAsText(fileList[0]);
            }
            
            function loadFile() {
                
                // 查找文档中的body部分
                var parser = new DOMParser(),
                    xml = parser.parseFromString(this.result,'text/xml'),
                    content = xml.getElementsByTagName('body');
                
                // 如果找到，提取body元素的innerHTML
                if (content.length > 0) {
                    var ct = content[0].innerHTML,
                        title = document.getElementById('bookTitle').value;
                        
                    title = '<h2>' + title + '</title>';
                    document.getElementById('result').innerHTML = title + ct;
                }
            }
        </script>
    </head>
    <body>
        <form>
            <label for="title">Title:</label>
            <input type="text" id="bookTitle" /></br ><br />
            <label for="file">File:</label> <input type="file" id="file" /><br />
        </form>
        <div id="result"></div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>ePub Reader</title>
        <meta charset="utf-8" />
        <style>
            #result
            {
                width: 500px;
                margin: 30px;
            }
            
        </style>
        <script>
            window.onload = function() {
                var inputElement = document.getElementById("file");
                
                inputElement.addEventListener('change', handleFiles, false);
            }
            
            function handleFiles() {
                var fileList = this.files,
                    reader = new FileReader();
                    
                reader.onload = loadFile;
                reader.readAsText(fileList[0]);
            }
            
            function loadFile() {
                
                // 查找文档中的body部分
                var parser = new DOMParser(),
                    xml = parser.parseFromString(this.result,'text/xml'),
                    content = xml.getElementsByTagName('body');
                
                // 如果找到，提取body元素的innerHTML
                if (content.length > 0) {
                    var ct = content[0].innerHTML,
                        title = document.getElementById('bookTitle').value;
                        
                    title = '<h2>' + title + '</title>';
                    document.getElementById('result').innerHTML = title + ct;
                }
            }
        </script>
    </head>
    <body>
        <form>
            <label for="title">Title:</label>
            <input type="text" id="bookTitle" /></br ><br />
            <label for="file">File:</label> <input type="file" id="file" /><br />
        </form>
        <div id="result"></div>
    </body>
</html>
``` 
