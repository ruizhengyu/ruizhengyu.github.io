---
date: 2016-04-19 20:16:30+00:00
layout: post
title: JavaScript经典实例 示例16-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
尝试新的对象属性方法
----------------

<html>
    <head>
        <title>Constructor Chaining</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
            
            // Book定制对象
            function Book(title, author) {
                var title = title,
                    author = author;
                
                this.getTitle = function() {
                    return 'Title: ' + title;
                }
                
                this.getAuthor = function() {
                    return 'Author: ' + author;
                }
                
            }
            
            // TechBook继承自Book
            function TechBook(title, author, category) {
                var category = category;
                
                this.getCategory = function() {
                    return 'Technical Category: ' + category;
                }
                
                Book.apply(this, arguments);
                this.getBook = function() {
                    return this.getTitle() + ' ' + author + ' ' + this.getCategory();
                }
                
            }
            
            window.onload = function() {
                try {
                    
                    // DOM 测试，Webkit在这里一败涂地
                    var img = new Image();
                    
                    // 添加新的属性和描述符
                    Object.defineProperty(img, 'geolatitude',{
                        get: function() { return geolatitude; },
                        set: function(val) { geolatitude = val; },
                        enumerable: true,
                        configurable: true
                    });
                    
                    // 测试configurable和enumerable属性
                    var props = 'Image has ';
                    
                    for (var prop in img) {
                        props += prop + ' ';
                    }
                    document.getElementById("result1").innerHTML = props;
                } catch(e) {
                    document.getElementById("result2").innerHTML = e;
                }
                
                try {
                
                    // 现在，我们在IE8中失败
                    
                    // 链化对象构造函数
                    TechBook.prototype = new Book();
                    
                    // 添加新的属性和属性描述符
                    Object.defineProperty(TechBook, 'experience',{
                        get: function() { return category; },
                        set: function(value) { category = value; },
                        enumerable: false,
                        configurable: true
                    });
                    
                    // 获取属性描述符并打印
                    var val = Object.getOwnPropertyDescriptor(TechBook, 'experience');
                    document.getElementById("result3").innerHTML = JSON.stringify(val);
                    
                    // 测试configurable和enumerable属性
                    var props = 'Image has ';
                    
                    for (var prop in TechBook) {
                        props += prop + ' ';
                    }
                    
                    document.getElementById("result4").innerHTML = props;
                    Object.defineProperty(TechBook, 'experience',{
                        enumerable: true
                    });
                    props = 'TechBook now has ';
                    for (var prop in TechBook) {
                        props += prop + ' ';
                    }
                    
                    document.getElementById("result5").innerHTML = props;
                    
                    // 创建TechBook实例
                    var newBook = new TechBook('The JavaScript Cookbook', 'Shelley Powers', 'Programming');
                    
                    // 测试新的setter
                    newBook.experience = 'intermediate';
                    
                    // 测试数据描述符
                    Object.defineProperty(newBook, 'publisher',{
                        value: "O'Reilly",
                        writable: false,
                        enumerable: true,
                        configurable: true
                    });
                    
                    // 测试writable
                    newBook.publisher = 'Some Other';
                    document.getElementById("result6").innerHTML = newBook.publisher;
                } catch(e) {
                    document.getElementById("result7").innerHTML = e;
                }
                
            }
        </script>
    </head>
    <body>
        <p>some content</p>
        <div id="result1"></div>
        <div id="result2"></div>
        <div id="result3"></div>
        <div id="result4"></div>
        <div id="result5"></div>
        <div id="result6"></div>
        <div id="result7"></div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Constructor Chaining</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
            
            // Book定制对象
            function Book(title, author) {
                var title = title,
                    author = author;
                
                this.getTitle = function() {
                    return 'Title: ' + title;
                }
                
                this.getAuthor = function() {
                    return 'Author: ' + author;
                }
                
            }
            
            // TechBook继承自Book
            function TechBook(title, author, category) {
                var category = category;
                
                this.getCategory = function() {
                    return 'Technical Category: ' + category;
                }
                
                Book.apply(this, arguments);
                this.getBook = function() {
                    return this.getTitle() + ' ' + author + ' ' + this.getCategory();
                }
                
            }
            
            window.onload = function() {
                try {
                    
                    // DOM 测试，Webkit在这里一败涂地
                    var img = new Image();
                    
                    // 添加新的属性和描述符
                    Object.defineProperty(img, 'geolatitude',{
                        get: function() { return geolatitude; },
                        set: function(val) { geolatitude = val; },
                        enumerable: true,
                        configurable: true
                    });
                    
                    // 测试configurable和enumerable属性
                    var props = 'Image has ';
                    
                    for (var prop in img) {
                        props += prop + ' ';
                    }
                    
                    alert(props);
                } catch(e) {
                    alert(e);
                }
                
                try {
                
                    // 现在，我们在IE8中失败
                    
                    // 链化对象构造函数
                    TechBook.prototype = new Book();
                    
                    // 添加新的属性和属性描述符
                    Object.defineProperty(TechBook, 'experience',{
                        get: function() { return category; },
                        set: function(value) { category = value; },
                        enumerable: false,
                        configurable: true
                    });
                    
                    // 获取属性描述符并打印
                    var val = Object.getOwnPropertyDescriptor(TechBook, 'experience');
                    alert(JSON.stringify(val));
                    
                    // 测试configurable和enumerable属性
                    var props = 'Image has ';
                    
                    for (var prop in TechBook) {
                        props += prop + ' ';
                    }
                    
                    alert(props);
                    Object.defineProperty(TechBook, 'experience',{
                        enumerable: true
                    });
                    props = 'TechBook now has ';
                    for (var prop in TechBook) {
                        props += prop + ' ';
                    }
                    
                    alert(props);
                    
                    // 创建TechBook实例
                    var newBook = new TechBook('The JavaScript Cookbook', 'Shelley Powers', 'Programming');
                    
                    // 测试新的setter
                    newBook.experience = 'intermediate';
                    
                    // 测试数据描述符
                    Object.defineProperty(newBook, 'publisher',{
                        value: "O'Reilly",
                        writable: false,
                        enumerable: true,
                        configurable: true
                    });
                    
                    // 测试writable
                    newBook.publisher = 'Some Other';
                    alert(newBook.publisher);
                } catch(e) {
                    alert(e);
                }
                
            }
        </script>
    </head>
    <body>
        <p>some content</p>
    </body>
</html>
``` 
