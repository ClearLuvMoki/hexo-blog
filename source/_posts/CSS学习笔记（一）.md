---
title: 'CSS（Cascading Style Sheets）层叠样式表'
date: 2020-03-24 10:07
updated: 2020-03-24 10:07
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

<h2>Css（Cascading Style Sheets）层叠样式表</h2>

<h3>元素</h3>

<p>元素（element）是文档结构基础。在Css中，至少在Css2.1中每个元素都会生成一个框（box），其中包含了元素的内容</p>

<h3>元素形式</h3>

<p>元素形式存在<strong>1.替换元素</strong><strong>2.非替换元素</strong></p>

##### &emsp;1.替换元素

<p>&emsp;替换元素（replaced element）:指用来替换元素内容的部分并非由文档之间表示；<br/>
  &emsp;🌰：&lt;img/&gt;标签， 还有&lt;input/&gt;标签类似，当type = 'radio'或者'button'替换元素也会生成相对应的。</p>

##### &emsp;2.非替换元素

<p>&emsp;非替换元素（nonreplaced element）:指用其内容由用户代理在元素本身生成的框中显示；<br/>
  &emsp;🌰：&lt;span/&gt;标签。</p>

##### 元素类型

<p>元素类型存在<strong>1.行内元素（inline-block）</strong><strong>2.块级元素（block-level）</strong></p>

##### &emsp;1.行内元素

<p>&emsp;行内元素（inline-block）:在一个文本行内生成元素框，而且不会打断这行文本<br/>
  &emsp;🌰：&lt;a&gt;&lt;/a&gt; &lt;strong/&gt;&lt;/strong/&gt; &lt;em&gt;&lt;/em&gt;</p>

##### 2.块级元素

<p>&emsp;块级元素（block-level）:会生成一个元素框填充其父元素的内容区域，旁边不能又其他元素，它在元素前后生成了“分隔符”；<br/>
  &emsp;🌰：&lt;p&gt;&lt;/p&gt; &lt;div/&gt;&lt;/div/&gt;</p>

### link标签

<p><strong>link</strong>标签将css文件和html（xhtml）关联起来</p>

<p>&emsp;在html（xhtml）中使用,举个🌰：</p>

```html
<link rel="stylesheet" type="text/css" href="xxx.css" media="all" />
```

>rel（relation）： 关系 
>
>type:  规定被链接文档的类型，总是设置为"text/css"
>
>href：链接文档的URL，可以是相对路径也可以是绝对路径
>
>media：样式表应用的类型  => 
>
>​			'all': 用于所有的媒体；
>
>​			'aural': 用于语音合成器，屏幕阅读和文档的其他声音表现；
>
>​			'braille': 用于Braille设备表现文档时使用（盲文）；
>
>​			'embossed': 用于Braille打印设备使用;
>
>​			'handeld': 用于手持设备，如个人数字助理或者支持web的蜂窝电话；
>
>​			'print': 为实正常的用户打印文档时候使用，另外还会在显示"打印预览"时候使用;
>
>​			'projection': 用于投影媒体，如发表演讲时显示的幻灯片的数字投影仪;（Opera）
>
>​			'ttr': 在固定间距环境（如电传打字机）中显示文档使用;
>
>​			'tv': 在电视上显示文档使用;
>
>​			'screen': 在屏幕媒体（如桌面计算机监视器）中表现文档使用。在这种系统上运行的所有web浏览器都是屏幕媒体用户代理；

<p><strong>media</strong>属性可支持多个媒体类型，如：media="screen, tv"</p>

<p>&emsp;一个文档连接多个样式表写法：</p>

```html
<link rel="stylesheet" type="text/css" href="a.css" media="all" />
<link rel="stylesheet" type="text/css" href="b.css" media="all" />
```

##### 候选样式表（alternate style sheet）

<p>&emsp;将<strong>link</strong>标签中的<em>rel</em>属性设置为"alternate"就可以定义候选样式表, 写法如下：</p>

```html
<link rel="alternate stylesheet" type="text/css" href="b.css" />
```

<p>&emsp;如果启用了候选样式表，link标签中的title则声称为候选样式的一个列表;在MacOs操作系统下仅仅是子啊Firefox浏览器中找到了候选样式表的选择，在Safari和Chrome浏览器中均没有找到可选样式表的地方;</p>

```html
<link rel="alternate stylesheet" title="Default" type="text/css" href="index.css" media="all"/>
<link rel="alternate stylesheet" title="BigText" type="text/css" href="./bigText.css" media="all"/>
```



![在Firefox中可选的样式表](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/alternateCss.jpg)

##### style元素

<p>&emsp;style元素包含样式表，在文档中单独出现， style中一定要使用type属性，一般type='text/css'</p>

```html
<style type="text/css" ></style
```

<p>&emsp;style中也支持media属性，与之前link中的可选值一样：</p>

<p>&emsp;与link标签一样可以引入多个<strong>@import</strong>标签，但是不同于link标签，每个引入的都会被加载和使用, 并且需要写在样式表的其他规则之前；但是在IE中不会放过任何一个<strong>@import</strong>无论你写在位置在style标签内部的哪，所以请规范书写;</p>

<p>&emsp;在style标签中支持引入外部样式文档，使用了<strong>@import</strong>来引入：</p>

```html
<style type="text/css">
	@import url(./index.css) all;
    @import url(./bigText.css) screen;
    @import url(http://xxxxx.org/layout.css) tv;
  h1 { color: red }
</style>
```

##### Css中的注释

```css
/* 这里写注释，
并且可以跨行， 但是不可以嵌套注释 */
```

##### 内联样式

```html
<p style="color: red; background:yellow">
  这里用作测试
</p>
```

>css引入方法：
>
>​	1.内部样式（在html中写style标签，将样式写在style中）
>
>​	2.外部样式表（通过link或者@import url引入外部的样式表）
>
>​	3.行内样式 （如上代码写在html行内， 用style属性书写的样式）

