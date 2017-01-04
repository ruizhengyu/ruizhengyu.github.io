---
date: 2016-04-05 14:56:30+00:00
layout: post
title: JavaScript经典实例 示例13-4
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

创建一个可重用的、多个标签页的应用程序
----------------

<html>
    <head>
        <title>Tabbed Pages</title>
        <meta charset="utf-8" />
        <style type="text/css">
            .tabcontainer
            {
                padding: 5px;
                width: 500px;
                margin: 20px;
            }
            
            .tabnavigation ul
            {
                padding: 0;
                margin: 0;
                display: none;
            }
            
            .tabnavigation ul li
            {
                padding: 3px;
                display: inline;
                border: 1px solid #000;
                background-color: #fff;
            }
            
            .tabnavigation ul li:hover
            {
                cursor: pointer;
            }
            
            .tabpages
            {
                position: relative;
                z-index: 2;
                border: 1px solid #000;
                background-color: #fff;
            }
            
            .tabpage
            {
                margin: 0 10px;
            }
            
        </style>
        <script type="text/javascript">
        
            // 为每个容器显示导航
            // 来设置显示
            // 隐藏所有标签，但第一个变迁例外，突出显示第一个标签
            window.onload = function() {
            
                // 针对每个容器
                var containers = document.querySelectorAll('.tabcontainer');
                
                for (var j = 0; j < containers.length; j++) {
                    
                    // 显示并隐藏元素
                    var nav = containers[j].querySelector('.tabnavigation ul'),
                    
                    // 设置当前标签
                        navitem = containers[j].querySelector('.tabnavigation ul li'),
                        ident = navitem.id.split('_')[1],
                        pages = containers[j].querySelectorAll('.tabpage'),
                        tabs = containers[j].querySelectorAll('.tabnavigation ul li');
                    
                    nav.style.display = 'block';
                    navitem.parentNode.setAttribute('data-current', ident);
                    navitem.setAttribute('style', 'background-color: #f00');
                    for (var i = 0; i < pages.length; i++) {
                        pages[i].style.display = 'none';
                    }
                    
                    for (var i = 0; i < tabs.length; i++) {
                        tabs[i].onclick = displayPage;
                    }
                    
                }
                
            }
            
            // 点击标签
            function displayPage() {
                var current = this.parentNode.getAttribute('data-current'),
                    ident = this.id.split('_')[1];
                
                document.getElementById('tabnav_' + current).setAttribute('style', 'background-color: #fff');
                document.getElementById('tabpage_' + current).style.display = 'none';
                this.setAttribute('style', 'background-color: #f00');
                document.getElementById('tabpage_' + ident).style.display = 'block';
                this.parentNode.setAttribute('data-current', ident);
            }
            
        </script>
    </head>
    <body>
        <div class="tabcontainer">
            <div class="tabnavigation">
                <ul>
                    <li id="tabnav_1">Page One</li>
                    <li id="tabnav_2">Page Two</li>
                    <li id="tabnav_3">Page Three</li>
                </ul>
            </div>
            <div class="tabpages">
                <div class="tabpage" id="tabpage_1">
                    <p>page 1</p>
                </div>
                <div class="tabpage" id="tabpage_2">
                    <p>page 2</p>
                </div>
                <div class="tabpage" id="tabpage_3">
                    <p>page 3</p>
                </div>
            </div>
        </div>
        <div class="tabcontainer">
            <div class="tabnavigation">
                <ul>
                    <li id="tabnav_4">Page Two One</li>
                    <li id="tabnav_5">Page Two Two</li>
                </ul>
            </div>
            <div class="tabpages">
                <div class="tabpage" id="tabpage_4">
                    <p>page 4</p>
                </div>
                <div class="tabpage" id="tabpage_5">
                    <p>page 5</p>
                </div>
                <div class="tabpage" id="tabpage_6">
                    <p>page 6</p>
                </div>
            </div>
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Tabbed Pages</title>
        <meta charset="utf-8" />
        <style type="text/css">
            .tabcontainer
            {
                padding: 5px;
                width: 500px;
                margin: 20px;
            }
            
            .tabnavigation ul
            {
                padding: 0;
                margin: 0;
                display: none;
            }
            
            .tabnavigation ul li
            {
                padding: 3px;
                display: inline;
                border: 1px solid #000;
                background-color: #fff;
            }
            
            .tabnavigation ul li:hover
            {
                cursor: pointer;
            }
            
            .tabpages
            {
                position: relative;
                z-index: 2;
                border: 1px solid #000;
                background-color: #fff;
            }
            
            .tabpage
            {
                margin: 0 10px;
            }
            
        </style>
        <script type="text/javascript">
        
            // 为每个容器显示导航
            // 来设置显示
            // 隐藏所有标签，但第一个变迁例外，突出显示第一个标签
            window.onload = function() {
            
                // 针对每个容器
                var containers = document.querySelectorAll('.tabcontainer');
                
                for (var j = 0; j < containers.length; j++) {
                    
                    // 显示并隐藏元素
                    var nav = containers[j].querySelector('.tabnavigation ul'),
                    
                    // 设置当前标签
                        navitem = containers[j].querySelector('.tabnavigation ul li'),
                        ident = navitem.id.split('_')[1],
                        pages = containers[j].querySelectorAll('.tabpage'),
                        tabs = containers[j].querySelectorAll('.tabnavigation ul li');
                    
                    nav.style.display = 'block';
                    navitem.parentNode.setAttribute('data-current', ident);
                    navitem.setAttribute('style', 'background-color: #f00');
                    for (var i = 0; i < pages.length; i++) {
                        pages[i].style.display = 'none';
                    }
                    
                    for (var i = 0; i < tabs.length; i++) {
                        tabs[i].onclick = displayPage;
                    }
                    
                }
                
            }
            
            // 点击标签
            function displayPage() {
                var current = this.parentNode.getAttribute('data-current'),
                    ident = this.id.split('_')[1];
                
                document.getElementById('tabnav_' + current).setAttribute('style', 'background-color: #fff');
                document.getElementById('tabpage_' + current).style.display = 'none';
                this.setAttribute('style', 'background-color: #f00');
                document.getElementById('tabpage_' + ident).style.display = 'block';
                this.parentNode.setAttribute('data-current', ident);
            }
            
        </script>
    </head>
    <body>
        <div class="tabcontainer">
            <div class="tabnavigation">
                <ul>
                    <li id="tabnav_1">Page One</li>
                    <li id="tabnav_2">Page Two</li>
                    <li id="tabnav_3">Page Three</li>
                </ul>
            </div>
            <div class="tabpages">
                <div class="tabpage" id="tabpage_1">
                    <p>page 1</p>
                </div>
                <div class="tabpage" id="tabpage_2">
                    <p>page 2</p>
                </div>
                <div class="tabpage" id="tabpage_3">
                    <p>page 3</p>
                </div>
            </div>
        </div>
        <div class="tabcontainer">
            <div class="tabnavigation">
                <ul>
                    <li id="tabnav_4">Page Two One</li>
                    <li id="tabnav_5">Page Two Two</li>
                </ul>
            </div>
            <div class="tabpages">
                <div class="tabpage" id="tabpage_4">
                    <p>page 4</p>
                </div>
                <div class="tabpage" id="tabpage_5">
                    <p>page 5</p>
                </div>
                <div class="tabpage" id="tabpage_6">
                    <p>page 6</p>
                </div>
            </div>
        </div>
    </body>
</html>
``` 
