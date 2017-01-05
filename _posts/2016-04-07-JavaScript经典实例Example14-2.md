---
date: 2016-04-07 15:46:30+00:00
layout: post
title: JavaScript经典实例 示例14-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

让覆盖/照片显示页面成为键盘可访问的
----------------

<html>
    <head>
        <title>Overlay</title>
        <meta charset="utf-8" />
        <style type="text/css">
            img
            {
                padding: 5px;
                border-style: none;
            }
            
            .overlay
            {
                background-color: #000;
                opacity: .7;
                filter: alpha(opacity = 70);
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
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
            
            // 当点击链接/图像的时候，展开照片
            function imgClick() {
                var img = this.firstChild;
                
                expandPhoto(img.getAttribute('data-larger'));
                return false;
            }
            
            // 如果覆盖是打开的，并且按下ESC，关闭覆盖
            // 考虑到页面中的键盘事件
            function imgKeyDown(evnt) {
                evnt = (evnt) ? evnt : ((window.event) ? window.event : '');
                var keycode = (evnt.which) ? evnt.which : evnt.keyCode;
                
                if (document.getElementById('overlay')) {
                    if (keycode === 27) {
                        restore();
                    }
                    
                    return false;
                } else {
                    if (keycode === 13) {
                        var img = this.firstChild,
                            src = img.getAttribute('data-larger');
                        expandPhoto(src);
                        return false;
                    }
                    
                }
                
                return true;
            }
            
            // 创建覆盖，展开图片
            function expandPhoto(src) {
                
                // 创建覆盖元素
                var overlay = document.createElement('div'),
                
                // 添加图像
                    img = document.createElement('img');
                
                overlay.setAttribute('id', 'overlay');
                overlay.setAttribute('class', 'overlay');
                
                // IE7
                // overlay.id = 'overlay';
                // overlay.className = 'overlay';
                
                document.body.appendChild(overlay);
                img.src = src;
                img.setAttribute('id', 'img');
                
                // 设置tabindex以获取焦点
                img.setAttribute('tabindex', '-1');
                
                // 样式化图像
                img.setAttribute('class', 'overlayimg');
                
                // IE7
                // img.class = 'overlayimg';
                
                img.onclick = restore;
                img.onkeydown = imgKeyDown;
                document.body.appendChild(img);
                
                // 覆盖到覆盖中的图像
                img.focus();
            }
            
            // 将页面回复正常
            function restore() {
                document.body.removeChild(document.getElementById('overlay'));
                document.body.removeChild(document.getElementById('img'));
            }
            
            window.onload = function() {
                var aimgs = document.getElementsByTagName('a');
                
                aimgs[0].focus();
                for (var i = 0; i < aimgs.length; i++) {
                    aimgs[i].onclick = imgClick;
                }
                
            }
           
        </script>
    </head>
    <body>
        <div id="outer">
            <p>Mouse click on image, or use kryboard to move to photo and hit ENTER to expand the photo. To close expanded photo, hit ESC or mouse click on image.</p>
            <a href="http://lovechina.xyz/assets/media/image/dragonfly2.jpg"><img src="http://lovechina.xyz/assets/media/image/dragonfly2.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly2.jpg" alt="女神全智贤"/></a>
            <a href="http://lovechina.xyz/assets/media/image/dragonfly4.jpg"><img src="http://lovechina.xyz/assets/media/image/dragonfly4.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly4.jpg" alt="女神全智贤"/></a>
            <a href="http://lovechina.xyz/assets/media/image/dragonfly6.jpg"><img src="http://lovechina.xyz/assets/media/image/dragonfly6.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly6.jpg" alt="女神全智贤"/></a>
            <a href="http://lovechina.xyz/assets/media/image/dragonfly8.jpg"><img src="http://lovechina.xyz/assets/media/image/dragonfly8.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly8.jpg" alt="来自星星的你"/></a>
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
                border-style: none;
            }
            
            .overlay
            {
                background-color: #000;
                opacity: .7;
                filter: alpha(opacity = 70);
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
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
            
            // 当点击链接/图像的时候，展开照片
            function imgClick() {
                var img = this.firstChild;
                
                expandPhoto(img.getAttribute('data-larger'));
                return false;
            }
            
            // 如果覆盖是打开的，并且按下ESC，关闭覆盖
            // 考虑到页面中的键盘事件
            function imgKeyDown(evnt) {
                evnt = (evnt) ? evnt : ((window.event) ? window.event : '');
                var keycode = (evnt.which) ? evnt.which : evnt.keyCode;
                
                if (document.getElementById('overlay')) {
                    if (keycode === 27) {
                        restore();
                    }
                    
                    return false;
                } else {
                    if (keycode === 13) {
                        var img = this.firstChild,
                            src = img.getAttribute('data-larger');
                        expandPhoto(src);
                        return false;
                    }
                    
                }
                
                return true;
            }
            
            // 创建覆盖，展开图片
            function expandPhoto(src) {
                
                // 创建覆盖元素
                var overlay = document.createElement('div'),
                
                // 添加图像
                    img = document.createElement('img');
                
                overlay.setAttribute('id', 'overlay');
                overlay.setAttribute('class', 'overlay');
                
                // IE7
                // overlay.id = 'overlay';
                // overlay.className = 'overlay';
                
                document.body.appendChild(overlay);
                img.src = src;
                img.setAttribute('id', 'img');
                
                // 设置tabindex以获取焦点
                img.setAttribute('tabindex', '-1');
                
                // 样式化图像
                img.setAttribute('class', 'overlayimg');
                
                // IE7
                // img.class = 'overlayimg';
                
                img.onclick = restore;
                img.onkeydown = imgKeyDown;
                document.body.appendChild(img);
                
                // 覆盖到覆盖中的图像
                img.focus();
            }
            
            // 将页面回复正常
            function restore() {
                document.body.removeChild(document.getElementById('overlay'));
                document.body.removeChild(document.getElementById('img'));
            }
            
            window.onload = function() {
                var aimgs = document.getElementsByTagName('a');
                
                aimgs[0].focus();
                for (var i = 0; i < aimgs.length; i++) {
                    aimgs[i].onclick = imgClick;
                }
                
            }
           
        </script>
    </head>
    <body>
        <div id="outer">
            <p>Mouse click on image, or use kryboard to move to photo and hit ENTER to expand the photo. To close expanded photo, hit ESC or mouse click on image.</p>
            <a href="http://lovechina.xyz/assets/media/image/dragonfly2.jpg"><img src="http://lovechina.xyz/assets/media/image/dragonfly2.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly2.jpg" alt="image of common dragonfly on bright green and pink flowers"/></a>
            <a href="http://lovechina.xyz/assets/media/image/dragonfly4.jpg"><img src="http://lovechina.xyz/assets/media/image/dragonfly4.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly4.jpg" alt="Drak orange dragonfly on water lily"/></a>
            <a href="http://lovechina.xyz/assets/media/image/dragonfly6.jpg"><img src="http://lovechina.xyz/assets/media/image/dragonfly6.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly6.jpg" alt="Drak orange dragonfly on purple water lily"/></a>
            <a href="http://lovechina.xyz/assets/media/image/dragonfly8.jpg"><img src="http://lovechina.xyz/assets/media/image/dragonfly8.thumbnail.jpg" data-larger="http://lovechina.xyz/assets/media/image/dragonfly8.jpg" alt="Dragonfly on bright pink water lily"/></a>
        </div>
    </body>
</html>
``` 
