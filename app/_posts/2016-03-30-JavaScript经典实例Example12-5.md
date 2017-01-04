---
date: 2016-03-30 10:46:30+00:00
layout: post
title: JavaScript经典实例 示例12-5
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

从页面删除段落元素
----------------

<html>
    <head>
        <title>removeChild</title>
        <style type="text/css">
            p
            {
                padding: 20px;
                margin: 10px 0;
                width: 400px;
                background-color: #eef;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                var paras = document.getElementsByTagName('p');
                
                for (var i = 0; i < paras.length; i++) {
                    paras[i].onclick = pruneparagraph;
                }
                
            }
            
            function pruneparagraph() {
                var parent = this.parentNode;
                
                parent.removeChild(this);
                alert('paras ' + document.getElementsByTagName('p').length);
            }
            
        </script>
    </head>
    <body>
        <p>This is paragraph one</p>
        <p>This is paragraph two</p>
        <p>This is paragraph three</p>
        <p>This is paragraph four</p>
        <p>This is paragraph five</p>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>removeChild</title>
        <style type="text/css">
            p
            {
                padding: 20px;
                margin: 10px 0;
                width: 400px;
                background-color: #eef;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                var paras = document.getElementsByTagName('p');
                
                for (var i = 0; i < paras.length; i++) {
                    paras[i].onclick = pruneparagraph;
                }
                
            }
            
            function pruneparagraph() {
                var parent = this.parentNode;
                
                parent.removeChild(this);
                alert('paras ' + document.getElementsByTagName('p').length);
            }
            
        </script>
    </head>
    <body>
        <p>This is paragraph one</p>
        <p>This is paragraph two</p>
        <p>This is paragraph three</p>
        <p>This is paragraph four</p>
        <p>This is paragraph five</p>
    </body>
</html>
``` 
