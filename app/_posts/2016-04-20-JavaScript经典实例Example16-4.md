---
date: 2016-04-20 13:46:30+00:00
layout: post
title: JavaScript经典实例 示例16-4
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
Function.bind用于定时器的用法展示
----------------

<html>
    <head>
        <title>Using bind with timers</title>
        <meta http-equiv="Content-Type" content="text/html" charset="utf-8" />
        <style type="text/css">
            #item
            {
                font-size: 72px;
                margin: 70px auto;
                width: 100px;
            }
            
        </style>
        <script type="text/javascript">
            if (!Function.bind) {
                Function.prototype.bind = function(scope) {
                    var _function = this;
                    
                    return function() {
                        return _function.apply(scope, arguments);
                    }
                    
                }
                
            }
            
            window.onload = function() {
                var theCounter = new Counter('item', 10, 0);
                
                theCounter.countDown();
            }
            
            function Counter(id, start, finish) {
                this.count = this.start = start;
                this.finish = finish;
                this.id = id;
                this.countDown = function() {
                    if (this.count == this.finish) {
                        this.countDown = null;
                        return;
                    }
                    
                    document.getElementById(this.id).innerHTML = this.count--;
                    setTimeout(this.countDown.bind(this), 1000);
                }
                
            }
        </script>
    </head>
    <body>
        <div id="item">
            10
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Using bind with timers</title>
        <meta http-equiv="Content-Type" content="text/html" charset="utf-8" />
        <style type="text/css">
            #item
            {
                font-size: 72px;
                margin: 70px auto;
                width: 100px;
            }
            
        </style>
        <script type="text/javascript">
            if (!Function.bind) {
                Function.prototype.bind = function(scope) {
                    var _function = this;
                    
                    return function() {
                        return _function.apply(scope, arguments);
                    }
                    
                }
                
            }
            
            window.onload = function() {
                var theCounter = new Counter('item', 10, 0);
                
                theCounter.countDown();
            }
            
            function Counter(id, start, finish) {
                this.count = this.start = start;
                this.finish = finish;
                this.id = id;
                this.countDown = function() {
                    if (this.count == this.finish) {
                        this.countDown = null;
                        return;
                    }
                    
                    document.getElementById(this.id).innerHTML = this.count--;
                    setTimeout(this.countDown.bind(this), 1000);
                }
                
            }
        </script>
    </head>
    <body>
        <div id="item">
            10
        </div>
    </body>
</html>
``` 
