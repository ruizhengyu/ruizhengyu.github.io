---
date: 2016-04-24 15:06:30+00:00
layout: post
title: JavaScript经典实例 示例17-4
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
使用新的插件的Web页面和应用程序
----------------

<html>
    <head>
        <style>
            #test
            {
                background-color: #00f;
                width: 500px;
                padding: 10px;
                color: #fff;
                font-weight: bold;
                font-size: larger;               
            }
            
        </style>
        <script type="text/javascript" src="/assets/media/image/jquery-2.2.4.js"></script>
        <script type="text/javascript" src="/assets/media/image/basic.js"></script>
        <script type="text/javascript">
            $(document).ready(function(){
                $('#test').click(function(){
                    $(this).flashBlueRed().increaseWidth();
                });
            });
        </script>
    </head>
    <body>
        <div id="test">
            hi, click me to change color
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <style>
            #test
            {
                background-color: #00f;
                width: 500px;
                padding: 10px;
                color: #fff;
                font-weight: bold;
                font-size: larger;               
            }
            
        </style>
        <script type="text/javascript" src="jquery-2.2.4.js"></script>
        <script type="text/javascript" src="basic.js"></script>
        <script type="text/javascript">
            $(document).ready(function(){
                $('#test').click(function(){
                    $(this).flashBlueRed().increaseWidth();
                });
            });
        </script>
    </head>
    <body>
        <div id="test">
            hi, click me to change color
        </div>
    </body>
</html>
``` 
