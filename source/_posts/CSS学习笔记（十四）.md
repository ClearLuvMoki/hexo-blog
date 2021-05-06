---
title: '基本视觉格式化（一）'
date: 2020-04-01 16:20
updated: 2020-04-01 016:20
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### 基本视觉格式化（一）

##### 基本框（盒子模型）

![](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/boxImg.png)

##### 块级元素

![](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/blockImg.png)

<p>块级元素中，<code>width</code>一般指的是左内边界到右内边界的距离，<code>height</code>同理。</p>

##### 水平格式化

```html
<!--在width中，指的是内容的宽度，而不是整个盒子的宽度；-->
<p style="width: 200px">展示内容</p>
<!--如果还指定了内边距（padding）和外边距（margin），那么整个盒子模型宽度还要继续增加-->
<!--如下：现在盒子模型的宽度是260px-->
<p style="width: 200px;padding: 10px; margin: 20px;">展示内容</p>
<!--在如下例子中:两个span的内容区+左右内边距+左右边框+左右外边距 就等于 div的内容区（content）的宽度-->
<div><span>span1</span><span>span2</span></div>
```

##### 水平属性

>水平属性：
>
>​	margin-left, margin-right;
>
>​	padding-left, padding-right;
>
>​	border-left, border-right;
>
>​	width;
>
>这些属性与块级框的水平布局有关
>
>在上述属性中，只有<code>width, margin-left, margin-right</code>可以设置成<code>auto</code>.	

##### 使用auto

<p>一个父块级元素的width等于其子元素的width+padding-left+padding-right+margin-left+margin-right.</p>

<p>设置auto可以自动计算宽度，让子元素的宽度补齐父元素的width。</p>

```css
/*当父元素的width为400px,不考虑边框和内边距，那么margin-right就等于200px*/
p { width: 100px; margin-left: 100px; margin-right: auto; }
/*当我们父元素还是400px, 没有一个属性设置为auto，那么会默认把mrgin-right设置为auto，由margin-right来填补宽度*/
```

<p>自动补齐中，设置子元素width为auto也是同样的道理；也可以不写width，效果一样可以补齐：</p>

```css
/*上下两种效果一样*/
p { width: auto; margin-left: 100px; margin-right: 100px; }
p { margin-left: 100px; margin-right: 100px; }

```

```css
/*当我们使用两个auto时候，在我们设置了width，margin-left和margin-right都使用了auto，那么将会让元素左右的外边距一样，则会让元素水平居中；*/
p { width: 100px; margin-left: auto; margin-right: auto; }
/*当我们设置width和某一个外边距为auto， 那么设置为auto的外边距则会变成0， 需要补充的部分由width补充*/
p { width: auto; margin-left: 100px; margin-right: auto; }
/*当我们设置了三个属性都是auto，那么左右的外边距则会变成0， width则会尽可能的宽*/
p { width: auto; margin-left: auto; margin-right: auto; }
```

##### 负外边距

<p>当我们存在负外边距的时候，但是还是满足子元素的width+padding-left+padding-right+margin-left+margin-right加起来为父元素的width：</p>

```css
/*当我们假设父元素还是400px,设置为width为auto， margin-right为-50px，但是还是等于父元素width400px*/
p { width: auto; margin-left: 100px; margin-right: -50px; border-left: 10px; border-right: 10px; }
/*100 + (-50) + 10 + 10 + 330 = 400, 这个330是因为上述width为auto， 补充为330*/
```

<p>当我们给mergin-right设置为auto，也是可以计算为负值；当我们根据父级元素width，将子元素的水平七大属性设置为固定值（非auto），当子元素的值大于了父元素的width，那么也会重置子元素的margin-right，使得两者相等；</p>

```css
div { wdith: 400px; }
p { width: 100px; margin: 0 200px; border-left: 10px; border-right: 10px; }
/*100 + 200 + 200 + 10 + 10 = 520 > 400,这个时候会重置margin-right，让margin-right变成-20px,这样才能重置跟父元素一样的*/
```

##### 百分数

<p>百分数跟确定值并没有太多区别，百分数也会遵循相应的规则。</p>

##### 替换元素

<p>替换元素中的规则，与非替换的块级元素基本规则一样，除去一点：替换元素如果设置<strong>width为auto，那么width则是该替换元素的默认宽度</strong>；并且设置了宽度，如果不设置height那么则会成比例的放大或者缩小，相反设置height也是一样的道理。</p>