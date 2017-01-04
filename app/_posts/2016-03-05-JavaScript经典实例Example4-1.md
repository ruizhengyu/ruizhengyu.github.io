---
date: 2016-03-05 18:44:30+00:00
layout: post
title: JavaScript经典实例 示例4-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

把表格值转换为数字，并且求得加和结果
----------------

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Accessing numbers in table</title>
<script type="text/javascript">
//<![CDATA[

window.onload = function(){

    var sum = 0;
    
    var dataTable = document.getElementById("table1");
    
    //使用querySelector找到第二列中的所有单元格
    var cells = document.querySelectorAll("td + td");
    
    for(var i = 0; i < cells.length; i++)
        sum += parseFloat(cells[i].firstChild.data);
    
    //现在求和知道到达表的末尾
    var newRow = document.createElement("tr");
    
    //第一个单元格
    var firstCell = document.createElement("td");
    var firstCellText = document.createTextNode("Sum:");
    firstCell.appendChild(firstCellText);
    newRow.appendChild(firstCell);
    
    //带有总和的第二个单元格
    var secondCell = document.createElement("td");
    var secondCellText = document.createTextNode(sum);
    secondCell.appendChild(secondCellText);
    newRow.appendChild(secondCell);
    
    //给表添加行
    dataTable.appendChild(newRow);
        
}

//--><!]]>
</script>
</head>
<body>
<table id = "table1">
    <tr>
        <td>Washington</td><td>145</td>
    </tr>
    <tr>
        <td>Oregon</td><td>233</td>
    </tr>
    <tr>
        <td>Missouri</td><td>833</td>
    </tr>
</table>
</body>
</html>


源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Accessing numbers in table</title>
<script type="text/javascript">
//<![CDATA[

window.onload = function(){

    var sum = 0;
    
    var dataTable = document.getElementById("table1");
    
    //使用querySelector找到第二列中的所有单元格
    var cells = document.querySelectorAll("td + td");
    
    for(var i = 0; i < cells.length; i++)
        sum += parseFloat(cells[i].firstChild.data);
    
    //现在求和知道到达表的末尾
    var newRow = document.createElement("tr");
    
    //第一个单元格
    var firstCell = document.createElement("td");
    var firstCellText = document.createTextNode("Sum:");
    firstCell.appendChild(firstCellText);
    newRow.appendChild(firstCell);
    
    //带有总和的第二个单元格
    var secondCell = document.createElement("td");
    var secondCellText = document.createTextNode(sum);
    secondCell.appendChild(secondCellText);
    newRow.appendChild(secondCell);
    
    //给表添加行
    dataTable.appendChild(newRow);
        
}

//--><!]]>
</script>
</head>
<body>
<table id = "table1">
    <tr>
        <td>Washington</td><td>145</td>
    </tr>
    <tr>
        <td>Oregon</td><td>233</td>
    </tr>
    <tr>
        <td>Missouri</td><td>833</td>
    </tr>
</table>
</body>
</html>
``` 

querySelectorAll：return a NodeList containing all of the matching Element nodes within the node’s subtrees, in document order. If there are no such nodes, the method must return an empty NodeList. （按文档顺序返回指定元素节点的子树中匹配选择器的元素集合，如果没有匹配返回空集合）

createElement() 方法可创建元素节点。此方法可返回一个 Element 对象。

createTextNode() 可创建文本节点。此方法可返回 Text 对象。

appendChild() 方法向节点添加最后一个子节点。
提示：如果您需要创建包含文本的新段落，请记得添加到段落的文本的文本节点，然后向文档添加该段落。
您也可以使用 appendChild() 方法从一个元素向另一个元素中移动元素。

