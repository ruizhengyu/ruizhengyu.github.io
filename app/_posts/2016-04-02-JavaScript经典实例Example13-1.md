---
date: 2016-04-02 17:36:30+00:00
layout: post
title: JavaScript经典实例 示例13-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

根据定位位置和绝对定位，把元素移动到其他元素之上
----------------

<html>
    <head>
        <title>Locating Elements</title>
        <meta charset="utf-8" />
        <style type="text/css">
            div#a
            {
                width: 500px;
            }
            
            div
            {
                border: 1px solid #000;
                padding: 10px;
            }
            
            #cursor
            {
                position: absolute;
                background-color: #ff0;
                width: 20px;
                height: 20px;
                left: 500px;
                top: 300px
            }
            
        </style>
        <script type="text/javascript">
            function positionObject(obj) {
                var rect = obj.getBoundingClientRect();
                
                return [rect.left, rect.top];
            }
            
            window.onload = function() {
                var tst = document.documentElement.getBoundingClientRect(),
                    cont = 'A',
                    cursor = document.getElementById('cursor');
                
                alert(tst.top);
                while (cont) {
                    cont = prompt('Where do you want to move the cursor block?', 'A');
                    if (cont) {
                        cont = cont.toLowerCase();
                        if (cont === 'a' || cont === 'b' || cont === 'c') {
                            var elem = document.getElementById(cont),
                                pos = positionObject(elem);
                            
                            cursor.setAttribute('style', 'top: ' + pos[1] + 'px; left: ' + pos[0] + 'px');
                        }
                        
                    }
                    
                }
                
            }
            
        </script>
    </head>
    <body>
        <div id="a">
            <p>A</p>
            <div id="b">
                <p>B</p>
                <div id="c">
                    <p>C</p>
                </div>
            </div>
        </div>
        <div id="cursor"></div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Locating Elements</title>
        <meta charset="utf-8" />
        <style type="text/css">
            div#a
            {
                width: 500px;
            }
            
            div
            {
                border: 1px solid #000;
                padding: 10px;
            }
            
            #cursor
            {
                position: absolute;
                background-color: #ff0;
                width: 20px;
                height: 20px;
                left: 500px;
                top: 300px
            }
            
        </style>
        <script type="text/javascript">
            function positionObject(obj) {
                var rect = obj.getBoundingClientRect();
                
                return [rect.left, rect.top];
            }
            
            window.onload = function() {
                var tst = document.documentElement.getBoundingClientRect(),
                    cont = 'A',
                    cursor = document.getElementById('cursor');
                
                alert(tst.top);
                while (cont) {
                    cont = prompt('Where do you want to move the cursor block?', 'A');
                    if (cont) {
                        cont = cont.toLowerCase();
                        if (cont === 'a' || cont === 'b' || cont === 'c') {
                            var elem = document.getElementById(cont),
                                pos = positionObject(elem);
                            
                            cursor.setAttribute('style', 'top: ' + pos[1] + 'px; left: ' + pos[0] + 'px');
                        }
                        
                    }
                    
                }
                
            }
            
        </script>
    </head>
    <body>
        <div id="a">
            <p>A</p>
            <div id="b">
                <p>B</p>
                <div id="c">
                    <p>C</p>
                </div>
            </div>
        </div>
        <div id="cursor"></div>
    </body>
</html>
``` 
