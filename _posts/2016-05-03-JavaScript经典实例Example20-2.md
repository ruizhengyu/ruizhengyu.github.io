---
date: 2016-05-03 20:26:30+00:00
layout: post
title: JavaScript经典实例 示例20-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
展示cookie
----------------

<html dir="ltr" lang="en-US">
    <head>
        <title>Persisting via Cookies</title>
        <style>
            div
            {
                margin: 5px;
            }
            
        </style>
        <script>
            
            // 如果cookie可用
            window.onload = function() {
                if (navigator.cookieEnabled) {
                    document.getElementById('set').onclick = setCookie;
                    document.getElementById('get').onclick = readCookie;
                    document.getElementById('erase').onclick = eraseCookie;
                }
            
            }
            
            
            // 将cookie过期日期设置为2010年
            function setCookie() {
                
                var cookie = document.getElementById('cookie').value,
                    value = document.getElementById('value').value,
                    futureDate = new Date();
                    
                futureDate.setDate(futureDate.getDate() + 10);
                
                var tmp = cookie + '=' + encodeURI(value) + '; expires=' + futureDate.toGMTString() + '; path=/';
                
                document.cookie = tmp;
                alert(tmp);
            }
            
            // 每个cookie用分号隔开
            function readCookie() {
                
                var key = document.getElementById('cookie').value,
                    cookie = document.cookie,
                    first = cookie.indexOf(key + '=');
                
                // cookie存在
                if (first >= 0) {
                    var str = cookie.substring(first,cookie.length),
                        last = str.indexOf(';');
                
                    // 如果是cookie的末尾
                    if (last < 0) {
                        last = str.length;
                    }
                    
                    // 获取cookie值
                    str = str.substring(0,last).split('=');
                    alert(decodeURI(str[1]));
                } else {
                    alert('none found');
                }
                
            }
            
            // 将cookie日期设置为过去以擦除它
            function eraseCookie() {
            
                var key = document.getElementById('cookie').value,
                    cookieDate = new Date();
                    
                cookieDate.setDate(cookieDate.getDate() - 10);
                document.cookie = key + '= ; expires=' + cookieDate.toGMTString() + '; path=/';
            }
        </script>
    </head>
    <body>
        <form>
            <label for="cookie"> Enter cookie:</label> <input type="text" id="cookie" /> <br />
            <label for="value">Cookie Value:</label> <input type="text" id="value" /><br />
        </form>
        <div>
            <button id="set">Set Cookie</button>
            <button id="get">Get Cookie</button>
            <button id="erase">Erase Cookie</button>
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html dir="ltr" lang="en-US">
    <head>
        <title>Persisting via Cookies</title>
        <style>
            div
            {
                margin: 5px;
            }
            
        </style>
        <script>
            
            // 如果cookie可用
            window.onload = function() {
                if (navigator.cookieEnabled) {
                    document.getElementById('set').onclick = setCookie;
                    document.getElementById('get').onclick = readCookie;
                    document.getElementById('erase').onclick = eraseCookie;
                }
            
            }
            
            
            // 将cookie过期日期设置为2010年
            function setCookie() {
                
                var cookie = document.getElementById('cookie').value,
                    value = document.getElementById('value').value,
                    futureDate = new Date();
                    
                futureDate.setDate(futureDate.getDate() + 10);
                
                var tmp = cookie + '=' + encodeURI(value) + '; expires=' + futureDate.toGMTString() + '; path=/';
                
                document.cookie = tmp;
                alert(tmp);
            }
            
            // 每个cookie用分号隔开
            function readCookie() {
                
                var key = document.getElementById('cookie').value,
                    cookie = document.cookie,
                    first = cookie.indexOf(key + '=');
                
                // cookie存在
                if (first >= 0) {
                    var str = cookie.substring(first,cookie.length),
                        last = str.indexOf(';');
                
                    // 如果是cookie的末尾
                    if (last < 0) {
                        last = str.length;
                    }
                    
                    // 获取cookie值
                    str = str.substring(0,last).split('=');
                    alert(decodeURI(str[1]));
                } else {
                    alert('none found');
                }
                
            }
            
            // 将cookie日期设置为过去以擦除它
            function eraseCookie() {
            
                var key = document.getElementById('cookie').value,
                    cookieDate = new Date();
                    
                cookieDate.setDate(cookieDate.getDate() - 10);
                document.cookie = key + '= ; expires=' + cookieDate.toGMTString() + '; path=/';
            }
        </script>
    </head>
    <body>
        <form>
            <label for="cookie"> Enter cookie:</label> <input type="text" id="cookie" /> <br />
            <label for="value">Cookie Value:</label> <input type="text" id="value" /><br />
        </form>
        <div>
            <button id="set">Set Cookie</button>
            <button id="get">Get Cookie</button>
            <button id="erase">Erase Cookie</button>
        </div>
    </body>
</html>
``` 
