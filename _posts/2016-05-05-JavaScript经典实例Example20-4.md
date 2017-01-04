---
date: 2016-05-05 14:56:30+00:00
layout: post
title: JavaScript经典实例 示例20-4
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
比较sessionStorage和cookie
----------------

<html dir="ltr" lang="en-US">
    <head>
        <title>Comparing Cookies and sessionStorage</title>
        <meta http-equiv="Content-Type" content="text/html;charset=utf-8" >
        <style>
            div
            {
                background-color: #ffff00;
                margin: 5px;
                width: 100px;
                padding: 1px;
            }
            
        </style>
        <script>
            window.onload = function() {
                document.getElementById('set').onclick = setData;
                document.getElementById('get').onclick = getData;
                document.getElementById('erase').onclick = removeData;
            }
            
            // 为session和cookie都设置数据
            function setData() {
                var key = document.getElementById('key').value,
                    value = document.getElementById('value').value,
            
                // 设置sessionStorage
                    current = sessionStorage.getItem(key);
                    
                if (current) {
                    current += value;
                } else {
                    current = value;
                }
                
                sessionStorage.setItem(key,current);
            
                // 设置cookie
                current = getCookie(key);
                if (current) {
                    current += value;
                } else {
                current = value;
                }
                setCookie(key,current);
            }
            
            function getData() {
                try {
                    var key = document.getElementById('key').value;
            
                    // sessionStorage
                    var value = sessionStorage.getItem(key);
                    if (!value) {
                        value = '';
                    }
                    
                    document.getElementById('sessionstr').innerHTML = '<p>' + value + '</p>';
            
                    // cookie
                    value = getCookie(key);
                    if (!value) {
                        value = '';
                    }
                    
                    document.getElementById('cookiestr').innerHTML = '<p>' + value + '</p>';
            
                } catch(e) {
                    alert(e);
                }
            }
            
            function removeData() {
                var key = document.getElementById('key').value;
            
                // sessionStorage
                sessionStorage.removeItem(key);
            
                // cookie
                eraseCookie(key);
            }
            // 设置session cookie
            function setCookie(cookie,value) {
                var tmp = cookie + '=' + encodeURI(value) + ';path=/';
                
                document.cookie = tmp;
            }
            
            // 每个cookie用分号隔开
            function getCookie(key) {
                var cookie = document.cookie,
                    first = cookie.indexOf(key+'=');
            
                // cookie存在
                if (first >= 0) {
                    var str = cookie.substring(first,cookie.length);
                    var last = str.indexOf(';');
                    
                    // 如果是cookie的末尾
                    if (last < 0) {
                        last = str.length;
                    }
                    
                    // 获取cookie值
                    str = str.substring(0,last).split('=');
                    return decodeURI(str[1]);
                } else {
                    return null;
                }
            }
            
            // 将cookie日期设置为过去以擦除它
            function eraseCookie (key) {
                var cookieDate = new Date();
                
                cookieDate.setDate(cookieDate.getDate() - 10);
                var tmp = key + '= ; expires=' + cookieDate.toGMTString() + '; path=/';
                
                document.cookie = tmp;
            }
        </script>
    </head>
    <body>
        <form>
            <label for="key"> Enter key:</label>
            <input type="text" id="key" /> <br /> <br />
            <label for="value">Enter value:</label>
            <input type="text" id="value" /><br /><br />
        </form>
        <button id="set">Set data</button>
        <button id="get">Get data</button>
        <button id="erase">Erase data</button>
        <div id="sessionstr"><p></p></div>
        <div id="cookiestr"><p></p></div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html dir="ltr" lang="en-US">
    <head>
        <title>Comparing Cookies and sessionStorage</title>
        <meta http-equiv="Content-Type" content="text/html;charset=utf-8" >
        <style>
            div
            {
                background-color: #ffff00;
                margin: 5px;
                width: 100px;
                padding: 1px;
            }
            
        </style>
        <script>
            window.onload = function() {
                document.getElementById('set').onclick = setData;
                document.getElementById('get').onclick = getData;
                document.getElementById('erase').onclick = removeData;
            }
            
            // 为session和cookie都设置数据
            function setData() {
                var key = document.getElementById('key').value,
                    value = document.getElementById('value').value,
            
                // 设置sessionStorage
                    current = sessionStorage.getItem(key);
                    
                if (current) {
                    current += value;
                } else {
                    current = value;
                }
                
                sessionStorage.setItem(key,current);
            
                // 设置cookie
                current = getCookie(key);
                if (current) {
                    current += value;
                } else {
                current = value;
                }
                setCookie(key,current);
            }
            
            function getData() {
                try {
                    var key = document.getElementById('key').value;
            
                    // sessionStorage
                    var value = sessionStorage.getItem(key);
                    if (!value) {
                        value = '';
                    }
                    
                    document.getElementById('sessionstr').innerHTML = '<p>' + value + '</p>';
            
                    // cookie
                    value = getCookie(key);
                    if (!value) {
                        value = '';
                    }
                    
                    document.getElementById('cookiestr').innerHTML = '<p>' + value + '</p>';
            
                } catch(e) {
                    alert(e);
                }
            }
            
            function removeData() {
                var key = document.getElementById('key').value;
            
                // sessionStorage
                sessionStorage.removeItem(key);
            
                // cookie
                eraseCookie(key);
            }
            // 设置session cookie
            function setCookie(cookie,value) {
                var tmp = cookie + '=' + encodeURI(value) + ';path=/';
                
                document.cookie = tmp;
            }
            
            // 每个cookie用分号隔开
            function getCookie(key) {
                var cookie = document.cookie,
                    first = cookie.indexOf(key+'=');
            
                // cookie存在
                if (first >= 0) {
                    var str = cookie.substring(first,cookie.length);
                    var last = str.indexOf(';');
                    
                    // 如果是cookie的末尾
                    if (last < 0) {
                        last = str.length;
                    }
                    
                    // 获取cookie值
                    str = str.substring(0,last).split('=');
                    return decodeURI(str[1]);
                } else {
                    return null;
                }
            }
            
            // 将cookie日期设置为过去以擦除它
            function eraseCookie (key) {
                var cookieDate = new Date();
                
                cookieDate.setDate(cookieDate.getDate() - 10);
                var tmp = key + '= ; expires=' + cookieDate.toGMTString() + '; path=/';
                
                document.cookie = tmp;
            }
        </script>
    </head>
    <body>
        <form>
            <label for="key"> Enter key:</label>
            <input type="text" id="key" /> <br /> <br />
            <label for="value">Enter value:</label>
            <input type="text" id="value" /><br /><br />
        </form>
        <button id="set">Set data</button>
        <button id="get">Get data</button>
        <button id="erase">Erase data</button>
        <div id="sessionstr"><p></p></div>
        <div id="cookiestr"><p></p></div>
    </body>
</html>
``` 
