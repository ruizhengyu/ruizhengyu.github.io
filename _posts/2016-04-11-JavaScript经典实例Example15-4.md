---
date: 2016-04-11 16:46:30+00:00
layout: post
title: JavaScript经典实例 示例15-4
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

SVG文件中的JavaScript的展示
----------------

<html xmlns="http://www.w3.org/1999/xthml" xmlns:svg="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" xml:lang="en">
    <head>
        <title>Accessing Inline SVG</title>
        <meta http-equiv="Content-Type" content="application/xhtml+xml; charset=utf-8" />
    </head>
    <body>
        <svg:svg width="600" height="600">
            <script type="text/ecmascript">
                <![CDATA[ 
                    
                    // 设置元素onclick 事件处理程序
                    window.onload = function() {
                        var square = document.getElementById('square');
                        
                        // onclick事件处理程序，修改圆的半径
                        square.onclick = function() {
                            var color = this.getAttribute('fill');
                            if (color === '#f00') {
                                this.setAttribute('fill', '#00f');
                            } else {
                                this.setAttribute('fill', '#f00');
                            }
                            
                        }
                        
                    }
                ]]>
            </script>
            <svg:rect id="square" width="400" height="400" fill="#f00" x="10" y="10" />
        </svg:svg>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1 plus MathML 2.0 plus SVG 1.1//EN" "http://www.w3.org/2002/04/xhtml-math-svg/xthml-math-svg.dtd">
<html xmlns="http://www.w3.org/1999/xthml" xmlns:svg="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" xml:lang="en">
    <head>
        <title>Accessing Inline SVG</title>
        <meta http-equiv="Content-Type" content="application/xhtml+xml; charset=utf-8" />
    </head>
    <body>
        <svg:svg width="600" height="600">
            <script type="text/ecmascript">
                <![CDATA[ 
                    
                    // 设置元素onclick 事件处理程序
                    window.onload = function() {
                        var square = document.getElementById('square');
                        
                        // onclick事件处理程序，修改圆的半径
                        square.onclick = function() {
                            var color = this.getAttribute('fill');
                            if (color === '#f00') {
                                this.setAttribute('fill', '#00f');
                            } else {
                                this.setAttribute('fill', '#f00');
                            }
                            
                        }
                        
                    }
                ]]>
            </script>
            <svg:rect id="square" width="400" height="400" fill="#f00" x="10" y="10" />
        </svg:svg>
    </body>
</html>
``` 
