---
date: 2016-04-25 19:56:30+00:00
layout: post
title: JavaScript经典实例 示例18-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
创建一个按需选项Ajax应用
----------------

<html>
    <head>
        <title>On Demand Select</title>
        <style>
            #nicestuff
            {   
                display: none;
                margin: 10px 0;
            }
            
            #nicething
            {
                width: 400px;
            }
            
        </style>
        <script type="text/javascript">
            var xmlhttp;
            
            function populateSelect() {
                var value,
                inputs = this.getElementsByTagName('input');
            
                for (var i = 0; i < inputs.length; i++) {
                    if (inputs[i].checked) {
                        value = inputs[i].value;
                        break;
                    }
                    
                }
                
                // 准备请求
                if (!xmlhttp) {
                    xmlhttp = new XMLHttpRequest();
                }
                
                var url = 'http://lovechina.xyz/JavaScript经典实例Example18-1?nicething=' + value;
                
                xmlhttp.open('GET', url, true);
                xmlhttp.onreadystatechange = getThings;
                xmlhttp.send(null);
            }
            
            // 处理返回值
            function getThings() {
                if (xmlhttp.readyState === 4 && xmlhttp.status === 200) {
                    var select = document.getElementById('nicestuff'),
                        nicethings = xmlhttp.responseText.split(',');
                                        
                    select.length = 0;
                    for (var i = 0; i < nicethings.length; i++) {
                        select.options[select.length] = new Option(nicethings[i], nicethings[i]);
                    }
                    
                    select.style.display = 'block';
                } else if (xmlhttp.readyState === 4 && xmlhttp.status !== 200) {
                    alert('No items returned for request');
                }
                
            }
            
            window.onload = function() {
                document.getElementById('submitbutton').style.display = 'none';
                document.getElementById('nicething').onclick = populateSelect;
            }
            
        </script>
    </head>
    <body>
        <form method="get">
            <p>Select one:</p>
            <fieldset id="nicething">
                <input type="radio" name="nicethings" value="bird" />
                <label for="bird">Brid</label><br />
                <input type="radio" name="nicethings" value="flower" />
                <label for="flower">Flower</label><br />
                <input type="radio" name="nicethings" value="sweets" />
                <label for="sweets">Sweets</label><br />
                <input type="radio" name="nicethings" value="cuddles" />
                <label for="cuddles">Cute Critters</label><br />
            </fieldset>
            <input type="submit" id="submitbutton" value="get nice things" />
            <select id="nicestuff"></select>
        </form>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>On Demand Select</title>
        <style>
            #nicestuff
            {   
                display: none;
                margin: 10px 0;
            }
            
            #nicething
            {
                width: 400px;
            }
            
        </style>
        <script type="text/javascript">
            var xmlhttp;
            
            function populateSelect() {
                var value,
                inputs = this.getElementsByTagName('input');
            
                for (var i = 0; i < inputs.length; i++) {
                    if (inputs[i].checked) {
                        value = inputs[i].value;
                        break;
                    }
                    
                }
                
                // 准备请求
                if (!xmlhttp) {
                    xmlhttp = new XMLHttpRequest();
                }
                
                var url = 'http://lovechina.xyz/JavaScript经典实例Example18-1.html?nicething=' + value;
                
                xmlhttp.open('GET', url, true);
                xmlhttp.onreadystatechange = getThings;
                xmlhttp.send(null);
            }
            
            // 处理返回值
            function getThings() {
                if (xmlhttp.readyState === 4 && xmlhttp.status === 200) {
                    var select = document.getElementById('nicestuff'),
                        nicethings = xmlhttp.responseText.split(',');
                                        
                    select.length = 0;
                    for (var i = 0; i < nicethings.length; i++) {
                        select.options[select.length] = new Option(nicethings[i], nicethings[i]);
                    }
                    
                    select.style.display = 'block';
                } else if (xmlhttp.readyState === 4 && xmlhttp.status !== 200) {
                    alert('No items returned for request');
                }
                
            }
            
            window.onload = function() {
                document.getElementById('submitbutton').style.display = 'none';
                document.getElementById('nicething').onclick = populateSelect;
            }
            
        </script>
    </head>
    <body>
        <form method="get">
            <p>Select one:</p>
            <fieldset id="nicething">
                <input type="radio" name="nicethings" value="bird" />
                <label for="bird">Brid</label><br />
                <input type="radio" name="nicethings" value="flower" />
                <label for="flower">Flower</label><br />
                <input type="radio" name="nicethings" value="sweets" />
                <label for="sweets">Sweets</label><br />
                <input type="radio" name="nicethings" value="cuddles" />
                <label for="cuddles">Cute Critters</label><br />
            </fieldset>
            <input type="submit" id="submitbutton" value="get nice things" />
            <select id="nicestuff"></select>
        </form>
    </body>
</html>
``` 
