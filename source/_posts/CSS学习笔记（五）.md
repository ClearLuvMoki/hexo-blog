---
title: '伪类和伪元素(二)'
date: 2020-03-27 09:05
updated: 2020-03-27 09:05
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### 伪类和伪元素(二)

##### 选择第一个子元素

<p>使用另外一个静态伪类<strong>:first-child</strong>来选择元素的第一个子元素。（之前所说的<strong>:link和:visited</strong>也是静态伪类）</p>

<p>先看下面的代码:</p>

```html
<div>
  <p>
    这是p层<em>这是em</em>
  </p>
</div>
```

```css
/*这里的含义是当p作为第一个子元素的时候，该样式如下*/
p:first-child { color: red; }
```

<p><strong>:first-child</strong>表示在一组兄弟元素中的第一个元素<br/><strong>Note：</strong>最初定义时，:first-chlid所选元素必须有一个parent。而从选择器 Level 4 开始，parent不再是必须的。</p>

##### 根据语言选择

<p>在某些情况下，可以根据元素的语言来选择，可以使用<strong>:lang()伪类。</strong>有点类似于属性选择器：</p>

<p>🌰：比如想把所有的法语元素变成斜体：</p>

```html
<p lang="fr">这是fr</p>
<p lang="en">这是en</p>
```

```css
/*那么它会把第一个p元素中的内容变成斜体*/
*:lang(fr) { font-style: italic; }
```

##### 结合伪类

<p>将伪类结合起来更方便我们展示更好的效果:</p>

```css
/*这里是a元素（具有href）点击前鼠标移动上去的样式*/
a:link:hover { color: red; }
 /*这里是a元素（具有href）点击后鼠标移动上去的样式*/
a:visited:hover { color: blue; }
/*这里是a元素（具有href）并且lang属性为en的a元素，点击前鼠标移动上去的样式*/
a:link:hover:lang(en) { color: green; } 
/*这里是a元素（具有href）并且lang属性为en的a元素，点击后鼠标移动上去的样式*/
a:visited:hover:lang(en)  { color: yellow; } 
```