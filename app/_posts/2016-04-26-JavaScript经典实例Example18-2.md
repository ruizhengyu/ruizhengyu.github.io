---
date: 2016-04-26 15:36:30+00:00
layout: post
title: JavaScript经典实例 示例18-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
发送器页面
----------------

<html>
    <head>
        <title>Sender</title>
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
                manageEvent(document.getElementById('button1'), 'click', sendMessage);
                manageEvent(window, 'message', receive);
            }
            
            // 确保把URL修改为你的位置
            function sendMessage() {
                try {
                    var farAwayWindow = document.getElementById('widgetId').contentWindow;
                    
                    farAwayWindow.postMessage('dragonfly6.thumbnail.jpg,Dragonfly on flower', 'http://jscb.burningbird.net');
                } catch(e) {
                    alert(e);
                }
                
            }
            
            // 把URL修改到你的位置
            function receive(e) {
                if (e.origin === 'http://jscb.burningbird.net') {
                    alert(e.data);
                }
                
            }
            
        </script>
    </head>
    <body>
        <div>
            <button id="button1">Load the photo</button>
        </div>
        <iframe src="http://lovechina.xyz/JavaScript%E7%BB%8F%E5%85%B8%E5%AE%9E%E4%BE%8BExample18-3/" id="widgetId"></iframe>
    </body>
</html>

[点击查看监听器页面](http://lovechina.xyz/JavaScript%E7%BB%8F%E5%85%B8%E5%AE%9E%E4%BE%8BExample18-3/){:target="_blank"} 

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Sender</title>
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
                manageEvent(document.getElementById('button1'), 'click', sendMessage);
                manageEvent(window, 'message', receive);
            }
            
            // 确保把URL修改为你的位置
            function sendMessage() {
                try {
                    var farAwayWindow = document.getElementById('widgetId').contentWindow;
                    
                    farAwayWindow.postMessage('dragonfly6.thumbnail.jpg,Dragonfly on flower', 'http://jscb.burningbird.net');
                } catch(e) {
                    alert(e);
                }
                
            }
            
            // 把URL修改到你的位置
            function receive(e) {
                if (e.origin === 'http://jscb.burningbird.net') {
                    alert(e.data);
                }
                
            }
            
        </script>
    </head>
    <body>
        <div>
            <button id="button1">Load the photo</button>
        </div>
        <iframe src="http://lovechina.xyz/JavaScript%E7%BB%8F%E5%85%B8%E5%AE%9E%E4%BE%8BExample18-3/" id="widgetId"></iframe>
    </body>
</html>
``` 
