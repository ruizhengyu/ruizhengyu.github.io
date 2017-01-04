---
date: 2016-04-27 15:46:30+00:00
layout: post
title: JavaScript经典实例 示例18-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
监听器页面
----------------

<html>
    <head>
        <title>Listener</title>
        <script type="text/javascript">
            function manageEvent(eventObj, event, eventHandler) {
                if (eventObj.addEventListerener) {
                    eventObj.addEventListerener(event, eventHandler, false);
                } else if (eventObj.attachEvent) {
                    event = 'on' + event;
                    eventObj.attachEvent(event, eventHandler);
                }
                
            }
            
            window.onload = function() {
                manageEvent(window, 'message', receive);
            }
            
            // 把URL修改到你的位置
            function receive(e) {
                var img = document.getElementById('image');
                
                img.src = e.data.split(',')[0];
                img.alt = e.data.split(',')[1];
                e.source.postMessage('Received ' + e.data, 'http://lovechina.xyz/JavaScript%E7%BB%8F%E5%85%B8%E5%AE%9E%E4%BE%8BExample18-2/');                
            }
            
        </script>
    </head>
    <body>
        <img src="/assets/media/image/quanzhixian.jpg" id="image" alt="来自星星的你剧照" />
    </body>
</html>

[点击查看发送器页面](http://lovechina.xyz/JavaScript%E7%BB%8F%E5%85%B8%E5%AE%9E%E4%BE%8BExample18-2/){:target="_blank"} 

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Listener</title>
        <script type="text/javascript">
            function manageEvent(eventObj, event, eventHandler) {
                if (eventObj.addEventListerener) {
                    eventObj.addEventListerener(event, eventHandler, false);
                } else if (eventObj.attachEvent) {
                    event = 'on' + event;
                    eventObj.attachEvent(event, eventHandler);
                }
                
            }
            
            window.onload = function() {
                manageEvent(window, 'message', receive);
            }
            
            // 把URL修改到你的位置
            function receive(e) {
                var img = document.getElementById('image');
                
                img.src = e.data.split(',')[0];
                img.alt = e.data.split(',')[1];
                e.source.postMessage('Received ' + e.data, 'http://lovechina.xyz/JavaScript%E7%BB%8F%E5%85%B8%E5%AE%9E%E4%BE%8BExample18-2/');                
            }
            
        </script>
    </head>
    <body>
        <img src="/assets/media/image/quanzhixian.jpg" id="image" alt="来自星星的你剧照" />
    </body>
</html>
``` 
