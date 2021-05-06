---
title: 'CSS继承'
date: 2020-03-28 14:56
updated: 2020-03-28 14:56
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### 继承

<p>🧑🏻‍💻写在前面：关于继承，在面试中只有一家公司提到了CSS的继承，记忆很深刻，整理下笔记如下：</p>

<p>基于继承机制，样式不仅会运用到指定元素，也会运用到其后代元素，🌰：</p>

```html
<h1>这是标题<em>标题</em></h1>
```

```css
/*这里给元素h1指定样式，那么h1的后代元素em也会相应的改变样式，继承对于无需列表ul也是一样起作用的*/
h1 { color: gray; }
```

>关于继承，一般都是沿着DOM树结构向下继承，直到改元素没有后代元素为止；
>
>但是有一种向上继承 应用到<strong>body标签</strong>的背景样式可以向上继承到<strong>html标签中</strong>

<p>⚠️：并不是所有的属性都可以继承，例如<strong>大多数框模型（内外边距，边框border属性）</strong></p>

<p>⚠️：关于前面提到的特殊性的取值，结合符和通配选择器的特殊性的值都是0，但是在这里继承的特殊性的值是不存在的！这里的特殊性的值为0和不存在是两种情况，请看如下例子：</p>

```html
<h1 id="page-title">CSS的<em>继承</em></h1>
<p>Welcome</p>
```

```css
* { color: gray; }
h1#page-title { color: black; }/*效果如下*/
```

![CSS继承](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/cssInheritance.jpg)

<p>在上方中通配的特殊性为0，继承没有特殊性，所以em元素并没有继承h1中ID为page-title的样式，这里就表现了特殊性为0的优先级高于继承,，再看下面这个例子：</p>

```html
<p id="pItem">这是一个<a href="#">链接</a></p>
```

```css
/*如下：即使这样写a链接还是蓝色的*/
#pItem{ color: white; background: black; }
```

<p  style="color: white; background: black;">这是一个<a href="#">链接</a></p>

<p>⚠️：这是因为浏览器默认存在<strong>a:link { color: blue }</strong>，伪类的特殊性是0，0，1，0；比继承的无特殊性要高，所以显示为蓝色</p>