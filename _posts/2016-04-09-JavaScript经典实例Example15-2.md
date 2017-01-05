---
date: 2016-04-09 14:46:30+00:00
layout: post
title: JavaScript经典实例 示例15-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

使用定时器动态地更新一个线条图表
----------------

<html>
    <head>
        <title>Canvas Chart</title>
        <meta charset="utf-8" />
        <script type="text/javascript">           
            window.onload = function() {
                var array1 = [[100, 100], [150, 50], [200, 185],[250, 185], [300, 250], [350, 100], [400, 250], [450, 100], [500, 20], [550, 80], [600, 120]],
                    array2 = [[100, 100], [150, 150], [200, 135],[250, 285], [300, 150], [350, 150], [400, 280], [450, 100], [500, 120], [550, 80], [600, 190]],
                    array3 = [[100, 200], [150, 100], [200, 35],[250, 185], [300, 10], [350, 15], [400, 80], [450, 100], [500, 120], [550, 80], [600, 120]],
                    imgcanvas = document.getElementById('imgcanvas');
                
                if (imgcanvas.getContext) {
                    var ctx = imgcanvas.getContext('2d');
                    
                    // 矩形包围线条图表
                    ctx.strokeRect(0, 0, 600, 300);
                    
                    // 第一条线条
                    ctx.beginPath();
                    ctx.moveTo(0, 100);
                    for (var i = 0; i < array1.length; i++) {
                        ctx.lineTo(array1[i][0], array1[i][1]);
                    }
                
                    ctx.stroke();
                    setTimeout(function() {
                        ctx.strokeStyle = '#f00';
                        
                        // 第二条线条
                        ctx.beginPath();
                        ctx.moveTo(0, 100);
                        for (var i = 0; i < array2.length; i++) {
                            ctx.lineTo(array2[i][0], array2[i][1]);
                        }
                        
                        ctx.stroke();
                        
                        // 第二次延迟
                        setTimeout(function() {
                            ctx.strokeStyle = '#0f0';
                            ctx.fillStyle = 'rgba(255, 255, 0, .1)';
                            
                            // 第三条线条
                            ctx.beginPath();
                            ctx.moveTo(0, 100);
                            for (var i = 0; i < array3.length; i++) {
                                ctx.lineTo(array3[i][0], array3[i][1]);
                            }
                            
                            ctx.stroke();
                        }, 5000);
                    }, 5000);
                }
            }
        </script>
    </head>
    <body>
        <canvas id="imgcanvas" width="650" height="350">
            <p>Include an image that has a static reresentation of the chart</p>
        </canvas>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Canvas Chart</title>
        <meta charset="utf-8" />
        <script type="text/javascript">           
            window.onload = function() {
                var array1 = [[100, 100], [150, 50], [200, 185],[250, 185], [300, 250], [350, 100], [400, 250], [450, 100], [500, 20], [550, 80], [600, 120]],
                    array2 = [[100, 100], [150, 150], [200, 135],[250, 285], [300, 150], [350, 150], [400, 280], [450, 100], [500, 120], [550, 80], [600, 190]],
                    array3 = [[100, 200], [150, 100], [200, 35],[250, 185], [300, 10], [350, 15], [400, 80], [450, 100], [500, 120], [550, 80], [600, 120]],
                    imgcanvas = document.getElementById('imgcanvas');
                
                if (imgcanvas.getContext) {
                    var ctx = imgcanvas.getContext('2d');
                    
                    // 矩形包围线条图表
                    ctx.strokeRect(0, 0, 600, 300);
                    
                    // 第一条线条
                    ctx.beginPath();
                    ctx.moveTo(0, 100);
                    for (var i = 0; i < array1.length; i++) {
                        ctx.lineTo(array1[i][0], array1[i][1]);
                    }
                
                    ctx.stroke();
                    setTimeout(function() {
                        ctx.strokeStyle = '#f00';
                        
                        // 第二条线条
                        ctx.beginPath();
                        ctx.moveTo(0, 100);
                        for (var i = 0; i < array2.length; i++) {
                            ctx.lineTo(array2[i][0], array2[i][1]);
                        }
                        
                        ctx.stroke();
                        
                        // 第二次延迟
                        setTimeout(function() {
                            ctx.strokeStyle = '#0f0';
                            ctx.fillStyle = 'rgba(255, 255, 0, .1)';
                            
                            // 第三条线条
                            ctx.beginPath();
                            ctx.moveTo(0, 100);
                            for (var i = 0; i < array3.length; i++) {
                                ctx.lineTo(array3[i][0], array3[i][1]);
                            }
                            
                            ctx.stroke();
                        }, 5000);
                    }, 5000);
                }
            }
        </script>
    </head>
    <body>
        <canvas id="imgcanvas" width="650" height="350">
            <p>Include an image that has a static reresentation of the chart</p>
        </canvas>
    </body>
</html>
``` 
