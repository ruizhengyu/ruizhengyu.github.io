---
date: 2016-04-13 21:06:30+00:00
layout: post
title: JavaScript经典实例 示例15-6
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

作为text/html嵌入到HTML 5的SVG
----------------

<html>
    <head>
        <title>SVG</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
        
            // 设置元素onclick事件处理程序
            window.onload = function() {
                var circle = document.getElementById('redcircle');
                
                // onclick事件处理程序，修改圆的半径
                circle.onclick = function() {
                    var r = parseInt(this.getAttributeNS(null, 'r'));
                    
                    r -= 10;
                    circle.setAttributeNS('', 'r', r);
                    var dc = document.getElementsByTagNameNS('http://purl.org/dc/elements/1.1/', 'title');
                    
                    for (var i = 0; i < dc.length; i++) {
                        var str = dc.item(i).namespaceURI + '' + dc.item(i).prefix + '' + dc.item(i).localName + '' + dc.item(i).textContent;
                        
                        alert(str);
                    }
                    
                }
                
            }
        </script>
    </head>
    <body>
        <h1>SVG</h1>
        <p>This is <code>text/html</code>!</p>
        <h2>SVG</h2>
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

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>SVG</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
        
            // 设置元素onclick事件处理程序
            window.onload = function() {
                var circle = document.getElementById('redcircle');
                
                // onclick事件处理程序，修改圆的半径
                circle.onclick = function() {
                    var r = parseInt(this.getAttributeNS(null, 'r'));
                    
                    r -= 10;
                    circle.setAttributeNS('', 'r', r);
                    var dc = document.getElementsByTagNameNS('http://purl.org/dc/elements/1.1/', 'title');
                    
                    for (var i = 0; i < dc.length; i++) {
                        var str = dc.item(i).namespaceURI + '' + dc.item(i).prefix + '' + dc.item(i).localName + '' + dc.item(i).textContent;
                        
                        alert(str);
                    }
                    
                }
                
            }
        </script>
    </head>
    <body>
        <h1>SVG</h1>
        <p>This is <code>text/html</code>!</p>
        <h2>SVG</h2>
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
