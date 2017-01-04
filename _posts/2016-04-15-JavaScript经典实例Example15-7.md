---
date: 2016-04-15 21:26:30+00:00
layout: post
title: JavaScript经典实例 示例15-7
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

非常基本的时钟方法，只需要进一步美化
----------------

<html>
    <?xml version="1.0"?>
    <svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 3 3">
        <defs>
            <style type="text/css">
                path
                {
                    stroke: black;
                    stroke-width: 0.02;
                    fill: none;
                }
                
                line
                {
                    stroke-linecap: round;
                }
                
                #seconds
                {
                    stroke: red;
                    stroke-width: 0.01;
                }
                
                #minutes
                {
                    stroke: black;
                    stroke-width: 0.03;
                }
                
                #hours
                {
                    stroke: black;
                    stroke-width: 0.03;
                }
                
            </style>
        </defs>
        <g transform="rotate(-90) translate(-1.3, 1.3)">
            <circle cx="0" cy="0" r="1.0" fill="white" />
            <line id="hours" x1="0" y1="0" x2="0.70" y2="0" stroke-width="1" />
            <line id="minutes" x1="0" y1="0" x2="0.85" y2="0" />
            <line id="seconds" x1="0" y1="0" x2="0.90" y2="0" />
        </g>
        <script>
            var seconds = document.getElementById('seconds'),
                minutes = document.getElementById('minutes'),
                hours = document.getElementById('hours');
                
            function setClock(date) {
                var s = (date.getSeconds() + date.getMilliseconds() / 1000) * Math.PI / 30,
                    m = date.getMinutes() * Math.PI / 30 + s / 60,
                    h = date.getHours() * Math.PI / 6 + m / 12;
                
                seconds.setAttribute('x2', 0.90 * Math.cos(s));
                seconds.setAttribute('y2', 0.90 * Math.sin(s));
                minutes.setAttribute('x2', 0.65 * Math.cos(m));
                minutes.setAttribute('y2', 0.65 * Math.sin(m));
                hours.setAttribute('x2', 0.40 * Math.cos(h));
                hours.setAttribute('y2', 0.40 * Math.sin(h));
            }
            
            setInterval('setClock(new Date())', 1000);
        </script>
    </svg>
</html>
    
源码如下：

``` html
<?xml version="1.0"?>
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 3 3">
    <defs>
        <style type="text/css">
            path
            {
                stroke: black;
                stroke-width: 0.02;
                fill: none;
            }
            
            line
            {
                stroke-linecap: round;
            }
            
            #seconds
            {
                stroke: red;
                stroke-width: 0.01;
            }
            
            #minutes
            {
                stroke: black;
                stroke-width: 0.03;
            }
            
            #hours
            {
                stroke: black;
                stroke-width: 0.03;
            }
            
        </style>
    </defs>
    <g transform="rotate(-90) translate(-1.3, 1.3)">
        <circle cx="0" cy="0" r="1.0" fill="white" />
        <line id="hours" x1="0" y1="0" x2="0.70" y2="0" stroke-width="1" />
        <line id="minutes" x1="0" y1="0" x2="0.85" y2="0" />
        <line id="seconds" x1="0" y1="0" x2="0.90" y2="0" />
    </g>
    <script>
        var seconds = document.getElementById('seconds'),
            minutes = document.getElementById('minutes'),
            hours = document.getElementById('hours');
            
        function setClock(date) {
            var s = (date.getSeconds() + date.getMilliseconds() / 1000) * Math.PI / 30,
                m = date.getMinutes() * Math.PI / 30 + s / 60,
                h = date.getHours() * Math.PI / 6 + m / 12;
            
            seconds.setAttribute('x2', 0.90 * Math.cos(s));
            seconds.setAttribute('y2', 0.90 * Math.sin(s));
            minutes.setAttribute('x2', 0.65 * Math.cos(m));
            minutes.setAttribute('y2', 0.65 * Math.sin(m));
            hours.setAttribute('x2', 0.40 * Math.cos(h));
            hours.setAttribute('y2', 0.40 * Math.sin(h));
        }
        
        setInterval('setClock(new Date())', 1000);
    </script>
</svg>
``` 
