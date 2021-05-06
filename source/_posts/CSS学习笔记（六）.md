---
title: '伪元素选择器'
date: 2020-03-27 19:13
updated: 2020-03-27 19:13
index_img: ./blog-img/css.jpg
categories: CSS
tags: CSS
---

### 伪元素选择器

##### 设置首字母的样式

<p><strong>:first-letter</strong>设置了<strong>块级元素</strong>首字母的样式，并且仅仅对这首字母设置样式：</p>

```css
p:first-letter { color: red; }
```

##### 设置第一行的样式

<p><strong>:first-line</strong>设置影响文本中第一行的样式:</p>

```css
p:first-line { font-size: 200%; }
```

<p>⚠️：在<strong>CSS2中（以前）:first-letter 和:first-line</strong>只能使用在<strong>块级元素</strong>中.在<strong>CSS2.1之后:first-line</strong>可以使用在任何元素中.</p>

<p>⚠️：所有的伪元素选择器应该放在选择器的最后面，如下是不合规则的：</p>

```css
/*这样写是不符合规则的,含有伪元素的选择器应该出现在最后*/
p:first-line em { font-size: 200%; }
```



##### ⭐️设置之前和之后的样式

<p>CSS2.1开始允许插入生成样式,使用<strong>:before和:after</strong>设置样式:</p>

```css
/*设置在文字前出现银色的中括号*/
p:before { content: "]]"; color: silver; }
/*这是在某元素之后出现的样式*/
body:after { content: " The End"; }
```

