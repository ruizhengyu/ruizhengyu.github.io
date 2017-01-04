---
date: 2016-04-16 14:46:30+00:00
layout: post
title: JavaScript经典实例 示例15-8
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

为HTML 5 video 元素提供一个定制的控制
----------------

<html>
    <head>
        <title>Meadow Video</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
            function manageEvent(eventObj, event, eventHandler) {
                if (eventObj.addEventListener) {
                    eventObj.addEventListener(event, eventHandler, false);
                } else if (eventObj.attachEvent) {
                    event = 'on' + event;
                    eventObj.attachEvent(event, eventHandler);
                }
                
            }
            
            window.onload = function() {
                
                // 用于按钮的事件
                manageEvent(document.getElementById('start'), 'click', startPlayback);
                manageEvent(document.getElementById('stop'), 'click', stopPlayback);
                manageEvent(document.getElementById('pause'), 'click', pausePlayback);
                
                // 设置视频以便播放
                var meadow = document.getElementById('meadow');
                
                manageEvent(meadow, 'timeupdate', reportProgress);
                
                // 视频备用
                var detect = document.createElement('video');
                
                if (!detect.canPlayType) {
                    document.getElementById('controls').style.display = 'none';
                }
                
            }
            
            // 开始视频，允许停止和暂停
            // 关闭视频
            function startPlayback() {
                var meadow = document.getElementById('meadow');
                
                meadow.play();
                document.getElementById('pause').disabled = false;
                document.getElementById('stop').disabled = false;
                this.disabled = true;
            }
            
            // 暂停视频，打开启动，关闭停止
            // 关闭暂停
            function pausePlayback() {
                document.getElementById('meadow').pause();
                this.disabled = true;
                document.getElementById('start').disabled = false;
                document.getElementById('stop').disabled = false;                                
            }
            
            // 停止视频，返回到0时间
            // 打开播放，关闭暂停和停止
            function stopPlayback() {
                var meadow = document.getElementById('meadow');
                
                meadow.pause();
                meadow.currentTime = 0;
                document.getElementById('start').disabled = false;
                document.getElementById('pause').disabled = false;
                this.disabled = true;
            }
            
            // 对于能过被5除的每个时间点，输出反馈
            function reportProgress() {
                var time = Math.round(this.currentTime),
                    div = document.getElementById('feedback');
                
                div.innerHTML = time + ' seconds';
            }
        </script>
    </head>
    <body>
        <video id="meadow" poster="http://lovechina.xyz/assets/media/image/purles.jpg" >
            <source src="http://lovechina.xyz/assets/media/image/meadow.MP4" type="video/MP4" />               
        </video>
        <div id="feedback"></div>
        <div id="controls">
            <button id="start">Play</button>
            <button id="stop">Stop</button>
            <button id="pause">Pause</button>
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Meadow Video</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
            function manageEvent(eventObj, event, eventHandler) {
                if (eventObj.addEventListener) {
                    eventObj.addEventListener(event, eventHandler, false);
                } else if (eventObj.attachEvent) {
                    event = 'on' + event;
                    eventObj.attachEvent(event, eventHandler);
                }
                
            }
            
            window.onload = function() {
                
                // 用于按钮的事件
                manageEvent(document.getElementById('start'), 'click', startPlayback);
                manageEvent(document.getElementById('stop'), 'click', stopPlayback);
                manageEvent(document.getElementById('pause'), 'click', pausePlayback);
                
                // 设置视频以便播放
                var meadow = document.getElementById('meadow');
                
                manageEvent(meadow, 'timeupdate', reportProgress);
                
                // 视频备用
                var detect = document.createElement('video');
                
                if (!detect.canPlayType) {
                    document.getElementById('controls').style.display = 'none';
                }
                
            }
            
            // 开始视频，允许停止和暂停
            // 关闭视频
            function startPlayback() {
                var meadow = document.getElementById('meadow');
                
                meadow.play();
                document.getElementById('pause').disabled = false;
                document.getElementById('stop').disabled = false;
                this.disabled = true;
            }
            
            // 暂停视频，打开启动，关闭停止
            // 关闭暂停
            function pausePlayback() {
                document.getElementById('meadow').pause();
                this.disabled = true;
                document.getElementById('start').disabled = false;
                document.getElementById('stop').disabled = false;                                
            }
            
            // 停止视频，返回到0时间
            // 打开播放，关闭暂停和停止
            function stopPlayback() {
                var meadow = document.getElementById('meadow');
                
                meadow.pause();
                meadow.currentTime = 0;
                document.getElementById('start').disabled = false;
                document.getElementById('pause').disabled = false;
                this.disabled = true;
            }
            
            // 对于能过被5除的每个时间点，输出反馈
            function reportProgress() {
                var time = Math.round(this.currentTime),
                    div = document.getElementById('feedback');
                
                div.innerHTML = time + ' seconds';
            }
        </script>
    </head>
    <body>
        <video id="meadow" poster="http://lovechina.xyz/assets/media/image/purles.jpg" >
            <source src="http://lovechina.xyz/assets/media/image/meadow.MP4" type="video/MP4" />             
        </video>
        <div id="feedback"></div>
        <div id="controls">
            <button id="start">Play</button>
            <button id="stop">Stop</button>
            <button id="pause">Pause</button>
        </div>
    </body>
</html>
``` 
