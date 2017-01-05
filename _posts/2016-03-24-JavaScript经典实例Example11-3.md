---
date: 2016-03-24 16:26:30+00:00
layout: post
title: JavaScript经典实例 示例11-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

使用first-of-type选择器以突出显示一个div元素中的第一段
----------------

<html>
    <head>
        <title>paras</title>
        <meta charset="utf-8">
        <style>
            div
            {
                padding: 10px;
                border: 1px solid #000000;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                document.onclick = function() {
                    try {
                        var paras = document.querySelectorAll('div p:first-of-type');
                        
                        for (var i = 0; i < paras.length; i++) {
                            paras[i].setAttribute('style', 'background-color: #ffff00');
                        }
                        
                    } catch(e) {
                        var divs = document.querySelectorAll('div');
                        
                        for (var j = 0; j < divs.length; j++) {
                            var ps = divs.item[i].getElementByTagName('p');
                            
                            if (ps.length > 0) {
                                ps[0].setAttribute('style', 'background-color: #ffff00');
                            }
                            
                        }
                        
                    }
                    
                };
                
            }
            
            
        </script>
    </head>
    <body>
        <div>
            <p>Paragraph one</p>
            <p>Paragraph two</p>
            <p>Paragraph three</p>
        </div>
        <div>
            <p>Paragraph one</p>
            <p>Paragraph two</p>
        </div>
        <div>
            <ul>
                <li>List item one</li>
                <li>Lisr item two</li>
            </ul>
            <p>Paragraph one</p>
            <p>Paragraph two</p>
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE>
<html>
    <head>
        <title>paras</title>
        <meta charset="utf-8">
        <style>
            div
            {
                padding: 10px;
                border: 1px solid #000000;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                document.onclick = function() {
                    try {
                        var paras = document.querySelectorAll('div p:first-of-type');
                        
                        for (var i = 0; i < paras.length; i++) {
                            paras[i].setAttribute('style', 'background-color: #ffff00');
                        }
                        
                    } catch(e) {
                        var divs = document.querySelectorAll('div');
                        
                        for (var j = 0; j < divs.length; j++) {
                            var ps = divs.item[i].getElementByTagName('p');
                            
                            if (ps.length > 0) {
                                ps[0].setAttribute('style', 'background-color: #ffff00');
                            }
                            
                        }
                        
                    }
                    
                };
                
            }
            
            
        </script>
    </head>
    <body>
        <div>
            <p>Paragraph one</p>
            <p>Paragraph two</p>
            <p>Paragraph three</p>
        </div>
        <div>
            <p>Paragraph one</p>
            <p>Paragraph two</p>
        </div>
        <div>
            <ul>
                <li>List item one</li>
                <li>Lisr item two</li>
            </ul>
            <p>Paragraph one</p>
            <p>Paragraph two</p>
        </div>
    </body>
</html>
``` 

`getElementsByTagNameNS()`方法可返回带有指定名称和命名空间的所有元素的一个节点列表。
`getElementsByTagNameNS(ns,name)``ns`	字符串值，可规定需检索的命名空间名称。值 "*" 可匹配所有的标签。
`name`	字符串值，可规定需检索的标签名。值 "*" 可匹配所有的标签。

`prefix`属性返回选定的节点的命名空间前缀。
如果选定的节点不是元素或属性，则该属性返回 `NULL`。

`namespaceURI` 属性为被选节点返回命名空间的 `URI`。
如果选定的节点不是元素或属性，则该属性返回 `NULL`。

`localName` 属性返回被选元素的本地名称（元素名称）。

`text` 属性返回选定节点中所有文本节点的值。

`textContent` 属性返回或设置选定元素的文本。
如果返回文本，则该属性返回元素节点内所有文本节点的值。
如果设置文本，则该属性删除所有子节点，并用单个文本节点来替换它们。

`getElementsByTagName()` 方法可返回带有指定标签名的对象的集合。`document.getElementsByTagName(tagname)``getElementsByTagName()` 方法返回元素的顺序是它们在文档中的顺序。
如果把特殊字符串 "*" 传递给 `getElementsByTagName()` 方法，它将返回文档中所有元素的列表，元素排列的顺序就是它们在文档中的顺序。