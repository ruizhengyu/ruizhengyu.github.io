---
date: 2016-03-26 14:26:30+00:00
layout: post
title: JavaScript经典实例 示例12-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

向Web页面插入一个div元素
----------------

<html>
    <head>
        <title>object detection</title>
        <style type="text/css">
            div
            {
                width: 300px;
                heigth: 20px;
                padding: 10px;
                margin: 10px 0;
            }
            
            #div1
            {
                background-color: #ff0;
            }
            
            .divclass
            {
                background-color: #cfc;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                document.getElementById('div1').onclick =addDiv;
            }
            var i = 1;
            function addDiv() {
                
                //获取父节点
                var parent = this.parentNode,
                
                //创建新的div
                    newDiv = document.createElement('div');
                
                newDiv.className = 'divclass';
                newDiv.innerHTML = "<p>I'm here, I'm in the page" + i + "</p>";
                i++;
                //添加到页面
                parent.insertBefore(newDiv, this);
            }
                        
        </script>
    </head>
    <body>
        <div id="parent">
            <div id="div1" onclick="addDiv()">
                <p>Click me to add new element</p>
            </div>
        </div>
    </body>
</html>


源码如下：

``` html
<!DOCTYPE html>
    <html>
    <head>
        <title>object detection</title>
        <style type="text/css">
            div
            {
                width: 300px;
                heigth: 20px;
                padding: 10px;
                margin: 10px 0;
            }
            
            #div1
            {
                background-color: #ff0;
            }
            
            .divclass
            {
                background-color: #cfc;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                document.getElementById('div1').onclick = addDiv();
            }
            
            function addDiv() {
                
                //获取父节点
                var parent = document.getElementById('parent'),
                
                //创建新的div
                    newDiv = document.createElement('div');
                
                newDiv.className = 'divclass';
                newDiv.innerHTML = "<p>I'm here, I'm in the page</p>";
                
                //添加到页面
                parent.insertBefore(newDiv, document.getElementById('div1'));
            }
                        
        </script>
    </head>
    <body>
        <div id="parent">
            <div id="div1">
                <p>Click me to add new element</p>
            </div>
        </div>
    </body>
</html>
```

`insertBefore()` 方法在您指定的已有子节点之前插入新的子节点。
提示：如果您希望创建包含文本的新列表项，请记得创建文本节点形式的文本，以便追加到 `LI` 元素中，然后向列表插入这个 `LI`。
您也可以使用 `insertBefore` 方法插入/移动已有元素。

`node.insertBefore(newnode,existingnode)`   `newnode`	`Node` 对象	必需。需要插入的节点对象。
`existingnode`	`Node` `object`	可选。在其之前插入新节点的子节点。如果未规定，则 `insertBefore` 方法会在结尾插入 `newnode`。
