# #define和typedef的区别

#define和typedef经常用于给一个对象取一个别名，以此增强程序的可读性，区别如下：

## （1）原理不同

#define的作用是在**预处理时**直接进行字符串的替换，不做正确性的检查。<br>
而typedef在**编译时**处理，是给结构体、变量、函数赋值一个别名。

## （2）操作对象不同

typedef用于给已存在的数据类型定义一个别名。<br>
#define不仅可以给数据类型取别名，还可以给常量、编译开关等取别名。

## （3）作用域不同

#define没有作用域的限制，只要是之前预定义过的宏，在以后的程序中都可以使用。<br>
而typedef有自己的作用域。

## （4）对指针的操作不同

~~~

#define INTPTR1 int*

typedef int* INTPTR2; 

INTPTR1 p1,p2;    //声明一个整形指针变量p1和整型变量p2  
 
INTPTR2 p3,p4;    //声明两个整形指针变量p3,p4

int a = 1;
int b = 2;
int c = 3;

const INTPTR1 p1 = &a;    //p1 是一个常量指针，即不可以通过p1去修改p1指向的变量的内容，但是p1可以指向其他变量。
const INTPTR2 p2 = &b;    //p2 是一个指针常量，不可以用p2再指向别的变量。  const INTPTR2 p2 == const(int *)
INTPTR2 const p3 = &c;    //同上

~~~
