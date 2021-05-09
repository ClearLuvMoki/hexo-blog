---
title: '改变元素显示'
date: 2020-04-02 19:47
updated: 2020-04-02 19:47
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### 改变元素显示

##### display

>常见的块级元素
>
>​	div, p, h1-h6, table, form, ol, ul
>
>常见的行内元素
>
>​	span, strong, em, a, input, label, imp, br, select

<ol>
  <li>值： none, inline, block, inline-block, list-item, run-in, table, inline-table, table-row-group,
  			table-header-group, table-footer-group, table-row, table-cloumn-group, table-column, table-cell,
    		table-caption, inherit
  </li>
  <li>初始值： inline</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 无</li>
</ol>

##### 改变角色

>display: block;
>
>​	1.	将元素变成块级元素；
>
>​	2.	block元素会独占一行；
>
>​	3.	可以设置width和height；
>
>​	4.	block元素可以设置margin和padding的所有属性；
>
>​	<code>a { display: block; }</code>
>
>display: inline; 
>
>​	1.	将元素变成行内元素；
>
>​	2.	inline元素设置width,height属性无效；
>
>​	3.	inline元素的margin和padding属性，水平方向的padding-left, padding-right, margin-left, margin-right都产生边距效果；但竖	直方向的padding-top, padding-bottom, margin-top, margin-bottom不会产生边距效果。
>
>​	a  { display: inline; }

##### 行内块元素 --- inline-block

>inline-block
>
> 1. 将元素设置成该值，可以即继承行内属性又有块级属性；
>
> 2. 简单来说就是将对象呈现为inline对象，但是对象的内容作为block对象呈现。
>
>    比如我们可以给一个link（a元素）inline-block属性值，使其既具有block的宽度高度特性又具有inline的同行特性。

