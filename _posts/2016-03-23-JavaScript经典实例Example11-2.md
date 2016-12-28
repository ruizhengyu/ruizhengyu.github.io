---
date: 2016-03-23 16:26:30+00:00
layout: post
title: JavaScript经典实例 示例11-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

getElementsByTagName的命名空间和命名空间变体之间的区别
----------------

<html xmlns="http://www.w3.org/1999/xthml" xml:lang="en">
<head>
<title>Namespace</title>
<script type="text/javascript">
//<![CDTAT[

window.onload = function(){

    var str = "";
    var title = document.getElementsByTagName("title");
    for(var i = 0; i < title.length; i++){
        str += title.item(i).namespaceURI + " " + title.item(i).prefix + " " + title.item(i).localName + " " + title.item(i).text + " ";
    }
    var blk1 = document.getElementById("result1");
    blk1.innerHTML = str;
    
    str = "";
    if(!document.getElementsByTagNameNS){
        return;
    }
    var titlens = document.getElementsByTagNameNS("http://purl.org/dc/element/1.1/", "title");
    for(var i = 0; i < titlens.length; i++){
        str += titlens.item(i).namespaceURI + " " + titlens.item(i).prefix + " " + titlens.item(i).localName + " " + titlens.item(i).textContent + " ";
    }
    var blk2 = document.getElementById("result2");
    blk2.innerHTML = str;
}

//--><!]]>
</script>
</head>
<body>
<h1>SVG</h1>
<svg id="svgelem" height="800" xmlns="http://www.w3.org/2000/svg">
    <circle id="redcircle" cx="300" cy="300" r="300" fill="red" />
    <metadata>
        <rdf:RDF xmlns:cc="http://web.resource.org/cc/" xmlns:dc="http://purl.org/dc/element/1.1/" xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
            <cc:Work rdf:about="">
                <dc:title>Sizing Red Circle</dc:title>
                <dc:description></dc:description>
                <dc:subject>
                    <rdf:Bag>
                        <rdf:li>circle</rdf:li>
                        <rdf:li>red</rdf:li>
                        <rdf:li>graphic</rdf:li>
                    </rdf:Bag>
                </dc:subject>
                <dc:publisher>
                    <cc:Agent rdf:about="http://www.openclipart.org">
                        <dc:title>Testing RDF in SVG</dc:title>
                    </cc:Agent>
                </dc:publisher>
                <dc:creator>
                    <cc:Agent>
                        <dc:title id="title">Testing</dc:title>
                    </cc:Agent>
                </dc:creator>
                <dc:rights>
                    <cc:Agent>
                        <dc:title>Testing</dc:title>
                    </cc:Agent>
                </dc:rights>
                <dc:date></dc:date>
                <dc:format>image/svg+xml</dc:format>
                <dc:type rdf:resource="http://purl.org/dc/dcmitype/StillImage" />
                <cc:license rdf:resource="http://web.resource.org/cc/PublicDomain" />
                <dc:language>en</dc:language>
            </cc:Work>
            <cc:License rdf:about="http://web.resource.org/cc/PublicDomain">
                <cc:permits rdf:resource="http://web.resource.org/cc/Reproduction" />
                <cc:permits rdf:resource="http://web.resource.org/cc/Distribution" />
                <cc:permits rdf:resource="http://web.resource.org/cc/DerivativeWorks" />
            </cc:License>
        </rdf:RDF>
    </metadata>
</svg>
<div id="result1"></div>
<div id="result2"></div>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1 plus MathML 2.0 plus SVG 1.1//EN" "http://www.w3.org/2002/04/xhtml-math-svg/xhtml-math-svg.dtd">
<html xmlns="http://www.w3.org/1999/xthml" xml:lang="en">
<head>
<title>Namespace</title>
<script type="text/javascript">
//<![CDTAT[

window.onload = function(){

    var str = "";
    var title = document.getElementsByTagName("title");
    for(var i = 0; i < title.length; i++){
        str += title.item(i).namespaceURI + " " + title.item(i).prefix + " " + title.item(i).localName + " " + title.item(i).text + " ";
    }
    alert(str);
    
    str = "";
    if(!document.getElementsByTagNameNS){
        return;
    }
    var titlens = document.getElementsByTagNameNS("http://purl.org/dc/element/1.1/", "title");
    for(var i = 0; i < titlens.length; i++){
        str += titlens.item(i).namespaceURI + " " + titlens.item(i).prefix + " " + titlens.item(i).localName + " " + titlens.item(i).textContent + " ";
    }
    alert(str);
}

//--><!]]>
</script>
</head>
<body>
<h1>SVG</h1>
<svg id="svgelem" height="800" xmlns="http://www.w3.org/2000/svg">
    <circle id="redcircle" cx="300" cy="300" r="300" fill="red" />
    <metadata>
        <rdf:RDF xmlns:cc="http://web.resource.org/cc/" xmlns:dc="http://purl.org/dc/element/1.1/" xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
            <cc:Work rdf:about="">
                <dc:title>Sizing Red Circle</dc:title>
                <dc:description></dc:description>
                <dc:subject>
                    <rdf:Bag>
                        <rdf:li>circle</rdf:li>
                        <rdf:li>red</rdf:li>
                        <rdf:li>graphic</rdf:li>
                    </rdf:Bag>
                </dc:subject>
                <dc:publisher>
                    <cc:Agent rdf:about="http://www.openclipart.org">
                        <dc:title>Testing RDF in SVG</dc:title>
                    </cc:Agent>
                </dc:publisher>
                <dc:creator>
                    <cc:Agent>
                        <dc:title id="title">Testing</dc:title>
                    </cc:Agent>
                </dc:creator>
                <dc:rights>
                    <cc:Agent>
                        <dc:title>Testing</dc:title>
                    </cc:Agent>
                </dc:rights>
                <dc:date></dc:date>
                <dc:format>image/svg+xml</dc:format>
                <dc:type rdf:resource="http://purl.org/dc/dcmitype/StillImage" />
                <cc:license rdf:resource="http://web.resource.org/cc/PublicDomain" />
                <dc:language>en</dc:language>
            </cc:Work>
            <cc:License rdf:about="http://web.resource.org/cc/PublicDomain">
                <cc:permits rdf:resource="http://web.resource.org/cc/Reproduction" />
                <cc:permits rdf:resource="http://web.resource.org/cc/Distribution" />
                <cc:permits rdf:resource="http://web.resource.org/cc/DerivativeWorks" />
            </cc:License>
        </rdf:RDF>
    </metadata>
</svg>
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