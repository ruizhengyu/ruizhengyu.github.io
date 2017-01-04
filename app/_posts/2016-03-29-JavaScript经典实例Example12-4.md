---
date: 2016-03-29 10:26:30+00:00
layout: post
title: JavaScript经典实例 示例12-4
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

从数组中提取数据，创建并附加表行
----------------

<html>
    <head>
        <title>Sum Table Column</title>
        <script type="text/javascript">
            window.onload = function() {
                var values = new Array(3),
                    mixed = document.getElementById('mixed'),
                    
                // IE7只支持向tbody附加行
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
                    
                    // 把行附加到表
                    // IE7需要把行附加到tbody
                    tbody.appendChild(tr);
                    mixed.appendChild(tbody);
                }
                
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
        <title>Sum Table Column</title>
        <script type="text/javascript">
            window.onload = function() {
                var values = new Array(3),
                    mixed = document.getElementById('mixed'),
                    
                // IE7只支持向tbody附加行
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
                    
                    // 把行附加到表
                    // IE7需要把行附加到tbody
                    tbody.appendChild(tr);
                    mixed.appendChild(tbody);
                }
                
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

`<tbody>` 标签表格主体（正文）。该标签用于组合 `HTML` 表格的主体内容。
`tbody` 元素应该与 `thead` 和 `tfoot` 元素结合起来使用。
`thead` 元素用于对 `HTML` 表格中的表头内容进行分组，而 `tfoot` 元素用于对 `HTML` 表格中的表注（页脚）内容进行分组。
注释：如果您使用 `thead`、`tfoot` 以及 `tbody` 元素，您就必须使用全部的元素。它们的出现次序是：`thead`、`tfoot`、`tbody`，这样浏览器就可以在收到所有数据前呈现页脚了。您必须在 `table` 元素内部使用这些标签。
提示：在默认情况下这些元素不会影响到表格的布局。不过，您可以使用 `CSS` 使这些元素改变表格的外观。
详细描述
`thead`、`tfoot` 以及 `tbody` 元素使您有能力对表格中的行进行分组。当您创建某个表格时，您也许希望拥有一个标题行，一些带有数据的行，以及位于底部的一个总计行。这种划分使浏览器有能力支持独立于表格标题和页脚的表格正文滚动。当长的表格被打印时，表格的表头和页脚可被打印在包含表格数据的每张页面上。
