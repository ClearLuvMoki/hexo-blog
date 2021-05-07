---
title: '基本视觉格式化（二）'
date: 2020-04-02 09:20
updated: 2020-04-02 09:20
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### 基本视觉格式化（二）

##### 行内元素和行布局

<p>在《CSS权威指南》中，指出了<code>em, a ,image</code>这些标签都是行内元素。</p>

##### 基本术语

>匿名文本
>
>​	未包含在行内标签中的文本。

```html
<!--“这是p”和“又是p”就属于匿名文本，空格也算-->
<p>这是p<em>em</em>又是p</p>
```

>em框
>
>​	之前文章<a href="http://www.clearluv.com/2020/03/29/CSS%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0%EF%BC%88%E5%8D%81%E4%B8%80%EF%BC%89/#%E5%AD%97%E4%BD%93%E5%A4%A7%E5%B0%8F-%E2%80%94-font-size">font-size这一章节中</a>，讲述过em框在一定程度上表现了字体的大小，字体的大小可能超过或者小于em框。

![](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/fontSizeEmBorder.png)

>内容区
>
>​	在非替换元素中，内容区元素中各em框组成的框；
>
>​	在替换元素中，内容区就是固有高度 + 内边距 + 边框 + 外边距；

>行间距（leading）
>
>​	行间距就是 font-size 和 line-height 之间的差；
>
>​	但是这个差又要分成两半，一半是上面的行间距，一半是下面的行间距；
>
>​	行间距只能用于非替换元素；

>行内框
>
>​	对于非替换元素，行内框 = line-height；
>
>​	对于替换元素，行内框 =  元素内容高度；

##### 行内格式化

<p><code>在line-height</code>只是会直接影响到行内元素的高度，不会直接影响块级元素的高度。</p>

<p>虽然块级元素设置line-height不会直接其作用，但是给块级元素设置line-height会对其文本内容或者其行内元素会继承line-height。</p>

