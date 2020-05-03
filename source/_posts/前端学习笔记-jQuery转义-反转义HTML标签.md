---
title: 前端学习笔记-jQuery转义/反转义HTML标签
date: 2020-04-27 23:02:02
tags: jQuery 前端 JavaScript
---
##### 1. jQuery转义HTML标签

```
$('<span>').text('<p>').html() // &lt;p&gt;
```
其中 `&lt`; 为 <；`&gt;`为 >

##### 2.jQuery转义HTML标签
```
$('<span>').html('&lt;p&gt;').text() // <P>
```

##### 3. 注意事项
在通过 `$('div').html() `向 DOM 插入HTML代码时，通常是需要插入非转义的代码。但因为在项目中，后端返回的HTML代码是经过转义的代码，这时就需要使用 
```
let htmoCode = $('<span>').html('需要反转义的代码').text()
```
反转义到的HTML标签字符串，然后再使用
```
$('div'>.html(htmoCode)
```
插入DOM。
##### 4. 后记
来自于某财富官网项目总结经验。