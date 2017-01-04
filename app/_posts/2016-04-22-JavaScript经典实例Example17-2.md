---
date: 2016-04-22 14:46:30+00:00
layout: post
title: JavaScript经典实例 示例17-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
测试示例17-1中的对象的方法的JsUnit测试页面
----------------
运行结果如下图
[![ ](/assets/media/image/Example 17-2.png)](/assets/media/image/Example 17-2.png)

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Testing Library</title>
        <meta charset="utf-8" />
        <script src="jsunit/app/jsUnitCore.js"></script>
        <script src="test.js"></script>
        <script type="text/javascript">
            function testConcatWithSpace() {
                inform('Testing concatWithSpace');
                assertEquals('Checking equality', 'Shelley Powers', BBTest.concatWithSpace('Shelley', 'Powers'));
            }
            
            function testDiscoverNumber() {
                inform('Testing discoverNumber');
                assertEquals('Checking valid params', 5, BBTest.discoverNumber('found5value', 5));
            }
            
            function testDivideNumbers() {
                inform('Testing divideNumbers');
                assertNaN('Checking numeric ops with no numbers', BBTest.divideNumbers('five', '2'));
                assertNotEquals('Checking no euqals', '5', BBTest.divideNumbers(10, 2));
            }
            
            function testAddAndRound() {
                inform('Testing addAndRound');
                assertNaN('Checking NaN', BBTest.addAndRound('four', 'Three Quarter'));
                assertEquals('Checking correct values', 6, BBTest.addAndRound(2.33, 3.45));
            }
        </script>
    </head>
    <body>
        <p>Running tests of test.js. View source to see tests.
    </body>
</html>
``` 

JUnit测试软件下载：[下载地址](/assets/media/image/jsunit2_2.zip)
