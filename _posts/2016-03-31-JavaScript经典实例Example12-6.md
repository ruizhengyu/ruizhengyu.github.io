---
date: 2016-03-31 15:16:30+00:00
layout: post
title: JavaScript经典实例 示例12-6
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

添加并删除表格行及相关的单元格和数据
----------------

<html>
    <head>
        <title>Adding and Removing Elements</title>
        <style type="text/css">
            table
            {
                border-collapse: collapse;
            }
            
            td, th
            {
                padding: 5px;
                border: 1px solid #ccc;
            }
            
            tr:nth-child(2n+1)
            {
                background-color: #efe;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                var values = new Array(3),
                    mixed = document.getElementById('mixed'),
                    
                // IE7需要tbody
                    tbody = document.createElement('tbody');
                
                values[0] = [123.45, 'apple', true];
                values[1] = [65, 'banana', false];
                values[2] = [1034.99, 'cherry', false];
                
                // 针对每个外围数组行
                for (var i = 0; i < values.length; i++) {
                    var tr = document.createElement('tr');
                    
                    // 针对每个内部数组单元格
                    // 创建td，然后，附加文本
                    for (var j = 0; j < values[i].length; j++) {
                        var td = document.createElement('td'),
                            txt = document.createTextNode(values[i][j]);
                            
                        td.appendChild(txt);
                        tr.appendChild(td);
                    }
                    
                    // 绑定事件处理程序
                    tr.onclick = prunerow;
                    
                    // 把行附加到表
                    tbody.appendChild(tr);
                    mixed.appendChild(tbody);
                }
                
            }
            
            function prunerow(){
                var parent = this.parentNode,
                    oldrow = parent.removeChild(this),
                    datastring = '';
                
                for (var i = 0; i < oldrow.childNodes.length; i++) {
                    var cell = oldrow.childNodes[i];
                    
                    datastring += cell.firstChild.data + ' ';
                }
                
                alert('removed' + datastring);
            }
            
        </script>
    </head>
    <body>
        <table id="mixed">
            <tr>
                <th>Value One</th>
                <th>Value Two</th>
                <th>Value Three</th>
            </tr>
        </table>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Adding and Removing Elements</title>
        <style type="text/css">
            table
            {
                border-collapse: collapse;
            }
            
            td, th
            {
                padding: 5px;
                border: 1px solid #ccc;
            }
            
            tr:nth-child(2n+1)
            {
                background-color: #efe;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                var values = new Array(3),
                    mixed = document.getElementById('mixed'),
                    
                // IE7需要tbody
                    tbody = document.createElement('tbody');
                
                values[0] = [123.45, 'apple', true];
                values[1] = [65, 'banana', false];
                values[2] = [1034.99, 'cherry', false];
                
                // 针对每个外围数组行
                for (var i = 0; i < values.length; i++) {
                    var tr = document.createElement('tr');
                    
                    // 针对每个内部数组单元格
                    // 创建td，然后，附加文本
                    for (var j = 0; j < values[i].length; j++) {
                        var td = document.createElement('td'),
                            txt = document.createTextNode(values[i][j]);
                            
                        td.appendChild(txt);
                        tr.appendChild(td);
                    }
                    
                    // 绑定事件处理程序
                    tr.onclick = prunerow;
                    
                    // 把行附加到表
                    tbody.appendChild(tr);
                    mixed.appendChild(tbody);
                }
                
            }
            
            function prunerow(){
                var parent = this.parentNode,
                    oldrow = parent.removeChild(this),
                    datastring = '';
                
                for (var i = 0; i < oldrow.childNodes.length; i++) {
                    var cell = oldrow.childNodes[i];
                    
                    datastring += cell.firstChild.data + ' ';
                }
                
                alert('removed' + datastring);
            }
            
        </script>
    </head>
    <body>
        <table id="mixed">
            <tr>
                <th>Value One</th>
                <th>Value Two</th>
                <th>Value Three</th>
            </tr>
        </table>
    </body>
</html>
``` 
