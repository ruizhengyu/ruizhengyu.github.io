---
date: 2016-04-12 19:26:30+00:00
layout: post
title: JavaScript经典实例 示例15-5
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

从脚本中访问object元素中的SVG
----------------

<html>
    <head>
        <title>SVG in Object</title>
        <meta charset="utf-8" />
    </head>
    <body>
        <object id="object" data="http://lovechina.xyz/assets/media/image/rect.svg" style="padding: 20px; width: 600px; height: 600px;">
            <p>No SVG support</p>
        </object>
        <script type="text/javascript">
            var object = document.getElementById('object');
            
            object.onload = function() {
                var svgdoc;
                
                // 访问SVG文档对象
                try {
                    svgdoc = object.contentDocument;
                } catch(e) {
                    try{
                        svgdoc = object.getSVGDocument();
                    } catch(e) {
                        alert('SVG in object not supported in your environment');
                    }
                    
                }
                
                if (!svgdoc) {
                    return;
                }
                
                var r = svgdoc.rootElement;
                
                // 获取SVG元素并修改
                var square = svgdoc.getElementById('square');
                
                square.onclick = function() {
                    
                    // SVG支持命名空间
                    var width = parseFloat(square.getAttributeNS(null, 'width'));
                    
                    width -= 50;
                    square.setAttributeNS(null, 'width', width);
                    var color = square.getAttributeNS(null, 'fill');
                    
                    if (color === 'blue') {
                        square.setAttributeNS(null, 'fill', 'yellow');
                        square.setAttributeNS(null, 'stroke', 'green');
                    } else {
                        square.setAttributeNS(null, 'fill', 'blue');
                        square.setAttributeNS(null, 'stroke', 'red');
                    }
                    
                }
                
            }
        </script>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>SVG in Object</title>
        <meta charset="utf-8" />
    </head>
    <body>
        <object id="object" data="http://lovechina.xyz/assets/media/image/rect.svg" style="padding: 20px; width: 600px; height: 600px;">
            <p>No SVG support</p>
        </object>
        <script type="text/javascript">
            var object = document.getElementById('object');
            
            object.onload = function() {
                var svgdoc;
                
                // 访问SVG文档对象
                try {
                    svgdoc = object.contentDocument;
                } catch(e) {
                    try{
                        svgdoc = object.getSVGDocument();
                    } catch(e) {
                        alert('SVG in object not supported in your environment');
                    }
                    
                }
                
                if (!svgdoc) {
                    return;
                }
                
                var r = svgdoc.rootElement;
                
                // 获取SVG元素并修改
                var square = svgdoc.getElementById('square');
                
                square.onclick = function() {
                    
                    // SVG支持命名空间
                    var width = parseFloat(square.getAttributeNS(null, 'width'));
                    
                    width -= 50;
                    square.setAttributeNS(null, 'width', width);
                    var color = square.getAttributeNS(null, 'fill');
                    
                    if (color === 'blue') {
                        square.setAttributeNS(null, 'fill', 'yellow');
                        square.setAttributeNS(null, 'stroke', 'green');
                    } else {
                        square.setAttributeNS(null, 'fill', 'blue');
                        square.setAttributeNS(null, 'stroke', 'red');
                    }
                    
                }
                
            }
        </script>
    </body>
</html>
``` 
