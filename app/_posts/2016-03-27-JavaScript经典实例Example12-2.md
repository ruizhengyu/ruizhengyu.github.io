---
date: 2016-03-27 15:06:30+00:00
layout: post
title: JavaScript经典实例 示例12-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

展示向一个Web页面添加内容的各种方法
----------------

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
    <head>
        <title>Adding Paragraphs</title>
        <script type="text/javascript">
            window.onload = function() {
                
                // 使用getElementById访问该div元素
                var div = document.getElementById('target'),
                
                // 获取段落文本
                    txt = prompt('Enter new paragraph text', 'new paragraph text'),
                
                // 使用getElementsByTagName和集合索引
                // 来访问第一个段落
                    oldPara = div.getElementsByTagName('p')[0],
                
                // 创建一个文本节点
                    txtNode = document.createTextNode(txt),
                    
                // 创建一个新的段落
                    para = document.createElement('p');
                    
                // 给该段落附加文本，并插入新的段落
                para.appendChild(txtNode);
                div.insertBefore(para, oldPara);
            }
                        
        </script>
    </head>
    <body>
        <div id="target">
            <p>
                There id a language 'little known,'<br />
                Lovers claim it as their own.
            </p>
            <p>
                Its symbols smile upon the land, <br />
                Wrought by nature's wondrous hand;
            </p>
            <p>
                And in their silent beauty speak, <br />
                Of life and joy, to those who seek.
            </p>
            <p>
                For Love Divine and sunny huors <br />
                In the language of the flowers.
            </p>
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
    <head>
        <title>Adding Paragraphs</title>
        <script type="text/javascript">
            window.onload = function() {
                
                // 使用getElementById访问该div元素
                var div = document.getElementById('target'),
                
                // 获取段落文本
                    txt = prompt('Enter new paragraph text', ''),
                
                // 使用getElementsByTagName和集合索引
                // 来访问第一个段落
                    oldPara = div.getElementsByTagName('p')[0],
                
                // 创建一个文本节点
                    txtNode = document.createTextNode(txt),
                    
                // 创建一个新的段落
                    para = document.createElement('p');
                    
                // 给该段落附加文本，并插入新的段落
                para.appendChild(txtNode);
                div.insertBefore(para, oldPara);
            }
                        
        </script>
    </head>
    <body>
        <div id="target">
            <p>
                There id a language 'little known,'<br />
                Lovers claim it as their own.
            </p>
            <p>
                Its symbols smile upon the land, <br />
                Wrought by nature's wondrous hand;
            </p>
            <p>
                And in their silent beauty speak, <br />
                Of life and joy, to those who seek.
            </p>
            <p>
                For Love Divine and sunny huors <br />
                In the language of the flowers.
            </p>
        </div>
    </body>
</html>
``` 
