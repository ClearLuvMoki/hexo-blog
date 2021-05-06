---
title: 'Css中的层级关系'
date: 2020-03-26 09:20
updated: 2020-03-26 09:20
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

## Css中的层级关系

<p>在浏览器的HTML文档中，元素之间存在许多关系，就像一颗树一样，如下：</p>

![DOM树结构](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/treeCss.jpg)

##### 后代选择器

<p>根据上方树结构，被包裹的元素被叫做包裹元素的后代，比如strong元素就是p元素的后代，anchor（a）元素也是。写法如下：</p>

```css
p strong { color: red; }
```

<p>当然也可以嵌套很多层，深入定位：</p>

```css
dp strong a em { color: red; }
/*注意这里并不是所有的元素都会改变样式，只是在最后的一个后代（em）才会改变， 因此在后代选择器中，中间可以省略很多间隔，如下*/
p em { color: red; }
/*这里的会一直定位到p元素下面的em元素进行对应的样式修改，无论这个em多深*/
```

<p>除去元素标签也可以使用class标签作为后代元素：</p>

```html
<p>
外层嵌套
  <span class="sidebar">内层嵌套</span>
</p>
```

```css
p .sidebar { color: blue; } /*中间也必须有空格*/
```

<em>⚠️注意：在具有多层的树结构中，如果css样式并未定位至对应的最低层，如图中p => strong => a => em结构：</em>

```css
p strong  { color: red; }
```

<em>⚠️：这时候样式依然也会扩张到strong的子元素中</em>

##### 子元素选择器

<p>当我们想缩小后端选择器的范围时，可以选择子元素选择器，他可以选择一个元素的子元素而不是后代元素：</p>

```css
p > strong { color: red; }
```

>或者例如使用类选择器作为子选择器时候：
>
>HTML: &lt;p&gt;这是父级元素的内容&lt;strong class="strongItem" &gt;这是子级元素的内容&lt;/strong&gt;&lt;/p&gt;
>
>Css：p > .strongItem { color: red; }

<P>🌰：当后代选择器和子元素选择器结合：</p>

```html
 <p>  这是p标签的内容
   <strong class="strongItem">这是第一个strong
     <em>第一个em<span class="strongItem2">这是第一个span</span><span>第一个span<span>111</span></span</em>
   </strong>
 </p>
```

```css
/*这里*/
p strong em > span {
    color: red;
}
```

<p>⚠️：当出现以下情况下，样式可能不同:</p>

```html
<!--第一种：在html中子元素相同元素的嵌套-->
<p>这是父级p
  <span>这是一个span
  	<span>这是第二个span</span>
  </span>
</p>
<!--第二种：在html中子元素后代选择中间出现块级元素被隔断-->
<p>这是p元素
  <div>这是span元素</div>
  <em>这是em</em>
</p>

```

```css
/*第一种的css, 子元素第一个span应该才是p元素的子元素，但是第二个嵌套的span元素对于p元素是后代元素也产生了样式的改变*/
p > span {
   color: red;
}
/*第二种css,选择子元素em时候前面出现了div这种块级元素时候，则子元素选择器不起作用，若是放在所选择的子元素后面则可以起作用*/
p > em {
  color: red;
}
```

##### 选择相邻兄弟元素

<p>当多个元素在同一个父级元素下，可以使用相邻兄弟结合符匹配一个元素之后的第一个元素（而不包括本身）：</p>

```html
<!--1-->
<div>
  <p>p</p>
  <span>span</span>
</div>
<!--2-->
<div>
  <span>sapn1</span>
  <span>span2</span>
  <span>span3</span>
</div>
```

```css
/*1.这里只会span元素产生效果，相邻兄弟结合符只会改变后边一个的样式*/
p + span {
  color: red;
}
/*2.当前面元素和后面兄弟以及后续兄弟元素相同时候，除去第一个元素不会改变，后续元素都会改变*/
span + span {
  color: red;
}
```

<p>⚠️:使用结合符时候，要注意顺序，相邻兄弟结合符按照代码的源顺序生效，比如：ul + ol 不等于 ol + ul</p>