---
date: 2016-04-04 13:06:30+00:00
layout: post
title: JavaScript经典实例 示例13-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

创建一个覆盖以显示较大的图片
----------------

<html>
    <head>
        <title>Overlay</title>
        <meta charset="utf-8" />
        <style type="text/css">
            img
            {
                padding: 5px;
            }
            
            #outer
            {
                width: 100%;
                height: 100%;
            }
            
            .overlay
            {
                background-color: #000;
                opacity: .7;
                filter: alpha(opacity = 70);
                position: fixed;
                top: 0;
                left: 0;
                z-index: 10;
            }
            
            .overlayimg
            {
                position: absolute;
                z-index: 11;
                left: 50px;
                top: 50px;
            }
            
        </style>
        <script type="text/javascript">
            function expandPhoto() {
                
                // 创建覆盖并将其附加到页面
                var overlay = document.createElement('div'),
                
                // 创建图像并将其附加到页面
                    img = document.createElement('img');
                
                overlay.setAttribute('id', 'overlay');
                overlay.setAttribute('class', 'overlay');
                document.body.appendChild(overlay);
                img.setAttribute('id', 'img');
                img.src = this.getAttribute('data-larger');
                img.setAttribute('class', 'overlayimg');
                
                // click to restore page
                img.onclick = restore;
                document.body.appendChild(img);
            }
            
            // 将页面回复正常
            function restore() {
                document.body.removeChild(document.getElementById('overlay'));
                document.body.removeChild(document.getElementById('img'));
            }
            
            window.onload = function() {
                var imgs = document.getElementsByTagName('img');
                
                imgs[0].focus();
                for (var i = 0; i < imgs.length; i++) {
                    imgs[i].onclick = expandPhoto;
                    imgs[i].onkeydown = expandPhoto;
                }
                
            }
           
        </script>
    </head>
    <body>
        <div id="outer">
            <p>Mouse click on image to expand the photo. To close expanded photo, mouse click on image.</p>
            <img src="http://lovechina.xyz/assets/media/image/dragonfly2.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly2.jpg" alt="image of common dragonfly on bright green and pink flowers"/>
            <img src="http://lovechina.xyz/assets/media/image/dragonfly4.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly4.jpg" alt="Drak orange dragonfly on water lily"/>
            <img src="http://lovechina.xyz/assets/media/image/dragonfly6.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly6.jpg" alt="Drak orange dragonfly on purple water lily"/>
            <img src="http://lovechina.xyz/assets/media/image/dragonfly8.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly8.jpg" alt="Dragonfly on bright pink water lily"/>
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Overlay</title>
        <meta charset="utf-8" />
        <style type="text/css">
            img
            {
                padding: 5px;
            }
            
            #outer
            {
                width: 100%;
                height: 100%;
            }
            
            .overlay
            {
                background-color: #000;
                opacity: .7;
                filter: alpha(opacity = 70);
                position: fixed;
                top: 0;
                left: 0;
                z-index: 10;
            }
            
            .overlayimg
            {
                position: absolute;
                z-index: 11;
                left: 50px;
                top: 50px;
            }
            
        </style>
        <script type="text/javascript">
            function expandPhoto() {
                
                // 创建覆盖并将其附加到页面
                var overlay = document.createElement('div'),
                
                // 创建图像并将其附加到页面
                    img = document.createElement('img');
                
                overlay.setAttribute('id', 'overlay');
                overlay.setAttribute('class', 'overlay');
                document.body.appendChild(overlay);
                img.setAttribute('id', 'img');
                img.src = this.getAttribute('data-larger');
                img.setAttribute('class', 'overlayimg');
                
                // click to restore page
                img.onclick = restore;
                document.body.appendChild(img);
            }
            
            // 将页面回复正常
            function restore() {
                document.body.removeChild(document.getElementById('overlay'));
                document.body.removeChild(document.getElementById('img'));
            }
            
            window.onload = function() {
                var imgs = document.getElementsByTagName('img');
                
                imgs[0].focus();
                for (var i = 0; i < imgs.length; i++) {
                    imgs[i].onclick = expandPhoto;
                    imgs[i].onkeydown = expandPhoto;
                }
                
            }
           
        </script>
    </head>
    <body>
        <div id="outer">
            <p>Mouse click on image to expand the photo. To close expanded photo, mouse click on image.</p>
            <img src="dragonfly2.thumbnail.jpg" data-larger="dragonfly2.jpg" alt="image of common dragonfly on bright green and pink flowers"/>
            <img src="dragonfly4.thumbnail.jpg" data-larger="dragonfly4.jpg" alt="Drak orange dragonfly on water lily"/>
            <img src="dragonfly6.thumbnail.jpg" data-larger="dragonfly6.jpg" alt="Drak orange dragonfly on purple water lily"/>
            <img src="dragonfly8.thumbnail.jpg" data-larger="dragonfly8.jpg" alt="Dragonfly on bright pink water lily"/>
        </div>
    </body>
</html>
``` 
