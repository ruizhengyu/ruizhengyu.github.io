---
date: 2016-04-03 10:46:30+00:00
layout: post
title: JavaScript经典实例 示例13-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

折叠表单元素
----------------

<html>
    <head>
        <title>Collapsed Form Elements</title>
        <meta charset="utf-8" />
        <style type="text/css">
            .label
            {
                width: 400px;
                margin: 10px 0 0 0;
                padding: 10px;
                background-color: #ccf;
                text-align: center;
                border: 1px solid #ccf;
            }
            
            .elements
            {
                border: 1px solid #ccf;
                padding: 10px;
                border: 1px solid #ccf;
                width: 400px;
            }
            
            button
            {
                margin: 20px;
            }
            
        </style>
    </head>
    <body>
        <form>
            <div>
                <div id="section1" class="label">
                    <p>Checkboxes</p>
                </div>
                <div id="section1b" class="elements">
                    <input type="checkbox" name="box1" /> - box one<br />
                    <input type="checkbox" name="box1" /> - box one<br />
                    <input type="checkbox" name="box1" /> - box one<br />
                    <input type="checkbox" name="box1" /> - box one<br />
                    <input type="checkbox" name="box1" /> - box one<br />
                </div>
            </div>
            <div>
                <div id="section2" class="label">
                    <p>Buttons</p>
                </div>
                <div class="elements">
                    <input type="radio" name="button1" /> - box one<br />
                    <input type="radio" name="button1" /> - box one<br />
                    <input type="radio" name="button1" /> - box one<br />
                    <input type="radio" name="button1" /> - box one<br />
                    <input type="radio" name="button1" /> - box one<br />
                    <button>Submit</button>
                </div>
            </div>
        </form>
        <script type="text/javascript">
            var elements = document.getElementsByTagName('div');
            
            // 折叠起所有的区段
            for (var i = 0; i < elements.length; i++) {
                if (elements[i].className === 'elements') {
                    elements[i].style.display = 'none';
                } else if (elements[i].className === 'label') {
                    elements[i].onclick = switchDisplay;
                }
                
            }
            
            // 根据状态折叠或展开
            function switchDisplay() {
                var parent = this.parentNode,
                    target = parent.getElementsByTagName('div')[1];
                
                if (target.style.display === 'none') {
                    target.style.display = 'block';
                } else {
                    target.style.display = 'none';
                }
                
                return false;
            }
            
        </script>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Collapsed Form Elements</title>
        <meta charset="utf-8" />
        <style type="text/css">
            .label
            {
                width: 400px;
                margin: 10px 0 0 0;
                padding: 10px;
                background-color: #ccf;
                text-align: center;
                border: 1px solid #ccf;
            }
            
            .elements
            {
                border: 1px solid #ccf;
                padding: 10px;
                border: 1px solid #ccf;
                width: 400px;
            }
            
            button
            {
                margin: 20px;
            }
            
        </style>
    </head>
    <body>
        <form>
            <div>
                <div id="section1" class="label">
                    <p>Checkboxes</p>
                </div>
                <div id="section1b" class="elements">
                    <input type="checkbox" name="box1" /> - box one<br />
                    <input type="checkbox" name="box1" /> - box one<br />
                    <input type="checkbox" name="box1" /> - box one<br />
                    <input type="checkbox" name="box1" /> - box one<br />
                    <input type="checkbox" name="box1" /> - box one<br />
                </div>
            </div>
            <div>
                <div id="section2" class="label">
                    <p>Buttons</p>
                </div>
                <div class="elements">
                    <input type="radio" name="button1" /> - box one<br />
                    <input type="radio" name="button1" /> - box one<br />
                    <input type="radio" name="button1" /> - box one<br />
                    <input type="radio" name="button1" /> - box one<br />
                    <input type="radio" name="button1" /> - box one<br />
                    <button>Submit</button>
                </div>
            </div>
        </form>
        <script type="text/javascript">
            var elements = document.getElementsByTagName('div');
            
            // 折叠起所有的区段
            for (var i = 0; i < elements.length; i++) {
                if (elements[i].className === 'elements') {
                    elements[i].style.display = 'none';
                } else if (elements[i].className === 'label') {
                    elements[i].onclick = switchDisplay;
                }
                
            }
            
            // 根据状态折叠或展开
            function switchDisplay() {
                var parent = this.parentNode,
                    target = parent.getElementsByTagName('div')[1];
                
                if (target.style.display === 'none') {
                    target.style.display = 'block';
                } else {
                    target.style.display = 'none';
                }
                
                return false;
            }
            
        </script>
    </body>
</html>
``` 
