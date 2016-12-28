---
date: 2016-05-01 16:46:30+00:00
layout: post
title: JavaScript经典实例 示例19-4
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
从页面中提取RDFa并且将数据嵌入到页面中
----------------

<html xmlns="http://www.w3.org/1999/xhtml"
    xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
    xmlns:dc="http://purl.org/dc/elements/1.1/"
    xmlns:foaf="http://xmlns.com/foaf/0.1/">
    <head profile="http://ns.inria.fr/grddl/rdfa/">
        <title>Biblio description</title>
        <style type="text/css">
            div
            {
                margin: 20px;
            }
        </style>
        <script type="text/javascript" src="/assets/media/image/json2.js"></script>
        <script type="text/javascript" src="/assets/media/image/jquery-2.2.4.js"></script>
        <script type="text/javascript" src="/assets/media/image/jquery.rdfquery.rdfa-1.0.js"></script>
        <script type="text/javascript">
            window.onload = function() {
                var j = $('#biblio').rdf()
                    .base('http://burningbird.net')
                    .prefix('rdf', 'http://www.w3.org/1999/02/22-rdf-syntax-ns#')
                    .prefix('dc', 'http://purl.org/dc/elements/1.1/')
                    .prefix('foaf', 'http://xmlns.com/foaf/0.1/'),
                    d = j.databank.dump();
                    str = JSON.stringify(d);
                
                document.getElementById('result1').innerHTML = str;
                
                var t = j.databank.triples(),
                    str2 = '';
                
                for (var i = 0; i < t.length; i++) {
                    str2 = str2 + t[i].toString().replace(/</g, '&lt;').replace(/>/g, '&gt;') + '<br />';
                }
                
                document.getElementById('result2').innerHTML = str2;
            }
        </script>
    </head>
    <body>
        <h1>Biblio description</h1>
        <dl about="http://www.w3.org/TR/2004/REC-rdf-mt-20040210/" id="biblio">
            <dt>Title</dt>
            <dd property="dc:title">
                RDF Semantics - W3C Recommendation 10 February 2004
            </dd>
            <dt>Author</dt>
            <dd rel="dc:creator" href="#a1">
                <span id="a1">
                    <link rel="rdf:type" href="[foaf:Preson]" />
                    <span property="foaf:name">Patrick Hayes</span>
                    see <a rel="foaf:homeage" href="http://www.ihmc.us/users/user.php?UserID=42">homepage</a>
                </span>
            </dd>
        </dl>
        <div id="result1"></div>
        <div id="result2"></div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml"
    xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
    xmlns:dc="http://purl.org/dc/elements/1.1/"
    xmlns:foaf="http://xmlns.com/foaf/0.1/">
    <head profile="http://ns.inria.fr/grddl/rdfa/">
        <title>Biblio description</title>
        <style type="text/css">
            div
            {
                margin: 20px;
            }
        </style>
        <script type="text/javascript" src="/assets/media/image/json2.js"></script>
        <script type="text/javascript" src="/assets/media/image/jquery-2.2.4.js"></script>
        <script type="text/javascript" src="/assets/media/image/jquery.rdfquery.rdfa-1.0.js"></script>
        <script type="text/javascript">
            window.onload = function() {
                var j = $('#biblio').rdf()
                    .base('http://burningbird.net')
                    .prefix('rdf', 'http://www.w3.org/1999/02/22-rdf-syntax-ns#')
                    .prefix('dc', 'http://purl.org/dc/elements/1.1/')
                    .prefix('foaf', 'http://xmlns.com/foaf/0.1/'),
                    d = j.databank.dump();
                    str = JSON.stringify(d);
                
                document.getElementById('result1').innerHTML = str;
                
                var t = j.databank.triples(),
                    str2 = '';
                
                for (var i = 0; i < t.length; i++) {
                    str2 = str2 + t[i].toString().replace(/</g, '&lt;').replace(/>/g, '&gt;') + '<br />';
                }
                
                document.getElementById('result2').innerHTML = str2;
            }
        </script>
    </head>
    <body>
        <h1>Biblio description</h1>
        <dl about="http://www.w3.org/TR/2004/REC-rdf-mt-20040210/" id="biblio">
            <dt>Title</dt>
            <dd property="dc:title">
                RDF Semantics - W3C Recommendation 10 February 2004
            </dd>
            <dt>Author</dt>
            <dd rel="dc:creator" href="#a1">
                <span id="a1">
                    <link rel="rdf:type" href="[foaf:Preson]" />
                    <span property="foaf:name">Patrick Hayes</span>
                    see <a rel="foaf:homeage" href="http://www.ihmc.us/users/user.php?UserID=42">homepage</a>
                </span>
            </dd>
        </dl>
        <div id="result1"></div>
        <div id="result2"></div>
    </body>
</html>
``` 
