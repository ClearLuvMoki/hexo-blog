---
title: 'C数组'
date: 2020-04-01 18:50
updated: 2020-04-01 18:50
index_img: ./blog-img/NewC.png
categories: C语言
tags: C语言
---

### C数组

>C 语言支持**数组**数据结构，它可以存储一个**固定大小**的**相同类型**元素的顺序集合。

```c
// 语法 type arrayName [ arraySize ];
int a[3];
double balance[10];
// 初始化数组， 可以在定义完数组并且赋值，当{}中元素确定，可以省略[]中数组长度
double balance[5] = {1000.0, 2.0, 3.4, 7.0, 50.0};
=> double balance[] = {1000.0, 2.0, 3.4, 7.0, 50.0};
// 但是当我们{}中元素个数和[]中长度不一样的，其余元素默认是0
int balance[5] = {1, 2, 3};
printf("%d", balance[3]); // 0
```

>访问数组元素是通过数组名+下表索引访问
>
>​	arrayName [ index ]；
>
>在这里需要区别下定义数组和引用数组元素的区别：
>
>​	type arrayName [ arraySize ]; 在定义数组前面跟上了类型，[]中的数值代表的数组长度；
>
>​	arrayName [ index ]; 在引用数组元素的时候，没有跟上类型，并且[]中的是数组下标，下标是从0开始计算；

##### 二维数组

<p>多维数组最简单的形式是二维数组。一个二维数组，在本质上，是一个一维数组的列表。声明一个 x 行 y 列的二维整型数组，形式如下：</p>

```c
// 二维数组可以堪称一个矩形的方阵列
type arrayName [ x ][ y ];
// 初始化二维数组
int a[3][4] = {0,1,2,3,4,5,6,7,8,9,10,11};
// 访问二维数组的元素
int val = a[2][3];
```

