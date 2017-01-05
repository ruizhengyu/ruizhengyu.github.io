---
date: 2016-04-10 15:06:30+00:00
layout: post
title: JavaScript经典实例 示例15-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

SVG文件中的JavaScript的展示
----------------

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="600" height="600">
    <script type="text/javascript">
        
        // 设置元素onclick 事件处理程序
        window.onload = function() {
            var square = document.getElementById('square');
            
            // onclick事件处理程序，修改圆的半径
            square.onclick = function() {
                var color = this.getAttribute('fill');
                if (color == '#f00') {
                    this.setAttribute('fill', '#00f');
                } else {
                    this.setAttribute('fill', '#f00');
                }
                
            }
            
        }
    </script>
    <rect id="square" width="400" height="400" fill="#f00" x="10" y="20" />
</svg>

源码如下：

``` html
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="600" height="600">
    <script type="text/javascript">
        
        // 设置元素onclick 事件处理程序
        window.onload = function() {
            var square = document.getElementById('square');
            
            // onclick事件处理程序，修改圆的半径
            square.onclick = function() {
                var color = this.getAttribute('fill');
                if (color == '#f00') {
                    this.setAttribute('fill', '#00f');
                } else {
                    this.setAttribute('fill', '#f00');
                }
                
            }
            
        }
    </script>
    <rect id="square" width="400" height="400" fill="#f00" x="10" y="20" />
</svg>
``` 
