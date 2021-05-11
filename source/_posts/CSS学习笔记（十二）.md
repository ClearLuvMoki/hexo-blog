---
title: '文本对齐'
date: 2020-03-30 10:07
updated: 2020-03-30 10:07
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### 文本对齐

##### 缩进和文本对齐

<ul><li>首行缩进 --- text-indent</li></ul>

<ol>
  <li>值： [length], [percentage（百分数）], inherit</li>
  <li>初始值： 0</li>
  <li>应用于： 块级元素(不可用在行内元素中，即使是img这种替换元素，但是块级元素中包含img元素是可以的)</li>
  <li>继承性： 有</li>
  <li>百分数： 相对于块级元素的宽度</li>
</ol>

<p>这个属性是指块级元素的第一行缩进一个给定的长度， 值也可以为负数：</p>

```css
p { text-indent: 3rem; }
p { text-indent: -4rem; }
```

<p>⚠️： 当我们使用负值的时候，要注意内容超出浏览器的可视范围，这时候最好设置一个左内边距（padding-left）</p>

```css
p { text-indent: -4rem; padding-left: 4rem; }
```

<ul><li>水平对齐 --- text-align</li></ul>

<ol>
  <li>值： left, right, center, justify, inherit</li>
  <li>初始值： 用户代理特定的值， 还可以取决于书写方向（西方语言从左到右； 阿拉伯语言等之类的语言从右到左）</li>
  <li>应用于： 块级元素</li>
  <li>继承性： 有</li>
  <li>百分数： 相对于块级元素的宽度</li>
</ol>

```css
/*文本左对齐*/
p { text-align: left; }
/*文本右对齐*/
p { text-align: right; } 
/*文本居中， 与之前的<CENTER>元素不同，text-align: center只会把文本居中（只会影响内部）， 但是<CENTER>会把元素也居中*/
p { text-align: center; } 
/*文本两端对齐，在两端对齐中，会把两端的内容放在内边距上， 然后调整这一行的内容间隙， 使得各行的内容长度相等*/
p { text-align: justify; } 
```

<p>⚠️：<strong>text-align: justify;</strong>拉伸行内间隙是由用户代理决定的， 而不是CSS决定；有一些用户代理会拉伸<strong>单词内字母</strong>间距，但是一些用户代理只会拉伸<strong>单词</strong>之间的间距；还有一些用户代理会缩短单词之间间隙让元素更加紧凑。</p>

<ul>
  width
  <li></li>
</ul>

##### 垂直对齐

<ul><li>行高 --- line-height🌟</li></ul>

<ol>
  <li>值： [length], [percentage（百分数）], [number], normal, inherit</li>
  <li>初始值： normal</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 有</li>
  <li>百分数： 相对于元素的字体大小</li>
</ol>

<p><strong>line-height</strong>指的是文本行基线之间的距离， 而不是字体的大小，控制了行间距。这是文本行之间超出字体大小的额外空间； line-height的值与字体大小之差就是行间距。</p>

<p⚠️：<strong>line-height</strong>指的是元素文本基线中的最小距离；文本拉开的距离可能要比line-height更大。</p>

<ul><li>构造文本行</li></ul>

<p>文本行内的每个元素都会生成内容区， 这个由字体大小确定；这个内容区则会生成一个行内框（inline box），这个行内框就完全等于该元素的内容区。 <strong>则line-height产生的行间距就是增加或者减少行内框的高度因素之一</strong></p>

>给定一个元素的行间距 = line-height的计算值 - font-size的计算值
>
>以上这个值可能是负值，但是这个值除以2（分别用在内容区的上下），就是改元素的行内框。

<ul><li>指定line-height的值</li></ul>

<ol>
  <li>默认值： normal，不用的用户代理可能计算出来的值不一样，但是一般为字体大小的1.2倍， 使得行内框要高于font-size的值。</li>
  <li>em， ex， 百分数： 这些值都是相对于元素的font-size值计算；</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 有</li>
  <li>百分数： 相对于元素的字体大小</li>
</ol>

<ul><li>行高和继承</li></ul>

<p>当一个块级元素从另一个元素继承line-height时候，要从父元素计算，而不是在子元素上计算，具体情况如下：</p>

```html
<body>
<div>
  这是div内容
  <p>
    这是p内容
  </p>
</div>
</body>
```

```css
/*例一：这里line-height只会继承body中的font-size，就会导致行间距小于字体大小*/
body { font-size: 10px; }
div { line-height: 1em; } 
p { font-size: 18px; }
/*例二：这里line-height只会继承body中的font-size，就会导致行间距小于字体大小*/
body { font-size: 10px; }
div { line-height: 1; } 
p { font-size: 18px; }
```

<p>⚠️：对于继承, 如我们如上所写，存在一个line-height的父元素的font-size小于其子元素的font-size，那么很有可能造成行间距负数，字体堆在一起；解决办法呢就是设置一个缩放因子（例二）这样就可以该元素和其子元素都是根据自己的font-size计算的line-height。</p>

<ul><li>垂直文本对齐 --- vertical-align🌟</li></ul>

<ol>
  <li>值： baseline, sub, top, super, text-top, middle, bottom, text-bottom, [length], [percentage（百分数）], inherit</li>
  <li>初始值： baseline</li>
  <li>应用于： 行内元素和表单元素</li>
  <li>继承性： 无</li>
  <li>百分数： 相对于元素的line-height的值</li>
  <li>说明： 应用到表单元素时候，只能识别baseline，top, middle, bottom等值</li>
</ol>