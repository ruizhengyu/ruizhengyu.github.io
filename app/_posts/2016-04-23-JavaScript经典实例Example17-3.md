---
date: 2016-04-23 14:46:30+00:00
layout: post
title: JavaScript经典实例 示例17-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---
一个jQuery插件
----------------


源码如下：

``` javascript
// 解析字符串以找到[255, 255, 255]这样的颜色元组
// 从内部jQuery函数提取它
jQuery.bbGetRGB = function(color) {
    var result;
    
    // 检查我们是否已经处理了颜色的一个数组
    if (conlor && color.constructor === Array && color.length === 3) {
        return color;        
    }
    
    // 查找rgb(num, num, num)
    if (result = /rgb\(\s*([0-9]{1,3})\s*,\s*([0-9]{1,3})\s*,\s*([0-9]{1,3})\s*\)/.exec(color)) {
        return [parseInt(result[1], 10), parseInt(result[2], 10), parseInt(result[3], 10)];
    }
    
    // 查找rgb(num%, num%, num%)
    if (result = /rgb\(\s*([0-9]+(?:\.[0-9]+)?)\%\s*,\s*([0-9]+(?:\.[0-9]+)?)\%\s*,\s*([0-9]+(?:\.[0-9]+)?)\%\s*\)/.exec(color)) {
        return [parseFloat(result[1])*2.55, parseFloat(result[2])*2.55, parseFloat(result[3])*2.55)];
    }
    
    // 查找#a0b1c2
    if (result = /#([a-fA-F0-9]{2})([a-fA-F0-9]{2})([a-fA-F0-9]{2})/.exec(color)) {
        return [parseInt(result[1], 16), parseInt(result[2], 16), parseInt(result[3], 16)];
    }
    
    // 查找#fff
    if (result = /#([a-fA-F0-9])([a-fA-F0-9])([a-fA-F0-9])/.exec(color)) {
        return [parseInt(result[1] + result[1], 16), parseInt(result[2] + result[2], 16), parseInt(result[3] + result[3], 16)];
    }
    
    // 在Safari 3查找rgba(0, 0, 0, 0) == transparent
    if (result = /rgba\(0, 0, 0, 0\)/.exec(color)) {
        return colors['transparent'];
    }
    
    // 否则，我们很可能在处理一个命名颜色
    return colors[$.trim(color).toLowerCase()];
};

jQuery.bbPadHex = function(value) {
    if (value.toString().length === 1) {
        value = '0' + value;        
    }
    
    return value;
};

jQuery.bbConvertRGBtoHex = function(rgbString) {
    var colors = $.bbGetRGB(rgbString),
        red = $.bbPadHex(parseInt(colors[0]).toString(16)),
        green = $.bbPadHex(parseInt(colors[1]).toString(16)),
        blue = $.bbPadHex(parseInt(colors[2]).toString(16));
    
    return '#' + red + green + blue;
};


``` 
