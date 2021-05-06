---
title: 'CSS字体'
date: 2020-03-29 09:20
updated: 2020-03-29 09:20
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### CSS字体

##### 字体系列 --- font-family

<ol>
  <li>初始值：用户代理指定的值</li>
  <li>应用于：所有元素</li>
  <li>继承性：有</li>
</ol>

<p>CSS定义了5种通用的字体系列：</p>

<p>分别是<em>Serif, Sans-serif, Monspace, Cursive, Fantasy：</em></p>

![这是五种字体的样本](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/fontfamily.png)

<p>当我们制定了一个元素的字体，用户代理会去寻找是否存在这个字体，如果存在这个字体那么就会显示；如果不存在这个字体，只会显示用户代理默认字体。</p>

<p>⚠️：所以我们在使用font-family时候，尽量保留一个通用字体，保证至少一个字体可用。特别是在跨平台的情况下，可能会没有我们希望的字体，那么需要我们保留一个通用字体（上述五大字体）；而这个字体一般放在最后，把自己希望希望出现的字体放在最前，按照自己希望的顺序排列。</p>

```css
/*当我们想使用的Georgia字体不起作用时候，那么serif就可以起作用啦，*/
#font { font-family: Georgia, serif; }
/*浏览器会一次判断这些字体是否存在有效，无效的那么会向后寻找，所以希望保留一个通用字体*/
#font { font-family: Georgia, Times, TimesNR, 'New York', serif; }
```

>在上述情况排列中，出现了'New york'这种用单引号包起来的字体，字体中如下情况需要用单引号包起来：
>
>​	1.字体名中出现空格；
>
>​	2.字体名中出现一些符号，比如#，$等这些符号;（在CSS2.1开始，出现特殊符号的不一样用单引号包起来，但是只是一种推荐）；
>
>​	3.当你想使用一种字体和通用字体名相冲突时候，需要加上引号；比如你也想使用"serif"外部引入的字体，那么则需要加上引号；

<hr/>

##### 字体加粗 --- font-weight

<ol>
  <li>值：normal（相当于400）， blod（相当于700）， bolder（从父元素继承来的值更粗）， lighter（从父元素继承来的值更细）， 100， 200 ... 900, inerit</li>
  <li>初始值：normal</li>
  <li>应用于：所有元素</li>
  <li>继承性：有</li>
</ol>

<p>一般来说字体加粗越重，那么字体看上去“越黑越粗”。如下展示：</p>

![](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/fontWeight.png)

<p>当我们选择了一个<strong>bolder或者是哦lighter</strong>,那么首先需要确定从父元素继承的font-weight的值。它应该是比继承的值大，但是是范围中最小的那个最大值。--- 根据字体本身的font-weight可选值改变，并不是每个字体都有100～900的加粗度。</p>

<hr/>

##### 字体大小 --- font-size

<ol>
  <li>值：xx-small, x-small, small, medium, large, x-large, xx-large, smaller, larger, [length], [percentage], inherit</li>
  <li>初始值：medium</li>
  <li>应用于：所有元素</li>
  <li>继承性：有</li>
  <li>百分数：根据父元素的字体大小计算</li>
</ol>

<p>实际上font-size与设计者设计字体来确定。这种设置字体本身有一个<strong>em框</strong>，这个em框和相应的字体大小，无法保证字体边界，有可能字体超过边界：</p>

![font的em边框](/Users/moki/Library/Application Support/typora-user-images/image-20210329231438797.png)

<ul><li>绝对大小</li></ul>

<p>font-size中存在六个绝对大小的值， <strong>xx-small, x-small, small, medium, larger, xx-large, x-large</strong></p>

![不同font-size的大小](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/fontSize.png)

<p>在这些绝对大小的值中，总是根据其他的值来比对；比如当medium的值是10px， 那么large就应该是15px</p><br/><p>
  在绝对大小的中的比较重一般使用<strong>缩放因子</strong>计算，一般是<em>1.5或者1.2</em>,根据用户代理的不同，缩放因子也不一样，CSS2的缩放因子介于1.0～1.2之间。
</p>

<ul><li>相对大小</li></ul>

<p>相对大小一般指的是<strong>smaller, larger</strong>, 这两个值会在父元素的font-szie大小梯度上上下移动；即使在xx-small和xx-lager中比较，<strong>smaller, larger</strong>也会更小或者更大。 </p>

<ul><li>百分数和大小</li></ul>

<p>百分数总是根据父元素那里继承过来的大小计算，它比相对大小控制的更加精准，在使用em时候等价于百分数，比如<storng>1em = 100%</storng>.</p>

<ul><li>字体大小和继承</li></ul>

<p>字体是可以继承的，但是它继承的是计算值而不是百分数，如下所示：</p>

```html
<!--事例-->
<p>这是p元素内容
  <strong>这是strong内容<em>这是em内容</em></strong>
</p>
```

```css
p { font-size: 12px; }
strong { font-szie: 120%; } /*这里等于 12px 乘以 120% 为 14.4px*/
em { font-szie: 135%; } /*这里等于父级的strong的计算值14.4px 14.4px 乘以 135% 为 19.44px*/
```

<p>⚠️： 在我们一层层嵌套中，如果用户代理每一次取整再计算，那么误差就会层层叠加。</p>

<hr/>

##### 风格和变形 --- font-style

<ol>
  <li>值：italic, oblique, normal, inherit</li>
  <li>初始值：normal</li>
  <li>应用于：所有元素</li>
  <li>继承性：有</li>
  <li>计算值：根据制定确定</li>
</ol>

![字体样式](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/fontStyle.png)

<p>除去inherit依然是继承了父元素的样式，主要是分辨<strong>italic和oblique</strong>的区别：关于italic，更多对于每一个字符都有所改变的倾斜体；而oblique，则是普通样式文本的倾斜体；但并不是每个文本都是如此，具体根据font-famliy所支持的。</p>

<hr/>

##### 字体变形 --- font-variant

<ol>
  <li>值：small-caps, normal, inherit</li>
  <li>初始值：normal</li>
  <li>应用于：所有元素</li>
  <li>继承性：有</li>
  <li>计算值：根据制定确定</li>
</ol>

<p>关于<strong>samll-caps</strong>，这个的意思是小型的大写字母，但是当文本中出现了大些字母，那么样式更大一点；具体样式如下：</p>

<ol>
  <li>值： uppercase（大写）, lowercase（小写）, capitalize, none, inherit</li>
  <li>初始值： normal</li>
  <li>应用于： 所有元素</li>
  <li>继承性： 有</li>
</ol>

<p>这与<code>text-transform: uppercase;</code>差不多，但是大小上有一定的区别；之所以small-caps能生效，是因为有一些字体具有这个small-caps这个值，当某些字体不具有这些值的时候，那么1.用户代理会自己缩放大写字母来创建small-caps；2.转换所有的字母为大写字母，但是大小相同。（等效于text-transform: uppercase;）</p>

<hr/>

##### 字体拉伸 --- font-stretch / font-size-adjust

<ol>
  <li>font-stretch</li>
  <li>值：normal, wider, narrower, ultra-condensed, extra-condensed, condensed, semi-condensed, semi-expanded, expanded, extra-expanded, ultra-expanded, inherit</li>
  <li>初始值：normal</li>
  <li>应用于：所有元素</li>
  <li>继承性：有</li>
</ol>
<ol>
  <li>font-size-adjust</li>
  <li>值："number", none, inherit</li>
  <li>初始值：none</li>
  <li>应用于：所有元素</li>
  <li>继承性：有</li>
</ol>

<p>⚠️：但是这个属性在MacOs系统下的 Safari，GoogleChrome, FireFox对于<strong>font-stretch</strong>都没有起作用。</p>

<p>⚠️：在MacOs系统下的 Safari，GoogleChrome对于<strong>font-size-adjust</strong>都没有起作用, 只有FireFox起作用。</p>

<hr/>

##### font

<p>当我们一个字体需要写很多属性的时候，那么就很杂乱，在font声明中，可以讲以上许多融入的一起, 规则如下：</p>

```css
/*在这和五个属性中，前三个顺序可以打乱，但是后两个必须按照font-size，font-famliy， 顺序错误则整个声明无效*/
font { font-style, font-weight, font-variant,  font-size, font-famliy }
```

<hr/>

##### 增加行高

<p>尽管增加行高更多是文本（text）属性而不是font属性，但是我们还是通过新增<strong>line-height</strong>来增加行高，但是<strong>font-size和line-height</strong>总是用“/”分割：</p>

```css
/*在我们添加设置行高的时候，通过在后面添加"/"来增加行高的值： font-size / line-height，并且line-height总是在font-size后面*/
font { font-style, font-weight, font-variant,  font-size: 200%/1.2, font-famliy }
```

<hr/>

##### 使用系统字体

<p>我们也可以使用系统的字体来进行匹配：</p>

>caption: 用于有标题的控件（按钮）
>
>icon： 用于有对图标加上标签
>
>menu：用于菜单，即下拉菜单和菜单列表
>
>message-box： 用于对话框
>
>samll-caption： 用于小控件带标签的
>
>status-bar： 用于窗口的状态条

![各种系统字体](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/fontSystem.png)

<p>⚠️：以上字体效果在GoogleChrome无效，但是在FireFox和Safari中有效果。</p>