---
date: 2016-04-29 14:26:30+00:00
layout: post
title: JavaScript经典实例 示例19-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
处理返回的XML中的story信息的JavaScript应用程序
----------------

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
    <head>
        <title>Stories</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
            var xmlHttpObj;
            
            window.onload = function() {
                var radios = document.forms[0].elements['category'];
                
                for (var i = 0; i < radios.length; i++) {
                    radios[i].onclick = getStories;
                }
                
            }
            
            function getStories() {
                // 分类
                var category = encodeURIComponent(this.value);
                
                // Ajax对象
                if (window.XMLHttpRequest) {
                    xmlHttpObj = new XMLHttpRequest();
                }
                
                // 构建请求
                var url = 'stories.php?category=' + category;
                
                xmlHttpObj.open('GET', url, true);
                xmlHttpObj.onreadystatechange = getData;
                xmlHttpObj.send(null);
            }
            
            function getData() {
                if (xmlHttpObj.readyState === 4 && xmlHttpObj.status === 200) {
                    try {
                        var result = document.getElementById('result'),
                            str = '<p>',
                            stories = xmlHttpObj.responseXML.getElementsByTagName('story');
                            
                        for (var i = 0; i < stories.length; i++) {
                            var story = stories[i],
                                url = story.childNodes[0].firstChild.nodeValue,
                                title = story.childNodes[1].firstChild.nodeValue;
                            
                            if (url === 'none') {
                                str += title + '<br />';
                            } else {
                                str += '<a href="' + url + '">' + title + '</a><br />';
                            }
                            
                        }
                        
                        // 完成HTML和插入
                        str += '</p>';
                        result.innerHTML = str;
                    } catch(e) {
                        alert(e.message);
                    }
                    
                }
            }
        </script>
    </head>
    <body>
        <form id="categoryform">
            CSS: <input type="radio" name="category" value="CSS" /><br />
            eBooks: <input type="radio" name="category" value="ebooks" /><br />
            Missouri: <input type="radio" name="category" value="missouri" /><br />
            Video: <input type="radio" name="category" value="video" /><br />
        </form>
        <div id="result">
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
    <head>
        <title>Stories</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
            var xmlHttpObj;
            
            window.onload = function() {
                var radios = document.forms[0].elements['category'];
                
                for (var i = 0; i < radios.length; i++) {
                    radios[i].onclick = getStories;
                }
                
            }
            
            function getStories() {
                // 分类
                var category = encodeURIComponent(this.value);
                
                // Ajax对象
                if (window.XMLHttpRequest) {
                    xmlHttpObj = new XMLHttpRequest();
                }
                
                // 构建请求
                var url = 'stories.php?category=' + category;
                
                xmlHttpObj.open('GET', url, true);
                xmlHttpObj.onreadystatechange = getData;
                xmlHttpObj.send(null);
            }
            
            function getData() {
                if (xmlHttpObj.readyState === 4 && xmlHttpObj.status === 200) {
                    try {
                        var result = document.getElementById('result'),
                            str = '<p>',
                            stories = xmlHttpObj.responseXML.getElementsByTagName('story');
                            
                        for (var i = 0; i < stories.length; i++) {
                            var story = stories[i],
                                url = story.childNodes[0].firstChild.nodeValue,
                                title = story.childNodes[1].firstChild.nodeValue;
                            
                            if (url === 'none') {
                                str += title + '<br />';
                            } else {
                                str += '<a href="' + url + '">' + title + '</a><br />';
                            }
                            
                        }
                        
                        // 完成HTML和插入
                        str += '</p>';
                        result.innerHTML = str;
                    } catch(e) {
                        alert(e.message);
                    }
                    
                }
            }
        </script>
    </head>
    <body>
        <form id="categoryform">
            CSS: <input type="radio" name="category" value="CSS" /><br />
            eBooks: <input type="radio" name="category" value="ebooks" /><br />
            Missouri: <input type="radio" name="category" value="missouri" /><br />
            Video: <input type="radio" name="category" value="video" /><br />
        </form>
        <div id="result">
        </div>
    </body>
</html>
``` 
