---
title: C#基础知识
data: 2024-7-5 19:52:54
updated: 2024-7-5
tags: 
    - TA
    - Program
    - C#
categories: Program
description: C#基础知识
cover: https://yin-qin.oss-cn-shanghai.aliyuncs.com/XiaoYao/202403201546328.jpg
---

# C#基础知识

## 简介

- C#是微软公司发布的一种由C和C++衍生出来的面向对象的编程语言，它不仅去掉了 C++ 和 Java 语言中的一些复杂特性，还提供了可视化工具，能够高效地编写程序。

- C#是由C和C++衍生出来的一种安全的、稳定的、简单的、优雅的面向对象编程语言。它在继承C和C++强大功能的同时去掉了一些它们的复杂特性（例如没有宏以及不允许多重继承）。
- C#使得C++程序员可以高效的开发程序，且因可调用由 C/C++ 编写的本机原生函数，而绝不损失C/C++原有的强大的功能。因为这种继承关系，C#与C/C++具有极大的相似性，熟悉类似语言的开发者可以很快的转向C#。

## HelloWorld

```c#
namespace Hello
{
  internal class Program
  {
    static void Main(string[] args)
    {
      Console.WriteLine("Hello World!");
      Console.ReadLine();
    }
  }
}
```

## 基本语法

### 注释

```
//这是一个单行注释

/*
*	这是一个多行注释
*/
```

### 成员变量

```
int a = 1;//a是一个变量
```

### 实例化

```
Obeject r = new Obejct();
```

### 关键字

|     关键字     |                             作用                             |
| :------------: | :----------------------------------------------------------: |
|    **void**    |              用作方法的返回类型，指定不返回值。              |
|   **const**    |          指定字段或局部变量的值是常数，不能被修改。          |
|     **as**     |               转换操作符，若转换失败返回null。               |
|  **private**   |            访问修饰符，是允许访问的最低访问级别。            |
|   **public**   |            访问修饰符，是允许访问的最高访问级别。            |
|  **internal**  | 访问修饰符，允许在同一程序集的文件中内部类型和成员可以访问。 |
| **protected**  |         访问修饰符，允许在其所在类中可由派生类访问。         |
|    **try**     |     异常处理代码块的组成部分，包括可能会抛出异常的代码。     |
|   **catch**    |     定义一个代码块，在特定类型异常抛出时，执行块内代码。     |
|    **base**    |      用于访问被派生类或构造中的同名成员隐藏的基类成员。      |
|  **abstract**  |   标识一个可以扩展但不能被实体化的、必须被实现的类或方法。   |
|  **delegate**  | 指定一个声明为一种委托类型，委托把方法封装为可调用实体，能在委托实体中调用。 |
|   **event**    | 声明一个全新的事件。允许一个类或对象提供通知的成员，必须是委托类型。 |
|  **checked**   |    确保编译器运行时，检查整数类型操作或转换时出现的溢出。    |
| **unchecked**  |                        禁止溢出检查。                        |
|    **enum**    |                   枚举类型，特殊的值类型。                   |
|    **goto**    |          跳转语句，将程序执行重定向到一个标签语句。          |
|  **foreach**   |                            遍历。                            |
| **namespace**  |               定义一个逻辑组的类型和命名空间。               |
|    **ref**     |              标识一个参数值可能会受影响的参数。              |
|   **struct**   |                       可以声明值类型。                       |
|   **throw**    |                          抛出异常。                          |
|   **typeof**   |                 操作符，返回传入参数的类型。                 |
|  **virtual**   |                     标识可被覆载的方法。                     |
|   **using**    | 用于命名空间时，允许访问该命名空间中的类型而无需指定其全名。用于定义finalization操作的范围。 |
|   **static**   |                   声明静态变量或静态函数。                   |
|   **extern**   |                    声明在外部实现的方法。                    |
|   **object**   | 所有类型都是直接或间接从Object继承的，可以将任何类型的值赋给object类型的变量。 |
|  **volatile**  | 标识一个可被操作系统、某些硬件设备或并发线程修改的attribute。 |
|  **readonly**  |             标识一个变量的值在初始化后不可修改。             |
|   **params**   |                      声明一个参数数组。                      |
|  **operator**  |                    声明或多载一个操作符。                    |
| **interface**  |   将一个声明指定为接口类型，即实现类或构造必须遵循的合同。   |
|    **out**     | 标识一个参数值会受影响的参数，但在传入方法时，该参数无需先初始化。 |
|   **sizeof**   |          操作符，以byte为单位返回一个值类型的长度。          |
| **stackalloc** |              返回在堆上分配的一个内存块的指针。              |
|   **sealed**   | 防止类型被派生，防止方法和property被覆载。在声明中使用可以防止该类被其他类继承。 |
|   **unsafe**   |             标注包含指针操作的代码块、方法或类。             |
|  **override**  |                在派生类中声明对虚方法的重载。                |
|  **implicit**  | 定义一个用户定义的转换操作符。通常用来将预定义类型转换为用户定义类型或反向操作。隐式转换操作符必须在转换时使用。 |
|  **explicit**  | 一个定义用户自定义转换操作符的操作符。通常用来将内建类型转换为用户定义类型或反向操作。必须在转换时调用显式转换操作符。 |

## C#数据类型

- 值类型
- 引用类型
- 指针类型

### 值类型

值类型变量可以直接分配给一个值。它们是从类 System.ValueType 中派生的。

#### 整型

|  类型  |         示意         |                       范围                        |
| :----: | :------------------: | :-----------------------------------------------: |
| Sbyte  | 代表有符号的8位整数  |               数值范围从-128 ～ 127               |
|  Byte  | 代表有符号的8位整数  |                 数值范围从0～255                  |
| Short  | 代表有符号的16位整数 |               范围从-32768 ～ 32767               |
| ushort | 代表有符号的16位整数 |                 范围从0 到 65,535                 |
|  Int   | 代表有符号的32位整数 |          范围从-2147483648 ～ 2147483648          |
|  uint  | 代表有符号的32位整数 |               范围从0 ～ 4294967295               |
|  Long  | 代表有符号的64位整数 | 范围从-9223372036854775808 ～ 9223372036854775808 |
| Ulong  | 代表有符号的64位整数 |          范围从0 ～ 18446744073709551615          |
|  char  | 代表有符号的16位整数 |                数值范围从0～65535                 |

#### 浮点型

|  类型  |           范围           |
| :----: | :----------------------: |
| Float  |  1.5*10 -45～3.4* 10 38  |
| Double | 5.0*10 -324～1.7* 10 308 |

### 引用类型

#### 对象类型（Object）

对象（Object）类型 是 C# 通用类型系统（Common Type System - CTS）中所有数据类型的终极基类。Object 是 System.Object 类的别名。所以对象（Object）类型可以被分配任何其他类型（值类型、引用类型、预定义类型或用户自定义类型）的值。但是，在分配值之前，需要先进行类型转换。

##### 装箱和拆箱

当一个值类型转换为对象类型时，则被称为**装箱**；另一方面，当一个对象类型转换为值类型时，则被称为**拆箱**。

```
//装箱：值类型转换为对象类型
int val = 8;
object obj = val;//整型数据转换为了对象类型（装箱）

//拆箱：之前由值类型转换而来的对象类型再转回值类型
int val = 8;
object obj = val;//先装箱
int nval = （int）obj;//再拆箱
```

#### 动态类型

您可以存储任何类型的值在**动态数据类型**变量中。这些变量的类型检查是在**运行**时发生的。

```
//语法
dynamic <variable_name> = value;
//实例
dynamic d = 20;
```

#### 字符串型

字符串（String）类型 允许您给变量分配任何字符串值。字符串（String）类型是 System.String 类的别名。它是从对象（Object）类型派生的。字符串（String）类型的值可以通过两种形式进行分配：引号和 @引号。

```
//实例
string str = "runoob.com";
//@转义
string str = @"C:\Windows";
```

#### 指针类型

指针类型变量存储另一种类型的内存地址。

```
//语法
type* identifier;
//实例
char* cptr;
int* iptr;
```

### 类型转换

- **隐式类型转换** ：这些转换是 C# 默认的以安全方式进行的转换, 不会导致数据丢失。例如，从小的整数类型转换为大的整数类型，从派生类转换为基类。
- **显式类型转换** ：显式类型转换，即强制类型转换。通过用户使用预定义的函数显式完成的，显式转换需要强制转换运算符，而且强制转换会造成数据丢失。转换类型的范围大小和从属关系和隐式转换相反。显式转换可能会导致数据出错，或者转换失败，甚至无法编译成功。

```c#
//隐式类型转换
namespace TypeConvertion
{   class Class1
    {

    }

    class Class2 : Class1 //类Class2是类Class1的子类
    {

    }
    class Program
    {
        static void Main(string[] args)
        {
            int inum = 100;
            long lnum = inum; // 进行了隐式转换，将 int 型（数据范围小）数据转换为了 long 型（数据范围大）的数据
            Class1 c1 = new Class2(); // 这里也是隐式转换，将一个新建的 Class2 实例转换为了其基类 Class1 类型的实例 C1
        }
    }
}

//显式类型转换
namespace TypeConversionApplication
{
    class ExplicitConversion
    {
        static void Main(string[] args)
        {
            double d = 5673.74;
            int i;

            // 强制转换 double 为 int
            i = (int)d;
            Console.WriteLine(i);
            Console.ReadKey();
           
        }
    }
}//result 5673
```

## C#运算符

## C#运算符

### 算术运算符

```
+,-,*,/,%,++,--
```

### 关系运算符

```
==,!=,>,<,>=,<=
```

### 逻辑运算符

```
&&,||,!
```

### 位运算符

```
&,|,^
```

### 赋值运算符

```
=,+=,-=,*=,/=,&=,<<=,>>=,&=,^=,|=
```

### 其他运算符

```
sizeof(),typeof(),&,*,? :,is.as
```

## C#语法

### 判断语句

#### if 语句

一个 if 语句 由一个布尔表达式后跟一个或多个语句组成。

#### switch语句

一个 switch 语句允许测试一个变量等于多个值时的情况。

### 循环语句

### while循环

### for/foreach循环

### do..while循环

### break循环控制

### continue循环控制

## C#封装

**封装** 被定义为"把一个或多个项目封闭在一个物理的或者逻辑的包中"。在面向对象程序设计方法论中，封装是为了防止对实现细节的访问。

一个 访问修饰符 定义了一个类成员的范围和可见性。C# 支持的访问修饰符如下所示：

- public：所有对象都可以访问；

- private：对象本身在对象内部可以访问；
- protected：只有该类对象及其子类对象可以访问
- internal：同一个程序集的对象可以访问；
- protected internal：访问限于当前程序集或派生自包含类的类型。

## C#方法

一个**方法**是把一些相关的语句组织在一起，用来执行一个任务的语句块。

- 定义方法
- 调用方法

### C#数组

数组是一个存储相同类型元素的固定大小的顺序集合。

```
//初始化数组
double[] balance = new double[10];

//数组赋值
double[] balance = new double[10];
balance[0] = 4500.0;
double[] balance = { 2340.0, 4523.69, 3421.0};
int [] marks = new int[5]  { 99,  98, 92, 97, 95};
int [] marks = new int[]  { 99,  98, 92, 97, 95};
int [] marks = new int[]  { 99,  98, 92, 97, 95};
int[] score = marks;
```

## C#结构体

在 C# 中，结构体是**值类型数据结构**。

```c#
//定义结构体

struct Books
{
   public string title;
   public string author;
   public string subject;
   public int book_id;
};
//调用结构体
using System;
using System.Text;
namespace day01
{
   struct Books
    {
        public string title;
        public string author;
        public string subject;
        public int book_id;
    };
    class Program
    {
     
        static void Main(string[] args)
        {
            Books Book1;
            Book1.title = "C programming";
            Book1.author = "Nuha Ali";
            Book1.subject = "C programming Tutorial";
            Book1.book_id = 12345;
            Console.WriteLine("Book1 title:{0}", Book1.title);
            Console.WriteLine("Book1 author:{0}", Book1.author);
            Console.WriteLine("Book1 subject:{0}", Book1.subject);
            Console.WriteLine("Book1 book_id:{0}", Book1.book_id);
            Console.ReadKey();
           
        }
    }
}
```

- 结构可带有方法、字段、索引、属性、运算符方法和事件。

- 结构可定义构造函数，但不能定义析构函数。但是，您不能为结构定义无参构造函数。无参构造函数(默认)是自动定义的，且不能被改变。
- 与类不同，结构不能继承其他的结构或类。
- 结构不能作为其他结构或类的基础结构。
- 结构可实现一个或多个接口。
- 结构成员不能指定为 abstract、virtual 或 protected。
- 当您使用 New 操作符创建一个结构对象时，会调用适当的构造函数来创建结构。与类不同，结构可以不使用 New 操作符即可被实例化。
- 如果不使用 New 操作符，只有在所有的字段都被初始化之后，字段才被赋值，对象才被使用。

### 类 VS 结构

类和结构有以下几个基本的不同点：

- 类是引用类型，结构是值类型。
- 结构不支持继承。
- 结构不能声明默认的构造函数。