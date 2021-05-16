---
title: 'C循环'
date: 2020-04-01 16:47
updated: 2020-04-01 16:47
index_img: ./blog-img/NewC.png
categories: C语言
tags: C语言
---

### C循环

##### while 循环

```c
/*condition 可以是任意的表达式，当为任意非零值时都为 true。当条件为 true 时执行循环。 当条件为 false 时，退出循环，程序流将继续执行紧接着循环的下一条语句。*/
while(condition)
{
   statement(s);
}
```

##### do....while 循环

```c
/*do...while 循环与 while 循环类似，但是 do...while 循环会确保至少执行一次循环。*/
do
{
   statement(s);

}while( condition );
```

##### for循环

```c
/*init：设置初始值，只执行一次，可以为一个，零个或者多个设置初始值；*/
/*condition：循环表达式*/
/*increment： 循环的调整*/
/*以上三个参数都可以省略，但是分号不可以省略*/
for ( init; condition; increment )
{
   statement(s);
}
/*在C99中可以在设置初始值的时候同时声明*/
for(int a = 0; a <= 10; i ++) printf("%d", i);
```

##### 改变循环的状态

```c
/*	1. break, brea可以提前终止循环，结束循环体，但是break不可以单独使用，只能在循环语句和switch语句中 */
for(int a = 0; a <= 10; a++)
{
  if (a == 3) break; // 如果等于3， 则会结束循环
  printf("%d", a);
}
/*	2. continue, continue只是跳出本次循环，开始下一轮新的循环，提前结束本次循环*/
for(int a = 0; a <= 10; a++)
{
  if (a == 3) continue; // 如果等于3则不会输出3， 但是会继续下一轮循环
  printf("%d", a);
}
```

