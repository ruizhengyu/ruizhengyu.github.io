---
date: 2016-04-30 15:56:30+00:00
layout: post
title: JavaScript经典实例 示例19-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
提取页面中的微格式活动，并将它们用图表展示在一个画布线条图中
----------------

<html>
    <head>
        <title>Microformats</title>
        <script type="text/javascript">
            window.onload = function() {
                var events = document.querySelectorAll('[class="vevent"]'),
                    v = events,
                    days = new Array();
                
                for (var i = 0; i < events.length; i++) {
                    var dstart = events[i].querySelectorAll('[class="dtstart"]'),
                        dt;
                    
                    if (dstart[0].tagName === 'SPAN') {
                        if (dstart[0].textContent) {
                            dt = dstart[0].textContent;
                        } else {
                            dt = dstart[0].innerText;
                        }
                    } else if (dstart[0].tagName === 'ABBR') {
                        dt = dstart[0].title;
                    }
                    
                    var day = parseInt(dt.split('-')[2]);
                    
                    days.push(day);
                }
                
                var ctx = document.getElementById('calendar').getContext('2d');
                
                // 绘制
                days.sort(function(a, b) {return a - b});
                ctx.fillStyle = 'red';
                ctx.strokeStyle = 'black';
                ctx.beginPath();
                ctx.moveTo(0, 100);
                ctx.lineTo(280, 100);
                ctx.stroke();
                
                for (var i = 0; i < days.length; i++) {
                    var x1 = days[i] * 10,
                        t1 = 70,
                        x2 = 5,
                        t2 = 30;
                    ctx.fillRect(x1, t1, x2, t2);
                }
                
            }
            
        </script>
    </head>
    <body>
        <div>
            <p>
                <span class="vevent">
                    <span class="summary">Monkey Play Time</span>
                    on <span class="dtstart">2010-02-05</span>
                    at <span class="location">St. Louis Zoo</span>
                </span>
            </p>
        </div>
        <div class="vevent">
            <abbr class="dtstart" title="2010-02-25">February 25th</abbr>
            <abbr class="dtend" title="2010-02-26"> 2010</abbr>
            <span class="summary">Event</span>
        </div>
        <p>
            <span class="vevent">
                <span class="summary">Tiger Feeding</span>
                on <span class="dtstart">2010-02-10</span>
                at <span class="location">St. Louis Zoo</span>
            </span>
        </p>
        <p>
            <span class="vevent">
                <span class="summary">Penguin Swimming</span>
                on <span class="dtstart">2010-02-10</span>
                at <span class="location">St. Louis Zoo</span>
            </span>
        </p>
        <div class="vevent">
            <abbr class="dtstart" title="2010-02-19">February 19th</abbr>
            <abbr class="dtend" title="2010-02-26"> 2010</abbr>
            <span class="summary">Sea Lion Show</span>
        </div>
        <canvas id="calendar" style="width: 600px; height: 100px; margin: 10px;">
            <p>Dates</p>
        </canvas>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Microformats</title>
        <script type="text/javascript">
            window.onload = function() {
                var events = document.querySelectorAll('[class="vevent"]'),
                    v = events,
                    days = new Array();
                
                for (var i = 0; i < events.length; i++) {
                    var dstart = events[i].querySelectorAll('[class="dtstart"]'),
                        dt;
                    
                    if (dstart[0].tagName === 'SPAN') {
                        if (dstart[0].textContent) {
                            dt = dstart[0].textContent;
                        } else {
                            dt = dstart[0].innerText;
                        }
                    } else if (dstart[0].tagName === 'ABBR') {
                        dt = dstart[0].title;
                    }
                    
                    var day = parseInt(dt.split('-')[2]);
                    
                    days.push(day);
                }
                
                var ctx = document.getElementById('calendar').getContext('2d');
                
                // 绘制
                days.sort(function(a, b) {return a - b});
                ctx.fillStyle = 'red';
                ctx.strokeStyle = 'black';
                ctx.beginPath();
                ctx.moveTo(0, 100);
                ctx.lineTo(280, 100);
                ctx.stroke();
                
                for (var i = 0; i < days.length; i++) {
                    var x1 = days[i] * 10,
                        t1 = 70,
                        x2 = 5,
                        t2 = 30;
                    ctx.fillRect(x1, t1, x2, t2);
                }
                
            }
            
        </script>
    </head>
    <body>
        <div>
            <p>
                <span class="vevent">
                    <span class="summary">Monkey Play Time</span>
                    on <span class="dtstart">2010-02-05</span>
                    at <span class="location">St. Louis Zoo</span>
                </span>
            </p>
        </div>
        <div class="vevent">
            <abbr class="dtstart" title="2010-02-25">February 25th</abbr>
            <abbr class="dtend" title="2010-02-26"> 2010</abbr>
            <span class="summary">Event</span>
        </div>
        <p>
            <span class="vevent">
                <span class="summary">Tiger Feeding</span>
                on <span class="dtstart">2010-02-10</span>
                at <span class="location">St. Louis Zoo</span>
            </span>
        </p>
        <p>
            <span class="vevent">
                <span class="summary">Penguin Swimming</span>
                on <span class="dtstart">2010-02-10</span>
                at <span class="location">St. Louis Zoo</span>
            </span>
        </p>
        <div class="vevent">
            <abbr class="dtstart" title="2010-02-19">February 19th</abbr>
            <abbr class="dtend" title="2010-02-26"> 2010</abbr>
            <span class="summary">Sea Lion Show</span>
        </div>
        <canvas id="calendar" style="width: 600px; height: 100px; margin: 10px;">
            <p>Dates</p>
        </canvas>
    </body>
</html>
``` 
