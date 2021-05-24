---
title: 'C语言的作用域'
date: 2020-04-02 08:30
updated: 2020-04-02 08:30
index_img: ./blog-img/NewC.png
categories: C语言
tags: C语言
---

### C语言的作用域

>C语言在三个地方可以申明变量：
>
>	1.	在函数块内部局部变量；
> 	2.	在所有函数的全局变量；
> 	3.	在形式参数 的函数参数定义中；

##### 局部变量

<p>在某个函数或块的内部声明的变量称为局部变量。它们只能被该函数或该代码块内部的语句使用。局部变量在函数外部是不可知的。</p>

```c
#include <stdio.h>
int main ()
{
  /* 局部变量声明 */
  int a, b;
  int c;
 
  /* 实际初始化 */
  a = 10;
  b = 20;
  c = a + b;
  printf ("value of a = %d, b = %d and c = %d\n", a, b, c);
  return 0;
}
```

##### 全局变量

<p>全局变量是定义在函数外部，通常是在程序的顶部。全局变量在整个程序生命周期内都是有效的，在任意的函数内部能访问全局变量。</p>

```c
#include <stdio.h>
/* 全局变量声明 */
int g;
 
int main ()
{
  /* 局部变量声明 */
  int a, b;
 
  /* 实际初始化 */
  a = 10;
  b = 20;
  g = a + b;
 
  printf ("value of a = %d, b = %d and g = %d\n", a, b, g);
  return 0;
}
```

##### 形式参数

<p>函数的参数，形式参数，被当作该函数内的局部变量，如果与全局变量同名它们会优先使用。</p>

```c
#include <stdio.h>
 
/* 全局变量声明 */
int a = 20;
 
int main ()
{
  /* 在主函数中的局部变量声明 */
  int a = 10;
  int b = 20;
  int c = 0;
  int sum(int, int);
 
  printf ("value of a in main() = %d\n",  a);
  c = sum( a, b);
  printf ("value of c in main() = %d\n",  c);
 
  return 0;
}
 
/* 添加两个整数的函数 */
int sum(int a, int b)
{
    printf ("value of a in sum() = %d\n",  a);
    printf ("value of b in sum() = %d\n",  b);
 
    return a + b;
}
```

>注意⚠️：
>
>​	在定义局部变量的时候，系统不会赋初始值；但是在全局变量中，那么就有初始值，具体如下：

| 数据类型 | 全局变量初始值 |
| -------- | -------------- |
| int      | 0              |
| char     | '\0'           |
| float    | 0              |
| double   | 0              |
| pointer  | NULL           |

