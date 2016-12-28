---
date: 2016-03-28 14:26:30+00:00
layout: post
title: JavaScript经典实例 示例12-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

从Web文档提取出链接并添加到页面末尾的一个列表中
----------------

<html>
    <head>
        <title>Moving Links</title>
        <style type="text/css">
            ul li
            {
                list-style-type: none;
                padding-bottom: 5px;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                var links = document.querySelectorAll('a'),
                    footnote = document.createElement('ul');
                    
                // 针对所有的链接
                for (var i = 0; i < links.length; i++) {
                    
                    // 获取父节点
                    var parent = links[i].parentNode,
                    
                    // 创建编号索引文本
                        num = document.createTextNode(i + 1),
                        sup = document.createElement('sup');
                    sup.appendChild(num);
                    
                    // 处理子节点
                    var children = links[i].childNodes;
                    
                    for (var j = 0; j < children.length; j++) {
                        var newChild = children[j].cloneNode(true);
                        
                        parent.insertBefore(newChild, links[i]);
                    }
                    
                    // 添加上标编号
                    var sup2 = sup.cloneNode(true);
                    
                    parent.insertBefore(sup2, links[i]);
                    
                    // 添加到脚注的一个链接
                    var li = document.createElement('li');
                    
                    li.appendChild(sup);
                    li.appendChild(links[i]);
                    footnote.appendChild(li);
                }
                
                document.getElementsByTagName('body')[0].appendChild(footnote);
            }
                        
        </script>
    </head>
    <body>
        <div id="target">
            <p>
                A favorite place of mine to visit in St. Louis is the 
                <a href="http://www.mobot.org/">Missouri Botanical Gardens</a>
                Great flowers all year round, though, are the 
                <a href="http://stlzoo.org/">St. Louis Zoo</a>, the 
                <a href="http://www.nps.gov/jeff/index.htm"><em>Gateway Arch</em></a>
                , the <a href="http://www.citygardenstl.org/">City Garden</a>
                , and the <a href="http://mdc.mo.gov/areas/cnc/powder/">Powder Valley Conservation Nature Center</a>
            </p>
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Moving Links</title>
        <style type="text/css">
            ul li
            {
                list-style-type: none;
                padding-bottom: 5px;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                var links = document.querySelectorAll('a'),
                    footnote = document.createElement('ul');
                    
                // 针对所有的链接
                for (var i = 0; i < links.length; i++) {
                    
                    // 获取父节点
                    var parent = links[i].parentNode,
                    
                    // 创建编号索引文本
                        num = document.createTextNode(i + 1),
                        sup = document.createElement('sup');
                    sup.appendChild(num);
                    
                    // 处理子节点
                    var children = links[i].childNodes;
                    
                    for (var j = 0; j < children.length; j++) {
                        var newChild = children[j].cloneNode(true);
                        
                        parent.insertBefore(newChild, links[i]);
                    }
                    
                    // 添加上标编号
                    var sup2 = sup.cloneNode(true);
                    
                    parent.insertBefore(sup2, links[i]);
                    
                    // 添加到脚注的一个链接
                    var li = document.createElement('li');
                    
                    li.appendChild(sup);
                    li.appendChild(links[i]);
                    footnote.appendChild(li);
                }
                
                document.getElementsByTagName('body')[0].appendChild(footnote);
            }
                        
        </script>
    </head>
    <body>
        <div id="target">
            <p>
                A favorite place of mine to visit in St. Louis is the 
                <a href="http://www.mobot.org/">Missouri Botanical Gardens</a>
                Great flowers all year round, though, are the 
                <a href="http://stlzoo.org/">St. Louis Zoo</a>, the 
                <a href="http://www.nps.gov/jeff/index.htm"><em>Gateway Arch</em></a>
                , the <a href="http://www.citygardenstl.org/">City Garden</a>
                , and the <a href="http://mdc.mo.gov/areas/cnc/powder/">Powder Valley Conservation Nature Center</a>
            </p>
        </div>
    </body>
</html>
``` 
