---
title: '字间距、字母间距和文本修饰'
date: 2020-04-01 08:20
updated: 2020-04-01 08:20
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### 字间距、字母间距和文本修饰

##### 字间距 --- word-spacing

<ol>
  <li>值： [length], normal, inherit</li>
  <li>初始值： normal</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 有</li>
  <li>计算值： 对于normal,为绝对长度0，否则，是绝对长度</li>
</ol>

<p>⚠️: 在word-spacing中同时提供了负值， 负责把字间距拉近。CSS定义字：字可以是任何非空字符串组成的串，并且由某种非空白符包围。</p>

```html
<!--在下方的样式中，只有第一行起作用，只有当存在空格时候，CSS才能判断为单独的字-->
<span style="word-spacing: 100px;">Hello World</span>
<span style="word-spacing: 100px;">欢迎光临</span>
```

<hr/>

##### 字母间隔 --- letter-spacing

<ol>
  <li>值： [length], normal, inherit</li>
  <li>初始值： normal</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 有</li>
  <li>计算值： 对于长度值， 为绝对长度；否则为normal</li>
</ol>

<p>⚠️: 在letter-spacing中同时提供了负值， 负责把字间距拉近。</p>


<p>letter-spacing与word-spacing的区别主要是，前者是修改字符和字母之间的间隔，不用存在空格</p>

```html
<!--在下方的样式中，无论中英文都会起效-->
<span style="letter-spacing: 100px;">Hello World</span>
<span style="letter-spacing: 100px;">欢迎光临</span>
```

>间隔和对齐
>
>​	在之前<code>text-align</code>中，提到可能存在控制单词之间的间距做到对齐
>
>​	所以<code>word-spacing</code>是会受到text-align的影响;
>
>​	但是为<code>letter-spacing</code>设置一个指定值，那么就不会收到text-align的影响;

<hr/>

##### 文本转换 --- text-transform

<ol>
  <li>值： uppercase（大写）, lowercase（小写）, capitalize(只是对每个单词的首字母大写), none, inherit</li>
  <li>初始值： normal</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 有</li>
</ol>

```html
<!--根据不同的用户代理可能出现两种不同的样式：1.Heaing-one;2.Heading-One-->
<span style="text-transform: capitalize;">heading-one</span>
```

<hr/>

##### 文本装饰 ---  text-decoration

<ol>
  <li>值： none, underline, overline, line-through, blink, inherit</li>
  <li>初始值： none</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 无</li>
</ol>

<p>除去Chrome不支持blink之外，其他效果如下：</p>

![](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/textDecoration.png)

```css
/*text-decoration可以存在多个值，如下，效果是既有上划线也有下划线*/
a:link, a: visited { text-decoration: underline overline; }
/*当存在冲突的时候，按照特殊性计算规则计算*/
h2.super { text-decoration: line-through; }
h2 { text-decoration: underline; }
```

<hr/>

##### 文本阴影 --- text-shadow

<ol>
  <li>值： none, [color, length, length, length ], inherit</li>
  <li>初始值： none</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 无</li>
</ol>

<p>⚠️：在定义文本阴影的值中， 可以定义颜色，后面三个长度值分别是阴影与文本左右和上下偏移距离，第三个长度单位是可选的：是阴影的模糊半径。</p>

```css
/*定义一个绿色的阴影，向右偏移5px，向下偏移0.5em*/
p { text-shadow: green 5px 0.5em; }
/*阴影模糊半径定义是： 从阴影的轮廓到模糊的编辑距离*/
p { text-shadow: green 5px 0.5em 2px; }
```

<hr/>

##### 处理空白符号 --- white-space

<ol>
  <li>值： normal, nowrap, pre, pre-wrap, pre-line, inherit</li>
  <li>初始值： normal</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 无</li>
</ol>

>默认的XHTML中，会把标签中的换行以及其他的空白符号合并为一个空格。
>
>​	normal： 这是值是告诉浏览器按照一般做法去做，忽略掉其他空白符号都换成空格；
>
>​	nowrap: 这个值防止文本换行，合并其他空白符号；
>
>​	pre： 这是按照文本内容格式完成，换行符号等会被保留；
>
>​	pre-warp: 这个值会保留空白符号，包括换行符号；
>
>​	pre-line: 这个值是合并其他空白符号，但是会保留换行符号；

![](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/whiteSpace.png)

<hr/>

