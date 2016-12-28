---
date: 2016-05-02 19:46:30+00:00
layout: post
title: JavaScript经典实例 示例20-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
使用URL和查询字符串来保留状态
----------------

<html>
    <head>
        <title>Remember me?</title>
        <style>
            #square
            {
                position: absolute;
                left: 0;
                top: 100px;
                width: 100px;
                height: 100px;
                border: 1px solid #333;
                background-color: #ff0;
            }
            
            div p
            {
                margin: 10px;
            }
            
        </style>
        <script>
        
            // 找到http://www.netlobo.com/url_query_string_javascript.html
            function getQueryParam(name) {
                    name = name.replace(/[\[]/,'\\\[').replace(/[\]]/,'\\\]');
                    var regexS = '[\\?&]' + name + '=([^&#]*)',
                        regex = new RegExp( regexS ),
                        results = regex.exec( window.location.href );
                        
                    if(results === null){
                        return null;
                    } else {
                        return results[1];
                    }
                    
            }
            
            window.onload=function() {
            
                // 设置按钮
                document.getElementById('move').onclick=moveSquare;
                document.getElementById('size').onclick=resizeSquare;
                document.getElementById('color').onclick=changeColor;
            
                var move = getQueryParam('move');
                
                if (!move) {
                    return;
                }
                
                var size = getQueryParam('size'),
                    color = getQueryParam('color'),
            
                // 跟新元素
                    square = document.getElementById('square');
                    
                square.style.left = move + 'px';
                square.style.height = size + 'px';
                square.style.width = size + 'px';
                square.style.backgroundColor = '#' + color;
            
                // 跟新数据状态值
                document.getElementById('move').setAttribute('data-state',move);
                document.getElementById('size').setAttribute('data-state',size);
                document.getElementById('color').setAttribute('data-state',color);
            }
            
            function updateURL () {
                var move = document.getElementById('move').getAttribute('data-state'),
                    color = document.getElementById('color').getAttribute('data-state'),
                    size = document.getElementById('size').getAttribute('data-state'),
                    link = document.getElementById('link'),
                    path = location.protocol + '//' + location.hostname + location.pathname + '?move=' + move + '&size=' + size + '&color=' + color;
                    
                link.innerHTML = '<p><a href="' + path + '">static state link</a></p>';
            
            }
            
            function moveSquare() {
                var move = parseInt(document.getElementById('move').getAttribute('data-state'));
                
                move += 100;
                document.getElementById('square').style.left = move + 'px';
                document.getElementById('move').setAttribute('data-state', move);
                updateURL();
            }
            
            function resizeSquare() {
                var size = parseInt(document.getElementById('size').getAttribute('data-state'));
                size += 50;
                var square = document.getElementById('square');
                square.style.width = size + 'px';
                square.style.height = size + 'px';
                document.getElementById('size').setAttribute('data-state',size);
                updateURL();
                }
            
            function changeColor() {
                var color = document.getElementById('color').getAttribute('data-state'),
                    hexcolor;
                    
                if (color === '00f') {
                    hexcolor = 'ff0';
                } else {
                    hexcolor = '00f';
                }
                document.getElementById('square').style.backgroundColor = '#' + hexcolor;
                document.getElementById('color').setAttribute('data-state',hexcolor);
                updateURL();
            }
            
        </script>
    </head>
    <body>
        <button id="move" data-state="0">Move Square</button>
        <button id="size" data-state="100">Increase Square Size</button>
        <button id="color" data-state="#ff0">Change Color</button>
        <div id="link"></div>
        <div id="square">
            <p>This is the object</p>
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Remember me?</title>
        <style>
            #square
            {
                position: absolute;
                left: 0;
                top: 100px;
                width: 100px;
                height: 100px;
                border: 1px solid #333;
                background-color: #ff0;
            }
            
            div p
            {
                margin: 10px;
            }
            
        </style>
        <script>
        
            // 找到http://www.netlobo.com/url_query_string_javascript.html
            function getQueryParam(name) {
                    name = name.replace(/[\[]/,'\\\[').replace(/[\]]/,'\\\]');
                    var regexS = '[\\?&]' + name + '=([^&#]*)',
                        regex = new RegExp( regexS ),
                        results = regex.exec( window.location.href );
                        
                    if(results === null){
                        return null;
                    } else {
                        return results[1];
                    }
                    
            }
            
            window.onload=function() {
            
                // 设置按钮
                document.getElementById('move').onclick=moveSquare;
                document.getElementById('size').onclick=resizeSquare;
                document.getElementById('color').onclick=changeColor;
            
                var move = getQueryParam('move');
                
                if (!move) {
                    return;
                }
                
                var size = getQueryParam('size'),
                    color = getQueryParam('color'),
            
                // 跟新元素
                    square = document.getElementById('square');
                    
                square.style.left = move + 'px';
                square.style.height = size + 'px';
                square.style.width = size + 'px';
                square.style.backgroundColor = '#' + color;
            
                // 跟新数据状态值
                document.getElementById('move').setAttribute('data-state',move);
                document.getElementById('size').setAttribute('data-state',size);
                document.getElementById('color').setAttribute('data-state',color);
            }
            
            function updateURL () {
                var move = document.getElementById('move').getAttribute('data-state'),
                    color = document.getElementById('color').getAttribute('data-state'),
                    size = document.getElementById('size').getAttribute('data-state'),
                    link = document.getElementById('link'),
                    path = location.protocol + '//' + location.hostname + location.pathname + '?move=' + move + '&size=' + size + '&color=' + color;
                    
                link.innerHTML = '<p><a href="' + path + '">static state link</a></p>';
            
            }
            
            function moveSquare() {
                var move = parseInt(document.getElementById('move').getAttribute('data-state'));
                
                move += 100;
                document.getElementById('square').style.left = move + 'px';
                document.getElementById('move').setAttribute('data-state', move);
                updateURL();
            }
            
            function resizeSquare() {
                var size = parseInt(document.getElementById('size').getAttribute('data-state'));
                size += 50;
                var square = document.getElementById('square');
                square.style.width = size + 'px';
                square.style.height = size + 'px';
                document.getElementById('size').setAttribute('data-state',size);
                updateURL();
                }
            
            function changeColor() {
                var color = document.getElementById('color').getAttribute('data-state'),
                    hexcolor;
                    
                if (color === '00f') {
                    hexcolor = 'ff0';
                } else {
                    hexcolor = '00f';
                }
                document.getElementById('square').style.backgroundColor = '#' + hexcolor;
                document.getElementById('color').setAttribute('data-state',hexcolor);
                updateURL();
            }
            
        </script>
    </head>
    <body>
        <button id="move" data-state="0">Move Square</button>
        <button id="size" data-state="100">Increase Square Size</button>
        <button id="color" data-state="#ff0">Change Color</button>
        <div id="link"></div>
        <div id="square">
            <p>This is the object</p>
        </div>
    </body>
</html>
``` 
