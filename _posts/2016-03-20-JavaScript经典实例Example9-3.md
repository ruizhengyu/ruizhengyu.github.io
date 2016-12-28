---
date: 2016-03-20 14:26:30+00:00
layout: post
title: JavaScript经典实例 示例9-3
categories: JavaScript经典实例
tags:  JavaScript  JavaScript经典实例
---

填充一个选项列表
----------------

<html xmlns="http://www.w3.org/1999/xthml">
<head>
<title>Populating Selection Lists</title>
<script>
//<![CDTAT[

var citystore = new Array();
citystore[0] = ['CA', 'San Francisco'];
citystore[1] = ['CA', 'Los Angeles'];
citystore[2] = ['CA', 'San Diego'];
citystore[3] = ['MO', 'St. louis'];
citystore[4] = ['MO', 'Kansas City'];
citystore[5] = ['WA', 'Seattle'];
citystore[6] = ['WA', 'Spokane'];
citystore[7] = ['WA', 'Redmond'];

window.onload = function(){
    document.getElementById("state").onchange = filterCities;
}

function filterCities(){
    var state = this.value;
    var city = document.getElementById("cities");
    city.options.length = 0;
    
    for(var i = 0; i < citystore.length; i++){
        var st = citystore[i][0];
        if(st == state){
            var opt = new Option(citystore[i][1]);
            try{
                city.add(opt, null);
            }catch(e){
                city.add(opt);
            }
        }
    }
}

//--><!]]>
</script>
</head>
<body>
<form id="picker" method="post" action="">
<select id="state">
<option value="">--</option>
<option value="MO">Missouri</option>
<option value="WA">Washington</option>
<option value="CA">California</option>
</select>
<select id="cities">
</select>
</form>
</body>
</html>

源码如下：

``` html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xthml">
<head>
<title>Populating Selection Lists</title>
<script>
//<![CDTAT[

var citystore = new Array();
citystore[0] = ['CA', 'San Francisco'];
citystore[1] = ['CA', 'Los Angeles'];
citystore[2] = ['CA', 'San Diego'];
citystore[3] = ['MO', 'St. louis'];
citystore[4] = ['MO', 'Kansas City'];
citystore[5] = ['WA', 'Seattle'];
citystore[6] = ['WA', 'Spokane'];
citystore[7] = ['WA', 'Redmond'];

window.onload = function(){
    document.getElementById("state").onchange = filterCities;
}

function filterCities(){
    var state = this.value;
    var city = document.getElementById("cities");
    city.options.length = 0;
    
    for(var i = 0; i < citystore.length; i++){
        var st = citystore[i][0];
        if(st == state){
            var opt = new Option(citystore[i][1]);
            try{
                city.add(opt, null);
            }catch(e){
                city.add(opt);
            }
        }
    }
}

//--><!]]>
</script>
</head>
<body>
<form id="picker" method="post" action="">
<select id="state">
<option value="">--</option>
<option value="MO">Missouri</option>
<option value="WA">Washington</option>
<option value="CA">California</option>
</select>
<select id="cities">
</select>
</form>
</body>
</html>
``` 
