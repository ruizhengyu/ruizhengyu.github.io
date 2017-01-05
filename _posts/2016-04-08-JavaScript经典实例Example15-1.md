---
date: 2016-04-08 14:16:30+00:00
layout: post
title: JavaScript经典实例 示例15-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

在一个canvas元素中创建3个矩形的跨浏览器应用程序
----------------

<html>
    <head>
        <title>Canvas Squares</title>
        <meta charset="utf-8" />
        <script type="text/javascript">           
            window.onload = function() {
                var imgcanvas = document.getElementById('imgcanvas');
                
                if (imgcanvas.getContext) {
                    var ctx = imgcanvas.getContext('2d');
                    
                    ctx.fillStyle = 'rgba(255, 0, 0, .1)';
                    ctx.strokeStyle = '#000';
                    
                    // 第一个矩形
                    ctx.fillRect(0, 0, 100, 100);
                    ctx.strokeRect(0, 0, 100, 100);
                    
                    // 第二个矩形
                    ctx.fillRect(50, 50, 100, 200);
                    
                    // 第三个矩形
                    ctx.strokeRect(80, 130, 200, 100);
                }
                
            }
        </script>
    </head>
    <body>
        <canvas id="imgcanvas" width="400" height="250">
            <p>Three rectangles,overlapping</p>
        </canvas>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Canvas Squares</title>
        <meta charset="utf-8" />
        <script type="text/javascript">           
            window.onload = function() {
                var imgcanvas = document.getElementById('imgcanvas');
                
                if (imgcanvas.getContext) {
                    var ctx = imgcanvas.getContext('2d');
                    
                    ctx.fillStyle = 'rgba(255, 0, 0, .1)';
                    ctx.strokeStyle = '#000';
                    
                    // 第一个矩形
                    ctx.fillRect(0, 0, 100, 100);
                    ctx.strokeRect(0, 0, 100, 100);
                    
                    // 第二个矩形
                    ctx.fillRect(50, 50, 100, 200);
                    
                    // 第三个矩形
                    ctx.strokeRect(80, 130, 200, 100);
                }
                
            }
        </script>
    </head>
    <body>
        <canvas id="imgcanvas" width="400" height="250">
            <p>Three rectangles,overlapping</p>
        </canvas>
    </body>
</html>
``` 
