---
title: '[freeCodeCamp学习笔记-产品落地页实战与面向对象编程]'
date: 2020-05-03 22:36:51
tags: freeCodeCamp CSS 原型链
---
##### 背景
这是freeCodeCamp学习笔记第二篇。今天主要学习了两块内容：
1. [响应式网站设计项目实战：产品落地页](https://learn.freecodecamp.one/responsive-web-design/responsive-web-design-projects/build-a-product-landing-page)
2. [算法和数据结构：面向对象编程](https://learn.freecodecamp.one/javascript-algorithms-and-data-structures/object-oriented-programming)
##### 产品落地页（CSS)
[这是项目完成后的链接，欢迎大神拷打。](https://codepen.io/focusfirst/pen/QWjONrX)落地页主要涉及的知识点为CSS中的flex布局和媒体查询的使用（media)。

项目总体结构为`header => content => footer`。其中`header`部分包含公司logo以及导航栏。`header` 使用  `fixed` 定位方式，当页面长度较长时使用scroll时，确保`header` 内容保留在屏幕上方，使用`flex`布局，以实现当页面宽度变化时，导航栏部分wrap到第二行。导航栏包含三部分,使用flex布局，添加媒体查询使flex布局方向由横向改为纵向。
***这里需要注意媒体查询语句要放在默认语句之后，不然媒体查询语句会被默认语句覆盖导致失效。***
```
@media (max-width:650px) {
  #nav-bar > ul {
    flex-direction: column;
    align-items: center;
  }
}
```
在写提交表单的按钮时，为了做一个input:hover的效果，刚开始直接写成了`.btn:hover`，但是没有生效。后来查到了stackoverflow上的一个[问答](https://stackoverflow.com/questions/38201279/how-to-set-css-hover-on-input/38201456)了解到，要写成这样的方式：`#hero input[type="submit"].btn:hover`。至于为什么这么写还没有找到比较好的解释，难道是为了强调CSS中层叠？这个希望在后边深入到css中能够找到答案。
```
  <input type="submit" value="GET STARTED" class="btn"/>
```
在写`pricing`模块时同样用到了flex布局以及媒体查询，使视口宽度较小时能够改为单列布局。

通过实践本项目主要收获为：

1. 熟悉了布局常用属性的使用以及其在响应式布局中的巨大威力。
2. 熟悉了媒体查询(`media`)方式的使用以及用来做响应式布局的实战。
3. `HTML5`中 `video`标签的使用。

##### JavaScript面向对象编程
1. 通过freeCodeCamp的一些小练习，理解了JavaScript中实现面向对象编程的方式：**原型及原型链**.
2. 了解了什么事Mixin，如何实现Mixin。
3. 了解了什么闭包，闭包有什么实际作用（保护对象的私有属性，在构造函数内部定义局部变量）
4. 复习了IIFE，IIFE（闭包）与Mixin结合将相关功能分组到单个对象或者模块中（在实战还未用到，期待...)。