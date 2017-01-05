---
date: 2016-03-02 16:04:30+00:00
layout: post
title: JavaScript经典实例 示例2-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

匹配正则表达式字符的正则表达式
----------------

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Replacement Insanity</title>
        <script>
        //<![CDATA[
            window.onload=function() {
                
                // 查找 \d
                var re = /\\d/,
                    pattern = "\\d{4}",
                    str = "I want 1111 to find 3334 certain 5343 things 8484",
                    re2 = new RegExp(pattern,"g"),
                    str1 = str.replace(re2,"****");
                    
                document.getElementById('result1').innerHTML = str1;
                var pattern2 = pattern.replace(re,"\\D"),
                    re3 = new RegExp(pattern2,"g"),
                    str2 = str.replace(re3, "****");
                    
                document.getElementById('result1').innerHTML = str2;
            }
        //--><!]]>
        </script>
    </head>
    <body>
        <p>content</p>
        <p id="result1"></p>
        <p id="result2"></p>
    </body>
</html>


源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Replacement Insanity</title>
        <script>
        //<![CDATA[
            window.onload=function() {
                
                // 查找 \d
                var re = /\\d/,
                    pattern = "\\d{4}",
                    str = "I want 1111 to find 3334 certain 5343 things 8484",
                    re2 = new RegExp(pattern,"g"),
                    str1 = str.replace(re2,"****");
                    
                alert(str1);
                var pattern2 = pattern.replace(re,"\\D"),
                    re3 = new RegExp(pattern2,"g"),
                    str2 = str.replace(re3, "****");
                    
                alert(str2);
            }
        //--><!]]>
        </script>
    </head>
    <body>
        <p>content</p>
    </body>
</html>
``` 