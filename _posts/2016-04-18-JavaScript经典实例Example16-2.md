---
date: 2016-04-18 15:46:30+00:00
layout: post
title: JavaScript经典实例 示例16-2
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
展示JavaScript中的对象继承
----------------

<html>
    <head>
        <title>Constructor Chaining</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
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
                
                // 链化该对象的构造函数
                TechBook.prototype = new Book();
                
                // 获取所有的值
                var newBook = new TechBook('The JavaScript Cookbook', 'Shelley Powers', 'Programming');
                
                document.getElementById("result1").innerHTML = newBook.getBook();
                
                // 现在，逐个显示
                document.getElementById("result2").innerHTML = newBook.getTitle();
                document.getElementById("result3").innerHTML = newBook.getAuthor();
                document.getElementById("result4").innerHTML = newBook.getCategory();
            }
        </script>
    </head>
    <body>
        <p>some content</p>
        <div id="result1"></div>
        <div id="result2"></div>
        <div id="result3"></div>
        <div id="result4"></div>
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
                
                // 链化该对象的构造函数
                TechBook.prototype = new Book();
                
                // 获取所有的值
                var newBook = new TechBook('The JavaScript Cookbook', 'Shelley Powers', 'Programming');
                
                alert(newBook.getBook());
                
                // 现在，逐个显示
                alert(newBook.getTitle());
                alert(newBook.getAuthor());
                alert(newBook.getCategory());
            }
        </script>
    </head>
    <body>
        <p>some content</p>
    </body>
</html>
``` 
