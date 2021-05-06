---
title: '伪类和伪元素(一)'
date: 2020-03-26 22:55
updated: 2020-03-26 22:55
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### 伪类和伪元素（一）

##### 伪类选择器

<p>CSS<strong>伪类(pseudo-class)</strong>是添加到选择器的关键字，指定要选择的元素的特殊状态.请遵循参照lvha顺序<strong>:link — :visited — :hover — :active</strong>。</p>

<ul>
  <li>链接伪类</li>
  <ul>
    <li><strong>:link</strong></li>
    <p>链接伪类中的<strong>a标签</strong>都是带有<strong>href属性</strong>，伪类选择器是用来选中元素当中的链接。:link它将会选中所有<strong>尚未访问</strong>的链接，包括那些已经给定了其他伪类选择器的链接（例如:hover选择器，:active选择器，:visited选择器）.</p>
  </ul>
</ul>


```html
<!---这里的链接需要带上href属性-->
<a href="#">链接</a>
```

```css
/*这是a链接点击之前的样式*/
a:link {
  color: red;
}
```

<ul>
  <li><strong>:visited</strong></li>
  <p><strong>:visited</strong>CSS伪类表示用户已访问过的链接。这个样式可能会被后声明的其他链接相关的伪类覆盖，这些伪类包括 (:link, :hover,和:active),请将:visited 规则放在:link 规则之后，但在:hover 和:active 规则之前，参照lvha顺序<strong>:link — :visited — :hover — :active</strong>。</p>
  </ul>

```css
/*如果要设置a链接点击前的样式，请使用a:link, 如果单独使用上方a链接的样式，可能也会使a标签(非链接=>即没有吧href属性)的内部文字改变样式*/
a{
  color: red;
}
/*这是a链接点击之后的样式*/
a:visited {
  color: green;
}
```

<p>⚠️：由于浏览器机制，设置：visited很容易暴露用户访问链接，建议先给a（含有href属性）标签之前设置样式，比如单独的<strong>a:link
  </strong></p>

<p>当一个页面存在多个a标签时候（具有href属性）可以等价于在<strong>body标签</strong>中添加上<strong>link属性和vlink属性：</strong></p>

```html
<body link="red" vlink="green"><a href="#">这是链接1</a></body>
```

<p><strong>:link和:visited</strong>都可以结合类选择器， ID选择器， 但是他们都是静态的----代表着他们第一次显示之后，不会再改变文档样式。</p>

<ul>
  <li>动态伪类</li>
  <ul>
    <li><strong>:focus</strong></li>
    <p>:focus表示获得焦点的元素（如表单输入）。当用户点击或触摸元素或通过键盘的 “tab” 键选择它时会被触发。</p>
    <li><strong>:hover</strong></li>
    <p>:hoverCSS伪类适用于用户使用指示设备虚指一个元素（没有激活它）的情况。这个样式会被任何与链接相关的伪类重写，像:link, :visited, 和 :active等。</p>
    <li><strong>:active</strong></li>
    <p>:active 伪类匹配被用户激活的元素。它让页面能在浏览器监测到激活时给出反馈。当用鼠标交互时，它代表的是用户按下按键和松开按键之间的时间。例如鼠标指针停留在一个超链接上，如果点击鼠标，就会激活这个超链接。</p>
  </ul>
</ul>

```css
a:link { color: navy; }
a:visited { color: gray; }
a:hover { color: red; }
a:active { color: yellow; }
```

<p>🌰：当然这里不仅仅是可以改变伪类的颜色，也可以改变其他样式，比如<strong>:hover</strong>时候改变字体的大小等</p>