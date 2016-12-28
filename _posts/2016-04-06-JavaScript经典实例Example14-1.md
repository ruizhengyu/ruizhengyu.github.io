---
date: 2016-04-06 15:46:30+00:00
layout: post
title: JavaScript经典实例 示例14-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

验证表单字段的时候，提供视觉和其他提示
----------------

<html>
    <head>
        <title>Validating Forms</title>
        <meta charset="utf-8" />
        <style type="text/css">
            [role="alert"]
            {
                background-color: #fcc;
                font-weight: bold;
                padding: 5px;
                border: 1px dashed #000;
            }
            
            div
            {
                margin: 10px 0;
                padding: 5px;
                width: 400px;
                background-color: #fff;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                document.getElementById('thirdfield').onchange = validateField;
                document.getElementById('firstfield').onblur = mandatoryField;
                document.getElementById('testform').onsubmit = finalCheck;
            }
            
            function removeAlert() {
                var msg = document.getElementById('msg');
                
                if (msg) {
                    document.body.removeChild(msg);
                }
            
            }
            
            function resetField(elem) {
                elem.parentNode.setAttribute('style', 'background-color:#fff');
                var valid = elem.getAttribute('aria-invalid');
                
                if (valid) {
                    elem.removeAttribute('aria-invalid');
                }
            
            }
            
            function badField(elem) {
                elem.parentNode.setAttribute('style', 'background-color: #fee');
                elem.setAttribute('aria-invalid', 'true');
            }
            
            function generateAlert(txt) {
                
                // 创建新的文本和div元素，并设置ARIA和类及id
                var txtNd = document.createTextNode(txt);
                
                msg = document.createElement('div');
                msg.setAttribute('role', 'alert');
                msg.setAttribute('id', 'msg');
                msg.setAttribute('class', 'alert');
                
                // 把文本附加到div，把div附加到文档
                msg.appendChild(txtNd);
                document.body.appendChild(msg);
            }
            
            function validateField() {
                
                // 删除任何已有的警告，而不管什么值
                removeAlert();
                
                // 检查数字
                if (!isNaN(parseFloat(this.value))) {
                    resetField(this);
                } else {
                    badField(this);
                    generateAlert("You entered an invalid value in Third Field.Only numeric nalues such as 105 or 3.54 are allowed")
                }
                
            }
            
            function mandatoryField() {
                
                // 删除任何已有的警告
                removeAlert();
                
                // 检查值
                if (this.value.length > 0) {
                    resetField(this);
                } else {
                    badField(this);
                    generateAlert("You must enter a value into First Field");
                }

            }
            
            function finalCheck() {
                removeAlert();
                var fields = document.querySelectorAll("[aria-invalid='true']");
                
                if (fields.length > 0) {
                    generateAlert("You have incorrect fields entries that must be fixed before you can submit this form");
                    return false;
                }
                
            }
            
        </script>
    </head>
    <body>
        <form id="testform">
            <div>
                <label for="firstfield">*First Field:</label><br />
                <input id="firstfield" name="firstfield" type="text" aria-required="true" />
            </div>
            <div>
                <label for="secondfield">Second Field:</label><br />
                <input id="secondfield" name="secondfield" type="text" />
            </div>
            <div>
                <label for="thirdfield">Third Field (numeric):</label><br />
                <input id="thirdfield" name="thirdfield" type="text" />
            </div>
            <div>
                <label for="fourthfield">Fourth Field:</label><br />
                <input id="fourthfield" name="fourthfield" type="text" />
            </div>
            <input type="submit" value="Send Data" />
        </form>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Validating Forms</title>
        <meta charset="utf-8" />
        <style type="text/css">
            [role="alert"]
            {
                background-color: #fcc;
                font-weight: bold;
                padding: 5px;
                border: 1px dashed #000;
            }
            
            div
            {
                margin: 10px 0;
                padding: 5px;
                width: 400px;
                background-color: #fff;
            }
            
        </style>
        <script type="text/javascript">
            window.onload = function() {
                document.getElementById('thirdfield').onchange = validateField;
                document.getElementById('firstfield').onblur = mandatoryField;
                document.getElementById('testform').onsubmit = finalCheck;
            }
            
            function removeAlert() {
                var msg = document.getElementById('msg');
                
                if (msg) {
                    document.body.removeChild(msg);
                }
            
            }
            
            function resetField(elem) {
                elem.parentNode.setAttribute('style', 'background-color:#fff');
                var valid = elem.getAttribute('aria-invalid');
                
                if (valid) {
                    elem.removeAttribute('aria-invalid');
                }
            
            }
            
            function badField(elem) {
                elem.parentNode.setAttribute('style', 'background-color: #fee');
                elem.setAttribute('aria-invalid', 'true');
            }
            
            function generateAlert(txt) {
                
                // 创建新的文本和div元素，并设置ARIA和类及id
                var txtNd = document.createTextNode(txt);
                
                msg = document.createElement('div');
                msg.setAttribute('role', 'alert');
                msg.setAttribute('id', 'msg');
                msg.setAttribute('class', 'alert');
                
                // 把文本附加到div，把div附加到文档
                msg.appendChild(txtNd);
                document.body.appendChild(msg);
            }
            
            function validateField() {
                
                // 删除任何已有的警告，而不管什么值
                removeAlert();
                
                // 检查数字
                if (!isNaN(parseFloat(this.value))) {
                    resetField(this);
                } else {
                    badField(this);
                    generateAlert("You entered an invalid value in Third Field.Only numeric nalues such as 105 or 3.54 are allowed")
                }
                
            }
            
            function mandatoryField() {
                
                // 删除任何已有的警告
                removeAlert();
                
                // 检查值
                if (this.value.length > 0) {
                    resetField(this);
                } else {
                    badField(this);
                    generateAlert("You must enter a value into First Field");
                }

            }
            
            function finalCheck() {
                removeAlert();
                var fields = document.querySelectorAll("[aria-invalid='true']");
                
                if (fields.length > 0) {
                    generateAlert("You have incorrect fields entries that must be fixed before you can submit this form");
                    return false;
                }
                
            }
            
        </script>
    </head>
    <body>
        <form id="testform">
            <div>
                <label for="firstfield">*First Field:</label><br />
                <input id="firstfield" name="firstfield" type="text" aria-required="true" />
            </div>
            <div>
                <label for="secondfield">Second Field:</label><br />
                <input id="secondfield" name="secondfield" type="text" />
            </div>
            <div>
                <label for="thirdfield">Third Field (numeric):</label><br />
                <input id="thirdfield" name="thirdfield" type="text" />
            </div>
            <div>
                <label for="fourthfield">Fourth Field:</label><br />
                <input id="fourthfield" name="fourthfield" type="text" />
            </div>
            <input type="submit" value="Send Data" />
        </form>
    </body>
</html>
``` 
`onblur` 事件会在对象失去焦点时发生。