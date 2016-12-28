---
date: 2016-03-25 11:06:30+00:00
layout: post
title: JavaScript经典实例 示例11-4
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

将第三列中的单元格加和的应用程序
----------------

<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
    <head>
        <title>Sum Table Column</title>
        <script>
            window.onload = function() {
                var table = document.querySelector('table');
                
                table.onclick = sum();
            }
            
            function sum() {
                var rows = document.getElementById('sumtable').getElementsByTagName('tr'),
                    sum = 0;
                
                //从1开始，从而跳过第一行，第一行包含了列标题
                for (var i = 1; i < rows.length; i++) {
                    sum += parseFloat(rows[i].childNodes[2].firstChild.data);
                }
                
                var blk1 = document.getElementById("result1");
                blk1.innerHTML = sum;
            } 
                        
        </script>
    </head>
    <body>
        <table id="sumtable">
            <tr>
                <th>Value 1</th><th>Value 2</th><th>Value 3</th><th>Value 4</th>
            </tr>
            <tr>
                <td>--</td><td>**</td><td>5.0</td><td>nn</td>
            </tr>
            <tr>
                <td>18.53</td><td>9.77</td><td>3.00</td><td>153.88</td>
            </tr>
            <tr>
                <td>Alaska</td><td>Montana</td><td>18.33</td><td>Missouri</td>
            </tr>
        </table>
        <div id="result1"></div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
    <head>
        <title>Sum Table Column</title>
        <script>
            window.onload = function() {
                var table = document.querySelector('table');
                
                table.onclick = sum();
            }
            
            function sum() {
                var rows = document.getElementById('sumtable').getElementsByTagName('tr'),
                    sum = 0;
                
                //从1开始，从而跳过第一行，第一行包含了列标题
                for (var i = 1; i < rows.length; i++) {
                    sum += parseFloat(rows[i].childNodes[2].firstChild.data);
                }
                
                alert(sum);
            } 
                        
        </script>
    </head>
    <body>
        <table id="sumtable">
            <tr>
                <th>Value 1</th><th>Value 2</th><th>Value 3</th><th>Value 4</th>
            </tr>
            <tr>
                <td>--</td><td>**</td><td>5.0</td><td>nn</td>
            </tr>
            <tr>
                <td>18.53</td><td>9.77</td><td>3.00</td><td>153.88</td>
            </tr>
            <tr>
                <td>Alaska</td><td>Montana</td><td>18.33</td><td>Missouri</td>
            </tr>
        </table>
    </body>
</html>
``` 
