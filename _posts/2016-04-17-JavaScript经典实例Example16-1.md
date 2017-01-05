---
date: 2016-04-17 15:16:30+00:00
layout: post
title: JavaScript经典实例 示例16-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
实例化一个新的对象，相加其值，并扩展该对象
----------------

<html>
    <head>
        <title>Tune Object</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
            function Tune(song, artist) {
                var title = song,
                    artist = artist;
                    
                this.concat = function() {
                    return title + ' ' + artist;
                }
                
            }
            
            window.onload = function() {
                
                // 创建实例，打印出值
                var happySong = new Tune('Putting on the Ritz', 'Ella Fitzgerald');
                
                // 扩展该对象
                Tune.prototype.addCategory = function(categoryName) {
                    this.category = categoryName;
                }
                
                // 添加分类
                happySong.addCategory('Swing');
                
                // 把歌曲打印到一个新的段落
                var song = 'Title and artist: ' + happySong.concat() + ' Category: ' + happySong.category,
                    p = document.createElement('p'),
                    txt = document.createTextNode(song);
                    
                p.appendChild(txt);
                document.getElementById('song').appendChild(p);
            }
        </script>
    </head>
    <body>
        <h1>Tune</h1>
        <div id="song">
        </div>
    </body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Tune Object</title>
        <meta charset="utf-8" />
        <script type="text/javascript">
            function Tune(song, artist) {
                var title = song,
                    artist = artist;
                    
                this.concat = function() {
                    return title + ' ' + artist;
                }
                
            }
            
            window.onload = function() {
                
                // 创建实例，打印出值
                var happySong = new Tune('Putting on the Ritz', 'Ella Fitzgerald');
                
                // 扩展该对象
                Tune.prototype.addCategory = function(categoryName) {
                    this.category = categoryName;
                }
                
                // 添加分类
                happySong.addCategory('Swing');
                
                // 把歌曲打印到一个新的段落
                var song = 'Title and artist: ' + happySong.concat() + ' Category: ' + happySong.category,
                    p = document.createElement('p'),
                    txt = document.createTextNode(song);
                    
                p.appendChild(txt);
                document.getElementById('song').appendChild(p);
            }
        </script>
    </head>
    <body>
        <h1>Tune</h1>
        <div id="song">
        </div>
    </body>
</html>
``` 
