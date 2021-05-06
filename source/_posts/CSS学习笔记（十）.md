---
title: 'CSS值和单位'
date: 2020-03-28 22:22
updated: 2020-03-28 22:22
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### CSS值和单位

##### 数字

<P>CSS中存在两种数字：整数和实数（小数），但是属性有时候会限制大小</p>

<hr/>

##### 百分数

<p>在CSS中百分数一般总是相对于另一个值，比如相对于父元素或者是祖先元素的某一属性的值</p>

<hr/>

##### 颜色

<ol>
  <li>命名颜色</li>
  <p>在我们对于颜色赋值时候，可以使用CSS2.1中规定的颜色名直接赋值，比如： blue， yellow等</p>
  <li>使用RGB命名</li>
  <p>使用RGB来源于计算机中通过红色，蓝色，绿色来创造颜色</p>
  <ul>
    <li>函数式RGB颜色</li>
    <p>RGB的颜色表示语法为:<strong>rgb(color)</strong>,其中color可以使用三元整数或者三元百分数表示；百分数的取值范围是0%～100%，而整数的取值范围是0～255.🌰：</p>
    <p>百分比的表示如下：</p>
    <code>rgb(100%,100%,100%)白色</code>
    <code>rgb(0%, 0%, 0%)黑色</code>
    <hr/>
    <p>整数的三元组的表示如下：</p>
    <code>rgb(255,255，255)白色</code>
    <code>rgb(0, 0, 0)黑色</code>
    <P>同时在用百分号表示的时候，也可以使用小数表示，比如<code>rgb(23.6%,47.9%,54.7%)</code>，但是某些用户代理并不会读取小数，会就近取整；在我们取值的时候如果大于最大值或者最小值（100%-255，0%-0）那么就会直接等于相应的最大值和最小值的极限。<br/>关于百分数与整数的关系是：百分数*255 = 相应的整数值。</P>
    <li>十六进制的RGB颜色</li>
    <p>十六进制的RGB语法是<code>#RRGGBB</code>将三个介于00～FF的三个十六进制的数连接起来，当我们偶尔会看见三位的十六进制颜色<code>#6AF</code>，这是因为浏览器用户代理可以每取一位然后复制一位，<code>#6AF</code>就等于<code>#66AAFF</code>.</p>
    <li>Web的安全颜色</li>
    <p>Web的安全颜色指的是在256（0～255）色的计算机上总能避免抖动的颜色。</p>
    <p>这些颜色指的是：RGB值为20%和51（十六进制的33）的倍数（0%-0也是安全值），如果使用的是十六进制的数，那么00，33，66，99，CC，FF这些也是安全值。</p>
  </ul>
</ol>
```css
/*red*/
rgb(100%, 0%, 0%), rgb(255,0,0), #FF0000, #F00
/*orange*/
rgb(100%, 40%, 0%), rgb(255,102,0), #FF6600, #F60
/*green*/
rgb(0%, 50%, 0%), rgb(0,128,0), #008000,  /
```

<hr/>

##### 长度单位

<ul>
	<li>绝对长度单位</li>
  <p>在平时开发中很少使用到绝对长度的单位，但是需要知晓：<br/>in(英寸);<br/>cm(厘米) --- 1in == 2.54cm;<br/>mm(毫米) --- 1cm == 10mm;<br/>pt(点) --- 1in == 72pt;<br/>pc(派卡) --- 1pc == 12pt, 1in == 6pc;</p>
  <li>相对长度单位</li>
  <p>相对长度一般是根据其他事物来进行度量的.</p>
  <ol>
    <li>em和ex单位（事例具体请详见下方例一！）</li>
    <p>
      首先我们在CSS中，<br/><strong>1em</strong>指的是一种给定字体的<code>font-size</code>值。如果一个元素的<code>font-size: 14像素</code>,那么相对于该元素，1em就等于14像素；<br/>
      <strong>1ex</strong>这里文档说的不是很清楚，<a href="https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Values_and_units">MDN上写的指的是字符“x”的高度.</a>，在关于《CSS权威指南》第三版中指出是所用字体中小写“x”的高度，一般是所用字体的一半的高。
    </p>
    <em>em和ex的实际问题</em>
    <p>
      在此之前的，一般的用户代理都会选择：先取em的值，再取其一般作为ex的值（相当于1ex == 0.5em），但是还有一些浏览器会在内部显示一个小写的x，并计算相应的像素值来确定其高度与此字符的font-size值之比，从而确定给定的字体的x高度。
    </p>
    <li>像素长度</li>
    <p>
      像素其实就是电脑显示屏上的一个个像素点，每一个框就是一个像素
    </p>
    <em>其他关于长度单位的请参考我的另一篇笔记: <a href="http://www.clearluv.com/2019/12/12/CSS%E5%8D%95%E4%BD%8D/">CSS单位</a></em>
  </ol>
</ul>

```css
/*例一*/
/*这里将一个元素设置了font-size，那么使用em则会按照其font-size的值来配对，比如14px = 1em，如果没有设置的则会寻找父级元素或者祖先元素的font-size*/
p { font-size: 14px; margin-left:1em; }
```

<hr/>

##### URL

<p>我在之前讲述的引入CSS的方法中，使用了<strong>link标签和@import</strong>来从外部引入CSS，在我们引入地址的情况下也分为绝对地址和相对地址:</p>

<ul><li>绝对地址(absolute)</li></ul>

<p>绝对地址的意思是，这个地址放在哪都可以被访问到，比如一个外部的http链接.<code>@import url(http://xxxxxx.css);</code></p>

<ul><li>相对地址(relative)</li></ul>

<p>相对地址的意思是，相对于该URL的一个文件存放位置.<code>@import url(/pages/css);</code></p>

<hr/>

##### 关键字

<p>用一个词来代表某一个值， 那么这个词就是关键字。但是可能不能属性的关键字一样的话，可能表现的效果不一样。</p>

```css
/*例如在text-decoration中就存在多个关键字*/
span { text-decoration: none; } /*none --- 设置没有下划线*/
span { text-decoration: underline; } /*underline --- 设置有下划线*/
```

<ul><li>inherit</li></ul>

<p>但是在CSS2.1中，又一个关键词的是所有属性共有的，<strong>inherit</strong> --- 它的意思是使一个属性的值和其父元素或者祖先元素的值相等。</p>

```html
<div id="toolBar">
  <a href="www.baidu.com">ONE</a>
  <a href="www.google.com">TWO</a>
</div>
```

```css
#toolBar { background: blue; color: white; }
#toolBar a { color: inherit; } /*这里后代a标签（带有href）都会继承祖先ID为toolBar的样式*/
```

<hr/>

##### CSS2单位--- 后续接触到会详细的写

<ul><li>角度值</li></ul>

<p>主要定义给定的声音从哪个位置发出的。共有三种角度：<em>度（deg），梯度（grad），弧度（rad）.</em> </p>

<ul><li>时间值</li></ul>

<p>用于给定语音元素之间的延迟。可以为毫秒（ms），也可以表示成秒（s）。时间不能是负值。</p>

<ul><li>频率值</li></ul>

<p>用于为语音浏览器可以产生的声音声明一个给定频率。可以为赫兹（Hz），兆赫（MHz）。</p>