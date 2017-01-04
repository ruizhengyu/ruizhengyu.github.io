---
date: 2016-05-08 15:46:30+00:00
layout: post
title: JavaScript经典实例 示例21-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
[示例21-1](http://lovechina.xyz/JavaScript%E7%BB%8F%E5%85%B8%E5%AE%9E%E4%BE%8BExample21-1/)中的ePub阅读器，使用一个Web Worker来反转内容
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
                var inputElement = document.getElementById('file');
                
                inputElement.addEventListener('change', handleFiles, false);
            }
            
            function handleFiles() {
                var fileList = this.files,
                    reader = new FileReader();
                    
                reader.onload = loadFile;
                reader.readAsText(fileList[0]);
            }
            
            function loadFile() {
                
                // 查找文档的body部分
                var parser = new DOMParser(),
                    xml = parser.parseFromString(this.result,'text/xml'),
                    content = xml.getElementsByTagName('body');
                
                // 如果找到，提取body元素的innerHTML
                if (content.length > 0) {
                    var ct = content[0].innerHTML,
                        ctarray = ct.split(' '),
                        worker = new Worker('reverse.js');
                        
                    worker.onmessage = receiveResult;
                    worker.postMessage(ctarray);
                }
            
            }
            
            function receiveResult(event) {
                document.getElementById('result').innerHTML = event.data;
            }
        </script>
    </head>
    <body>
        <form>
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
                var inputElement = document.getElementById('file');
                
                inputElement.addEventListener('change', handleFiles, false);
            }
            
            function handleFiles() {
                var fileList = this.files,
                    reader = new FileReader();
                    
                reader.onload = loadFile;
                reader.readAsText(fileList[0]);
            }
            
            function loadFile() {
                
                // 查找文档的body部分
                var parser = new DOMParser(),
                    xml = parser.parseFromString(this.result,'text/xml'),
                    content = xml.getElementsByTagName('body');
                
                // 如果找到，提取body元素的innerHTML
                if (content.length > 0) {
                    var ct = content[0].innerHTML,
                        ctarray = ct.split(' '),
                        worker = new Worker('reverse.js');
                        
                    worker.onmessage = receiveResult;
                    worker.postMessage(ctarray);
                }
            
            }
            
            function receiveResult(event) {
                document.getElementById('result').innerHTML = event.data;
            }
        </script>
    </head>
    <body>
        <form>
            <label for="file">File:</label> <input type="file" id="file" /><br />
        </form>
        <div id="result"></div>
    </body>
</html>
``` 
