---
title: 'CSS选择器'
date: 2020-03-25 11:07
updated: 2020-03-25 11:07
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

## Css选择器

##### 基本规则

![Css规则格式](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/cssRules.jpg)

##### 一、元素选择器

<p>元素选择器中基本都是用HTML中某个元素作为选择器，如p， h3，em等, 如下：</p>

```Css
html { color: red; }
h3 { color: red; }
h2, h1 { color: green; }
```

<p>如果声明中使用了不存在的属性或者是错误的值，那么这个声明则会被忽略掉; 如果一个属性可以选取多个值，那么则用空格隔开，如下：</p>

```Css
p { front: medium Helvetica; }
```

##### 二、通配选择器

<p>通配选择器可以和任何元素匹配：</p>

```css
* { color: red; }
```

##### 三、类选择器

<p>在HTML元素中输入<strong>class</strong>属性，并且赋予其一个适当的值，那么在css就可以使用类选择器对HTML中存在class属性的对应的值，修改样式：</p>

```html
<!-- 在html中 -->
<p class="warning">该区域需要修改</p>
<!-- 多类的html -->
<p class="warning italic">该区域需要修改</p>
```

```css
/*在css中对应的class=waring的样式， 这里是p元素中class为warning的样式*/ 
p.warning {  
  color: red;
}
/*在css中对应的多类选择器的样式, 这里表示的是p元素中包含warning和italic的具有class的元素， 只包含其一个不予以匹配*/
p.warning.italic {
  color: green;
}
```

##### 四、ID选择器

<p>在HTML元素中输入<strong>id</strong>属性，并且赋予其一个适当的值：</p>

```html
<!-- 在html中 -->
<p id="warning">该区域需要修改</p>
```

```css
/*在css中对应的id=waring的样式*/ 
#warning {  
  color: red;
}
```

<p>☝️需要注意的是他们之间的区别：1.<strong>类选择器</strong>可以被运用到很多元素，可以有多个元素的class的值是相同的，那么他们的样式也是相同的；但是<strong>id</strong>选择器只能使用一次，例如在一个文档中，又一个id的值为lead那么其他的元素的id值都不可以是lead。<br/>同时ID选择器和类选择器都区分大小写.</p>

##### 五、属性选择器

<em>1.普通属性选择器</em>

<p>如果希望根据某个属性，但是无论属性的值是什么，那么可以使用一个简单的属性选择器:</p>

```html
<p class="italic">这里是内容</p>
<p class="warning" moon="star">这里是内容</p>
```

```css
p[class] { color: red; }
```

>这一这里[ ]中的的属性也可以自己命名定义；
>
>如上在html中定义一个含有moon属性的span元素， 那么在css中也可以写成span[moon] {.....},多属性的写法如下：

```css
p[class][moon] { color: green; }
```

<em>2.根据具体属性值选择</em>

<p>除去根据属性可以选择，我们可以进一步缩小范围，根据具体的属性值进行选择：</p>

```html
<p class="warning" moon="star">这里是内容</p>
<p class="warning" moon="sun">这里是内容</p>
<p class="warning" moon="sun star">这里是内容</p> <!-- 当存在多个值的属性， 在css中也应该与之匹配 -->
```

```css
/*那么这里只会对属性moon的值为sun的p元素起作用， 多个属性选择如下二， 可以更精准的定位*/
p[moon="sun"] { color: red; }
p[class="warning"][moon="sun"] { color: green; }
p[class="warning"][moon="sun star"] { color: green; } /*这里多个值的属性应该按照html中写全，并且顺序不能相反，只写其一则无法匹配不生效*/
```

<em>3.根据部分属性值选择</em>

<p>在2中当一个属性具有多个值时（词列表），我们必须在css中也将属性值写全才能匹配，但是部分属性值选择就可以匹配具有部分属性值的元素标签了， 只是需要在等号（=）前面加上一个波浪号（～）：</p>

```html
<p class="warning" moon="sun star">这里是内容</p> 
```

```css
p[moon~="sun"] { color: red; }
```

```css
/*除此之外还有一些部分属性选择器----子串匹配属性选择器*/
[foo^="bar"]  /*选择属性foo以bar开头的所有元素*/
[foo$="bar"]	/*选择属性foo以bar结尾的所有元素*/
[foo*="bar"]	/*选择属性foo包含bar的所有元素*/
```



