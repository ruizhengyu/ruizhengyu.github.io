---
date: 2016-04-01 16:46:30+00:00
layout: post
title: JavaScript经典实例 示例12-7
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

展示设置和获取CSS样式设置
----------------

<html>
    <head>
        <title>Changing style</title>
        <meta charset="utf-8" />
        <style type="text/css">
            #elem
            {
                width: 200px;
                background-color: lime;
            }
            
        </style>
        <script type="text/javascript">
            function getStyle(elem, cssprop, cssprop2) {
                
                // IE
                if (elem.currentStyle) {
                    return elem.currentStyle[cssprop];
                
                // 其他浏览器
                } else if (document.defaultView && document.defaultView.getComputedStyle) {
                    return document.defaultView.getComputedStyle(elem, null).getPropertyValue(cssprop2);
                
                // 备用方案
                } else {
                    return null;
                }
                
            }
            
            window.onload = function() {
                
                // 设置和访问样式属性
                var elem = document.getElementById('elem'),
                    color = getStyle(elem, 'backgroundColor', 'background-color');
                
                alert(color); // rgb(0, 255, 0)
                elem.style.width = '500px';
                elem.style.backgroundColor = 'yellow';
                alert(elem.style.width); // 500px
                alert(elem.style.backgroundColor); // yellow
                
                // 数组表示法
                elem.style['fontFamily'] = 'Courier';
                
                // 展示覆盖属性
                var style = elem.getAttribute('style');
                
                alert(style); // 应该显示color: purple; width: 500px; background-color: yellow;
                elem.setAttribute('style', 'height: 100px');
                style = elem.getAttribute('style');
                alert(style); // 现在只显示高度，重置样式
                
                var font = getStyle(elem, 'fontFamily', 'font-family');
                
                alert(font); // 默认的字体
            }
            
        </script>
    </head>
    <body>
        <div id="elem" style="color: purple">
            testing
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Changing style</title>
        <meta charset="utf-8" />
        <style type="text/css">
            #elem
            {
                width: 200px;
                background-color: lime;
            }
            
        </style>
        <script type="text/javascript">
            function getStyle(elem, cssprop, cssprop2) {
                
                // IE
                if (elem.currentStyle) {
                    return elem.currentStyle[cssprop];
                
                // 其他浏览器
                } else if (document.defaultView && document.defaultView.getComputedStyle) {
                    return document.defaultView.getComputedStyle(elem, null).getPropertyValue(cssprop2);
                
                // 备用方案
                } else {
                    return null;
                }
                
            }
            
            window.onload = function() {
                
                // 设置和访问样式属性
                var elem = document.getElementById('elem'),
                    color = getStyle(elem, 'backgroundColor', 'background-color');
                
                alert(color); // rgb(0, 255, 0)
                elem.style.width = '500px';
                elem.style.backgroundColor = 'yellow';
                alert(elem.style.width); // 500px
                alert(elem.style.backgroundColor); // yellow
                
                // 数组表示法
                elem.style['fontFamily'] = 'Courier';
                
                // 展示覆盖属性
                var style = elem.getAttribute('style');
                
                alert(style); // 应该显示color: purple; width: 500px; background-color: yellow;
                elem.setAttribute('style', 'height: 100px');
                style = elem.getAttribute('style');
                alert(style); // 现在只显示高度，重置样式
                
                var font = getStyle(elem, 'fontFamily', 'font-family');
                
                alert(font); // 默认的字体
            }
            
        </script>
    </head>
    <body>
        <div id="elem" style="color: purple">
            testing
        </div>
    </body>
</html>
``` 
