---
title: '基本元素框'
date: 2020-04-02 21:03
updated: 2020-04-02 21:03
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### 基本元素框

##### 宽度和高度

<p>一个元素的<code>wdith</code>定义是左内边界到右内边界的距离；<code>height</code>定义的事上内边界到下内边界的距离。</p>

<p>⚠️： 这个高度和宽度不能用到行内非替换元素中！！行内非替换元素的宽度与高度与其内容有关！！</p>

![](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/CSSElementBox.png)

<ol>
  width
  <li>值： [length], [percentage（百分数）], inherit, auto</li>
  <li>初始值： auto</li>
  <li>应用于： 块级元素和替换元素</li>
  <li>继承性： 无</li>
  <li>百分数： 相对于包含块级元素的宽度</li>
</ol>

<ol>
  height
  <li>值： [length], [percentage（百分数）], inherit, auto</li>
  <li>初始值： auto</li>
  <li>应用于： 块级元素和替换元素</li>
  <li>继承性： 无</li>
  <li>百分数： 相对于包含块级元素的高度</li>
</ol>

<hr/>

##### 内边距和外边距

<p>有三种办法可以增加元素与元素之间的距离： 1.增加内边距；2.增加外边距；3.同时增加内外边距；</p>

##### 外边距 --- margin

<ol>
  <li>值： [length], [percentage（百分数）], inherit, auto</li>
  <li>初始值： auto</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 无</li>
  <li>百分数： 相对于包含块级元素的width</li>
</ol>

>在设置外边距的时候，可以使用任何长度值；
>
>margin单独的设置四边的格式：
>
>​	margin： top right bottom left（顺时针旋转）
>
>当我们存在值重复可以减少值的书写：
>
>​	🌰： margin: 0.25em  1em;
>
>	1.	如果缺少左外边距的值可以使用右外边距的值；
> 	2.	如果缺少下外边距的值可以使用上外边距的值；
> 	3.	如果缺少右外边距的值可以使用上外边距的值；

##### 单边外边距属性

<strong>margin-left; margin-right; margin-bottom; margin-top;</strong>

<ol>
  <li>值： [length], [percentage（百分数）], inherit, auto</li>
  <li>初始值： auto</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 无</li>
  <li>百分数： 相对于包含块级元素的width</li>
</ol>

##### 外边距和行内元素

>对于只是包含文本的行，能影响到行间距的只有：
>
>	1.	line-height;
> 	2.	font-size
> 	3.	vertical-align（元素的垂直对齐方式）
>
>由于行内非替换元素的<code>height</code>无效，所以设置行内元素的margin-top和margin-bottom也是无效的;
>
>但是给行内替换元素设置margin-top和margin-bottom可能会印象行高的；

<p>但是可以正常设置<code>margin-left 和 margin-right</code>,设置负的外边距也可以影响到左右的布局。</p>