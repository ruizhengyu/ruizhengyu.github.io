---
date: 2016-05-04 20:36:30+00:00
layout: post
title: JavaScript经典实例 示例20-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
使用新的history.pushState和window.onpopstate事件处理程序，转换后的8.8节[示例8-2](http://lovechina.xyz/JavaScript%E7%BB%8F%E5%85%B8%E5%AE%9E%E4%BE%8BExample8-2/)
----------------

<html>
    <head>
        <title>Remember me--new, and improved!</title>
        <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
        <script>
            window.onload = function() {
                document.getElementById('next').onclick = nextPanel;
            }
            
            window.onpopstate = function(event) {
                
                // 检查event.state，如果找到了，重新载入
                if (!event.state) {
                    return;
                }
                
                var page = event.state.page;
                
                switch (page) {
                    case 'one' :
                    functionOne();
                    break;
                    case 'two' :
                    functionOne();
                    functionTwo();
                    break;
                    case 'three' :
                    functionOne();
                    functionTwo();
                    functionThree();
                }
                
            }
            
            // 按照按钮的类，显示下一个面板
            function nextPanel() {
                var page = document.getElementById('next').getAttribute('data-page');
                
                switch(page) {
                    case 'zero' :
                        functionOne();
                        break;
                    case 'one' :
                        functionTwo();
                        break;
                    case 'two' :
                        functionThree();
                }
                
            }
            // 设置两个按钮的类，并且，创建状态链接，添加到页面
            function setPage(page) {
                document.getElementById('next').setAttribute('data-page',page);
                window.history.pushState({ page : page}, 'Page ' + page, '?page=' + page);
            }
            
            // 函数one、two、three，修改div，设置按钮和链接
            function functionOne() {
                var square = document.getElementById('square');
                
                square.style.position = 'relative';
                square.style.left = '0';
                square.style.backgroundColor = '#f00';
                square.style.width = '200px';
                square.style.height = '200px';
                square.style.padding = '10px';
                square.style.margin = '20px';
                setPage('one');
            }
            
            function functionTwo() {
                var square = document.getElementById('square');
                
                square.style.backgroundColor = '#ff0';
                square.style.position = 'absolute';
                square.style.left = '200px';
                setPage('two');
            }
            
            function functionThree() {
                var square = document.getElementById('square');
                
                square.style.width = '400px';
                square.style.height = '400px';
                square.style.backgroundColor = '#0f0';
                square.style.left = '400px';
                setPage('three');
            }
        </script>
    </head>
    <body>
        <button id="next" data-page="zero">Next Action</button>
        <div id="square" class="zero">
            <p>This is the object</p>
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Remember me--new, and improved!</title>
        <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
        <script>
            window.onload = function() {
                document.getElementById('next').onclick = nextPanel;
            }
            
            window.onpopstate = function(event) {
                
                // 检查event.state，如果找到了，重新载入
                if (!event.state) {
                    return;
                }
                
                var page = event.state.page;
                
                switch (page) {
                    case 'one' :
                    functionOne();
                    break;
                    case 'two' :
                    functionOne();
                    functionTwo();
                    break;
                    case 'three' :
                    functionOne();
                    functionTwo();
                    functionThree();
                }
                
            }
            
            // 按照按钮的类，显示下一个面板
            function nextPanel() {
                var page = document.getElementById('next').getAttribute('data-page');
                
                switch(page) {
                    case 'zero' :
                        functionOne();
                        break;
                    case 'one' :
                        functionTwo();
                        break;
                    case 'two' :
                        functionThree();
                }
                
            }
            // 设置两个按钮的类，并且，创建状态链接，添加到页面
            function setPage(page) {
                document.getElementById('next').setAttribute('data-page',page);
                window.history.pushState({ page : page}, 'Page ' + page, '?page=' + page);
            }
            
            // 函数one、two、three，修改div，设置按钮和链接
            function functionOne() {
                var square = document.getElementById('square');
                
                square.style.position = 'relative';
                square.style.left = '0';
                square.style.backgroundColor = '#f00';
                square.style.width = '200px';
                square.style.height = '200px';
                square.style.padding = '10px';
                square.style.margin = '20px';
                setPage('one');
            }
            
            function functionTwo() {
                var square = document.getElementById('square');
                
                square.style.backgroundColor = '#ff0';
                square.style.position = 'absolute';
                square.style.left = '200px';
                setPage('two');
            }
            
            function functionThree() {
                var square = document.getElementById('square');
                
                square.style.width = '400px';
                square.style.height = '400px';
                square.style.backgroundColor = '#0f0';
                square.style.left = '400px';
                setPage('three');
            }
        </script>
    </head>
    <body>
        <button id="next" data-page="zero">Next Action</button>
        <div id="square" class="zero">
            <p>This is the object</p>
        </div>
    </body>
</html>
``` 
