---
title: 'C判断'
date: 2020-04-01 14:15
updated: 2020-04-01 14:15
index_img: ./blog-img/NewC.png
categories: C语言
tags: C语言
---

### C判断

<p>C 语言把任何<strong>非零和非空的值假定为true</strong>，<strong>把零或null假定为false</strong>。</p>

### if 和 if.. else..语句

<p>语法：</p>

```c
if(boolean_expression)
{
   /* 如果布尔表达式为真将执行的语句 */
}

if(boolean_expression1)
{ /*语句1*/ }
else if (boolean_expression2) 
{ /*语句2*/ }
else
{ /*语句3*/ }
```

<p>当存在嵌套的if语句时候，else总是寻找它上面未匹配的if语句。</p>

>- 一个 if 后可跟零个或一个 else，else 必须在所有 else if 之后。
>- 一个 if 后可跟零个或多个 else if，else if 必须在 else 之前。
>- 一旦某个 else if 匹配成功，其他的 else if 或 else 将不会被测试。

### switch 语句

语法：

```c
switch(expression){
    case constant-expression  :
       statement(s);
       break; /* 可选的 */
    case constant-expression  :
       statement(s);
       break; /* 可选的 */
  
    /* 您可以有任意数量的 case 语句 */
    default : /* 可选的 */
       statement(s);
}
```

>- **switch** 语句中的 **expression** 是一个常量表达式，必须是一个整型或枚举类型。
>- 在一个 switch 中可以有任意数量的 case 语句。每个 case 后跟一个要比较的值和一个冒号。
>- case 的 **constant-expression** 必须与 switch 中的变量具有相同的数据类型，且必须是一个常量或字面量。
>- 当被测试的变量等于 case 中的常量时，case 后跟的语句将被执行，直到遇到 **break** 语句为止。
>- 当遇到 **break** 语句时，switch 终止，控制流将跳转到 switch 语句后的下一行。
>- 不是每一个 case 都需要包含 **break**。如果 case 语句不包含 **break**，控制流将会 *继续* 后续的 case，直到遇到 break 为止。
>- 一个 **switch** 语句可以有一个可选的 **default** case，出现在 switch 的结尾。default case 可用于在上面所有 case 都不为真时执行一个任务。default case 中的 **break** 语句不是必需的。