---
title: 'CSS选择器的特殊性'
date: 2020-03-28 09:43
updated: 2020-03-28 09:43
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### CSS选择器的特殊性

<p>当可能一个一个元素可以使用一个多个元素匹配，那么需要根据每个选择器的<strong>特殊性（specificity）</strong>来适配最高特殊性：</p>

>选择器的特殊性由选择器本身决定：选择器的特殊值表示为四部分：0, 0, 0, 0;
>
>+ 对于选择器中的给定的各个ID属性值，加 0，1，0，0；
>+ 对于选择器中的给定的类选择器，属性选择器和伪类，加：0，0，1，0；
>+ 对于选择器中的给定的各个元素和伪元素选择器，加：0，0，0，1；
>+ 结合符和通配选择器没有任何贡献；

```css
/*举例如下*/
h1 { color: red; } /*specificity --- 0,0,0,1*/
p em { color: silver; } /*specificity --- 0,0,0,2*/
.grape { color: green; } /*specificity --- 0,0,1,0*/
*.item { color: blue; } /*specificity --- 0,0,1,0*/
p.item em.dark { color: black; } /*specificity --- 0,0,2,2*/
#id216 { color: yellow; } /*specificity --- 0,1,0,0*/
div#id216 *[href] { color: yellow; } /*specificity --- 0,1,1,1*/
```

<strong>在上方例子中，当含有em的CSS规则第二条和第五条相冲突时候，明显第五条的规则特殊性比第二条的特殊性高，所有em表现为第五条的规则。</strong>

##### 声明和特殊性

```css
/*一旦确定一个选择器的声明，这个值将授予其所有的相关声明*/
h1 { color: silver; background: black; }
/*由于特殊性，用户代理相应的处理这个规则，将其解组为单独的规则*/
h1 { color: silver; } /*specificity --- 0,0,0,1*/
h1 { background: black; } /*specificity --- 0,0,0,1*/
```

<p>当一个声明的存在多个规则的时候，用户代理会计算出特殊性并确定哪些规则胜出跟声明相匹配</p>

##### 通配选择器的特殊性

<p>如上，通配选择器的特殊性的值为0，0，0，0，基本没有任何贡献，所以当出现通配选择器的时候，是不会对特殊性做出改变的</p>

#### ID和属性选择器的特殊性

<p>如上ID选择器的特殊性贡献为0，1，0，0；属性选择器的贡献是0，0，1，0；举个例子🌰：</p>

```css
html > body table tr[id="totals"] td ul > li { color: maroon; }   /*specificity --- 0,0,1,7*/
li#answer { color: navy; }  /*specificity --- 0,1,0,1*/
/*属性为id的和ID选择器*/
#meadow { color: green; } /*specificity --- 0,1,0,0*/
*[id="meadow"] { color: red; } /*specificity --- 0,0,1,0*/
```

<p>⚠️：在这里属性选择器中<strong> #meadow > [id="meadow"]</strong>这里很明确的表示了，即使属性中出现了id但是特殊性也不必上ID选择器的特殊性。</p>

##### 内联样式特殊性

<p>之前我们所看到的特殊性第一位都是0,但是在内联样式中，第一位总是保持着1，0，0，0；</p>

```html
<!--specificity --- 1,0,0,0, 那么这意味着即使存在ID选择器也必须遵守内联样式声明-->
<h1 stle="color: green;">The Meadow</h1>  
```

<p>⚠️：<strong>在CSS2.1开始样式特殊性的值0，0，0，0；第一位就是为内联样式新增的。</strong></p>

##### 重要性

<p>在声明某个很重要的声明时候，CSS2.1称之为重大声明---<strong>!important</strong>,允许在分号未结束之前插入!important来表示:</p>

```css
p.drak { color: #333 !important; background: white; }
p.light { color: yellow; font: smaller Times, serif !important; }
```

<p>⚠️：!important总是放在声明最后并且是在分号之前，如果一个属性包含多个值，那么也必须放在最后!</p>