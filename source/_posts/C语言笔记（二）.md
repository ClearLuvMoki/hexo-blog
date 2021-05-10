---
title: 'C变量'
date: 2020-04-01 09:08
updated: 2020-04-01 09:08
index_img: ./blog-img/NewC.png
categories: C语言
tags: C语言
---

### C变量

![](https://moki-blog.oss-cn-chengdu.aliyuncs.com/blogImg/cDataType.png)

<p>变量定义就是告诉编译器在何处创建变量的存储，以及如何创建变量的存储。变量定义指定一个数据类型:</p>

```c
/*语法, type 必须是一个有效的 C 数据类型，variable_list 可以由一个或多个标识符名称组成，多个标识符之间用逗号分隔。*/
type variable_list;
// 例子
int    i, j, k;
char   c, ch;
float  f, salary;
double d;
/*变量可以在声明的时候被初始化（指定一个初始值）*/
type variable_name = value;
int d = 3, f = 5;    				// d 和 f 的声明与初始化
int d = 3, f = 5;           // 定义并初始化 d 和 f
char x = 'x';               // 变量 x 的值为 'x'
```

### C中的变量声明

>变量的声明有两种情况：
>
>	1.	一种是需要建立存储空间的。例如：int a 在声明的时候就已经建立了存储空间。
> 	2.	另一种是不需要建立存储空间的，通过使用extern关键字声明变量名而不定义它。 例如：extern int a 其中变量 a 可以在别的文件中定义的。

```c
extern int i; 	//声明，不是定义
int i; 					//声明，也是定义
```

```c
#include <stdio.h>
int x;
int y;
int addNum()
{
  // 函数内声明变量 x 和 y 为外部变量
  extern int x;
  extern int y;
  // 给外部变量（全局变量）x 和 y 赋值
  x = 1;
  y = 2;
  return x + y;
}
int main()
{
  int result;
  // 调用函数 addNum
  result = addNum();
  printf("result是%d\n", result);
  return 0;
}
```

<hr/>

### C常量

<p>常量是固定值，在程序执行期间不会改变。这些固定的值，又叫做<strong>字面量</strong>。</p>

<p>常量可以是任何的基本数据类型，比如整数常量、浮点常量、字符常量，或字符串字面值，也有枚举常量。</p>

### 整数常量

<p>整数常量可以是十进制、八进制或十六进制的常量。前缀指定基数：0x 或 0X 表示十六进制，0 表示八进制，不带前缀则默认表示十进制。</p>

<p>整数常量也可以带一个后缀，后缀是 U 和 L 的组合，U 表示无符号整数（unsigned），L 表示长整数（long）。后缀可以是大写，也可以是小写，U 和 L 的顺序任意。</p>

```c
85         /* 十进制 */
0213       /* 八进制 */
0x4b       /* 十六进制 */
30         /* 整数 */
30u        /* 无符号整数 */
30l        /* 长整数 */
30ul       /* 无符号长整数 */
```

### 浮点常量

<p>浮点常量由整数部分、小数点、小数部分和指数部分组成。您可以使用小数形式或者指数形式来表示浮点常量。</p>

```c
3.14159       /* 合法的 */
314159E-5    /* 合法的 */
0.31415E2     /* 合法的 */
510E          /* 非法的：不完整的指数 */
210f          /* 非法的：没有小数或指数 */
.e55          /* 非法的：缺少整数或分数 */
```

### 字符常量

<p>字符常量是括在单引号中，例如，'x' 可以存储在 **char** 类型的简单变量中。</p>

<p>字符常量可以是一个普通的字符（例如 'x'）、一个转义序列（例如 '\t'），或一个通用的字符（例如 '\u02C0'）。</p>

| 转义序列 | 含义            |
| -------- | --------------- |
| \ \      | \字符           |
| \ '      | '字符           |
| \ "      | "字符           |
| \ a      | 警报铃声        |
| \ b      | 退格键          |
| \ f      | 换页符          |
| \ n      | 换行符          |
| \ r      | 回车            |
| \ t      | 水平制表符(tab) |
| \ v      | 垂直制表符      |

### 字符串常量

<p>字符串字面值或常量是括在双引号 "" 中的。一个字符串包含类似于字符常量的字符：普通的字符、转义序列和通用的字符。</p>

<p>⚠️：定义常量，一般是定义成大写！</p>

>在C语言中，可以使用两种方式定义常量：
>
> 1. 使用<strong>#define</strong>预处理器；
>
>    语法： #define identifier value
>
>    注意： 这里末尾没有分号，在谭浩强的《C语言程序设计》中，这个被叫做符号常量；
>
> 2. 使用<strong>const</strong>关键字；
>
>    语法：const type variable = value;
>
>    注意： 使用const只能声明和赋值同时完成，不能分步完成，或者只是声明不赋值；

```c
#include <stdio.h>

#define PI 3.14
int main()
{
  printf("PI=%f\n", PI);
  return 0;
}
```

```c
#include <stdio.h>
int main()
{
  const int A = 10;
  const int B = 20;
  const char NewLine = '\n';
  int num;
  num = A * B;
  printf("num=%d", num);
  printf("%c", NewLine);
  return 0;
}
```

