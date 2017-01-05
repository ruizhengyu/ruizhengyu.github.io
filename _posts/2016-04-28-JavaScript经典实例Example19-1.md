---
date: 2016-04-28 22:06:30+00:00
layout: post
title: JavaScript经典实例 示例19-1
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
返回一个XML结果的PHP应用程序
----------------

源码如下：

``` php
<?php
    // 如果没有传递搜索字符串，那么，我们不能搜索
    if (empty($_GET['category'])) {
        $result = "<story><url>none</url><title>No Category Sent</title></story>";
    } else {
        // 从传递的搜索的开始和末尾删除空白
        $search = trim($_GET['category']);
        switch ($search) {
            case "css" :
                $result = "<story><url>http://realtech.burningbird.net/graphics/css/opacity-returns-ie8</url>" .
                    "<title>Opacity returns to IE8</title></story>" .
                    "<story><url>http://realtech.burningbird.net/graphics/css/embedded-fonts-font-face</url>" .
                    "<title>Embedded Fonts with Font Face</title></story>";
                break;
            case "ebooks" :
                $result = "<story><url>http://realtech.burningbird.net/web/ebooks/kindle-clipping-limits</url>" .
                    "<title>Kindle Clipping Limits</title></story>" .
                    "<story><url>http://realtech.burningbird.net/web/ebooks/kindle-and-book-freebies</url>" .
                    "<title>Kindle and Book Freebies</title></story>";
                break;
            case "video" :
                $result = "<story><url>http://secretofsignals.burningbird.net/science/how-things-work/video-online-crap-shoot</url>" .
                    "<title>The Video Online Crap Shoot</title></story>" .
                    "<story><url>http://secretofsignals.burningbird.net/toys-and-technologies/gadgets/review-flip-ultra-camcorder</url>" .
                    "<title>Review of the Flip Ultra Camcorder</title></story>" .
                    "<story><url>http://secretofsignals.burningbird.net/review/movies-disc/gojira</url>" .
                    "<title>Gojira</title></story>" .
                    "<story><url>http://secretofsignals.burningbird.net/review/movies-disc/its-raging-squid</url>" .
                    "<title>It's a Raging Squid</title></story>";
                break;
            case "misssouri" :
                $result = "<story><url>http://misssourigreen.burningbird.net/times-past/misssouri/tyson-valley-lone-elk-and-bomb</url>" .
                    "<title>Tyson Vally, a Lone Elk, and a Bomb</title></story>";
                break;
            default :
                $result = "<story><url>none</url><title>No Stories Found</title></story>";
                break;
        }
    }
    $result = '<?xml version="1.0" encoding="UTF-8" ?>' .
        "<stories>" .$result . "</stories>";
    header("Content-Type: text/xml; charset=utf-8");
    echo $result;
?>
``` 
