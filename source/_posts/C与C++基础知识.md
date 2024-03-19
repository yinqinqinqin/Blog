---
title: C与C++基础知识
---



#### 字符串赋值

##### char* 赋值

```c++
char* temp1;
char temp2[24]="hello world";
temp1 = temp2;

char* temp3="hello world"; //error  C++禁止该赋值方式
```

#### 打印

```c++
printf("%d",temp); //打印十进制的整数类型

int temp1=10;
char* temp2="hello world";
printf(temp1);//error printf支持const char* 类型，不支持int类型
printf(temp2);//success 与printf("%s",temp2);一样

```

#### strcpy

```c++
strcpy(str1,str2)//将str2复制给str1   前提：sizeof(str1)>sizeof(str2);
    
```

#### 局部变量

```c++

char* GetMemory()
{
    char p[] = "hello world";//局部变量
    return p;
}

int main()
{
	char* str = NULL;
	str = GetMemory();
	
	printf(str);
	return 0;
}
```

## 内存模型

堆：程序员自己申请和销毁的内存空间

栈：编译器自动分配释放，参数，局部变量

自由存储区：由malloc/free 申请或者销毁的内存分布在堆区，由new/delete申请的内存在自由存储区

静态/全局存储区:全局变量和静态变量被分配到同一块内存中

常量存储区：存放常量的区间，如字符串常量等，注意在常量区存放的数据一旦经初始化后就不能被修改

#### 内存空间分配

##### new和malloc区别

由malloc/free 申请或者销毁的内存分布在堆区，由new/delete申请的内存在自由存储区。

1.new、delete是C++中的操作符，而malloc和free是标准库函数。操作符可以在类的内部重载，malloc/free不行，唯一的关联只是在默认情况下new/delete调用malloc/free

2.malloc/free(只是分配内存，不能执行构造函数，不能执行析构函数)，new/free。

3.new返回的是指定类型的指针，并且可以自动计算所申请内存的大小。而 malloc需要我们计算申请内存的大小，并且在返回时强行转换为实际类型的指针。

## 关键字

### using

1. 定义别名： 类型别名和类型名字等价，typedef和using定义的别名在语义上等效。using的可读性更好。//建议使用using
2. 定义模版别名：使用using给模版指定别名更灵活。

### final和override

final 限制某个类不能被继承或某个函数不能被重写   如果使用final关键字修饰函数，**只能修饰虚函数**    并且要把final关键字写在**类或者函数的后面**。

override       确保派生类中声明的重写函数与基类中的虚函数有相同的名字,位置与final一样。

### 静态断言static_assert

### 空指针类型nullptr

NULL字面意思为0，与0一样，会产生二义性。

nullptr专门用于初始化空类型指针，nullptr可以隐式转化为不同类型的指针，(通用指针void*) 

### 常量表达式修饰符：constexpr

通常建议将`const`和`constexpr`的功能区分，`表达“只读”语义用const， 表达“常量”语义用constexpr`。在表达常量语义时，const和constexpr等价，都在程序的编译阶段得到运算结果。

### const（引用）

将参数定义为指针或引用，就不用构造临时对象了

```c++
func(const int& a)//该地址的值不可变，地址可变

a = 10;

const int* a    //a的地址的值不可改变，a的地址可以改变

const int a*    

```

引用与指针的区别：

指针可以为空，引用不能而且引用必须被初始化，

指针初始化之后可以改变，引用不能，

指针大小32位下为4，引用为对象的大小

作为参数，指针传入实参地址，引用传入实参本身

## 运算符重载

#### 重载规则

重载运算符必须符合语言语法
不能重载对内部c++数据类型进行操作的运算符（例如不能重载二元浮点减法运算符）
不能创建新的运算符
不能重载下面的运算符：
. 类成员选择运算符
.*成员指针运算符
:: 作用域运算符
?:条件表达式运算符
除此之外的运算符都可以被重载，并且只有“=”的重载函数不能被继承
重载运算符要保持原有的基本语义不变

```c++
/*  单目运算符  */
//++
Clock& operator++()//前置++  返回的是一个左值
Clock operator ++ (int);//后置++    返回的是一个右值
/*  双目运算符  */

// +：重载为成员函数时：只有一个形参
  Complex operator + (const Complex &c2) const;
// +：重载为非成员函数时：两个参数，且函数设为友元函数
  friend Complex operator+(const Complex &c1, const Complex &c2);
```



## C++泛型算法

泛型算法一般定义在头文件`algorithm`中

```c++
/*	find	*/

    auto it1 = find(nums.begin(), nums.end(), val1);//找与val1相等的元素
    if(it1 != nums.end())
        cout<<*it1<<endl;
    else
        cout<<"can not find"<<endl;

/*	copy	*/
/**将nums1[1]-nums[6]范围内的内容复制给nums2[2]
*
*nums1 = {1,2,3,4,5,6,7,8}
*nums2 = {0,0,0,0,0,0,0,0}
*
*after nums2 = {0,0,2,3,4,5,6,7,0};
*/
auto res = copy(nums1.begin() + 1, nums1.begin() + 6, nums2.begin() + 2);

/*	sort	*/
sort(num.begine(),num.end());//默认从小到大排序//num = 1,2,3,4,5,6
sort(nums.begin(), nums.end(), [](int& a, int& b) { return a > b; });//第三个参数自定义规则，传入一个lambdad表达方便一些,num=6,5,4,3,2,1

/*	count	*/
//计数
auto it = count(nums.begin(),nums.end(), val);//查找val,返回找到的个数
/*	replace	*/
//替换
replace(nums.begin(), nums.end(),initval, reval);//在范围内将initval替换成reval
/*	reverse	*/
reverse(nums.begin(), nums.end());//范围内的元素反转
/*	unique	*/
//清楚相邻重复的元素，想要清楚全部需要排序
//重复的元素被替换到最后，返回这些元素之前的迭代器，使用erase删除这些元素
    auto new_end = unique(nums.begin(),nums.end()); //注意unique的返回值
    a.erase(new_end,nums.end());//使用erase删除重复的元素
```



## C++容器

### 顺序容器

#### vector

##### deque

##### list

### 关联容器

#### set

#### map

map容器的[数据结构](https://so.csdn.net/so/search?q=数据结构&spm=1001.2101.3001.7020)也采用红黑树来实现的，插入元素的键值不允许重复



#### vector容器扩容过程：

vector是一个动态数组，每次插入是按照1，2，4，8，16，二倍扩容。扩容后是一片新的内存，需要把旧内存空间中的所有元素都拷贝进新内存空间中去，之后再在新内存空间中的原数据的后面继续进行插入构造新元素，并且同时释放旧内存空间，并且，由于vector 空间的重新配置，导致旧vector的所有迭代器都失效了。

**注意:** GCC编译器二倍扩容，G++编译器1.5倍扩容

1.5倍优于2倍：二倍扩容释放的内存连接起来都小于将要申请的内存

#### vectory容器的使用

```c++
 1 #include <iostream>
 2 #include <vector>
 3 #include <algorithm>
 4 using namespace std;
 5 
 6 // unique_ptr::get vs unique_ptr::release
 7 int main() 
 8 {
 9     //初始化
10     vector<int> vec;//声明，未初始化
11     vector<int> vec1(2, 5);//2个5 
12     vector<int> vec2 = { 1, 2, 3, 4, 5 };//直接初始化

13     //读取元素
14     cout << "第2个元素: " << vec2[1] << endl;
15     cout << "首元素: " << vec2.front() << endl;
16     cout << "尾元素: " << vec2.back() << endl;

17     //插入元素
18     vec1.insert(vec1.begin(), 999);//para1-插入位置，要迭代器即指针，para2-插入内容
19     vec2.push_back(888);//尾部插入
20     vec2.pop_back();//删除尾部，类似于stack，所以有时候也可以把vector当stack用

21     //删除元素
22     vec2.erase(vec2.end()-1);//参数也是迭代器类型，所以使用insert和erase时，最好用iterator来遍历
		vec2.remove(5);	
     
23     //排序
24     sort(vec2.begin(), vec2.end());//给出首位指针
25     sort(vec2.begin(), vec2.begin()+3);//甚至这样也可以，因为iterator本身就是类型指针
26 
27     //遍历--下标索引访问
28     cout << "vec1 : " ;
29     for (int i = 0; i < vec1.size(); ++i)
30     {
31         cout << vec1[i] << " ";
32     }
33 
34     //遍历--迭代器指针访问
35     cout << "\nvec2 : ";
36     vector<int>::iterator it;
37     for (it=vec2.begin(); it != vec2.end(); ++it)
38     {
39         cout << *it << " ";
40     }
41　　　//使用指针遍历vector
　　　　auto vec = new vector<int>(10, 8);
　　　　for(int i=0; i<vec->size(); i++)
　　　　　　cout << (*vec)[i] << "  ";
		//for循环遍历
     for(auto i:vec)//需要被循环的数组有begine和end
     {
         cout << i << endl;
     }
     
     //查找容器中的元素
     auto it =find(vec.begin,vec.end,temp);//vector<int>::iterator it =find(vec.begin,vec.end,temp);
     if(it != vec.end())
		cout<<*it<<endl;
	else
		cout<<"can not find"<<endl;

41     return 0;
42 }
```

## STL的迭代器

```c++
std::vector<int> ::iterator it;     //it能读写vector<int>的元素
std::vector<int>::const_iterator it;//it只能读vector<int>的元素，不可以修改vector<int>中的元素
```

## 构造函数和析构函数

### 同作用域下。多个对象构造顺序和析构

先构造后析构

### 全局对象什么时候构造与析构



### 静态对象什么时候构造

全局：

局部：

## 构造函数初始化列表

成员变量是引用

成员变量是常量

成员对象没有默认构造函数

基类没有默认构造函数

```;
class A
{
	A():b(x),a(b){}
    a
    b
}
A test(100,101);
a---->???
    b---------->100
```

## 拷贝构造函数

### **调用时机**

const和&的作用

### 深拷贝和浅拷贝

**浅拷贝：**简单的赋值拷贝操作。

**深拷贝：**在堆区重新申请空间，进行拷贝操作。

## 移动构造函数（右值引用）

把临时对象的资源转移到将要构造的对象中去

## 继承中的构造函数和析构函数

构造函数和析构函数不能被继承

不能处理派生类新增的成员

派生类名(参数):基类名{参数}

{

}

## 虚函数和构造函数和析构函数

构造函数不可以是虚函数

虚函数---动态绑定

调用虚函数---->找到指针实际指向的对象------>虚函数表指针---->虚函数表------->虚函数

析构函数建议设置为虚函数

# 右值引用

右值：保存在内存的常量存储区中的值

左值：局部变量保存在栈区，全局变量保存在静态全局变量区

```c++
/*  引用  */
int num = 10;
int &b = num; //正确
int &c = 10; //错误  因为该地址在常量存储区中


int num = 10;
const int &b = num;//正确
const int &c = 10;//正确 添加const保证了不会修改该地址的值

/*   右值引用(C++11)   */ 
//使用  &&  表示，常用于移动构造函数

int num = 10;
//int && a = num; //右值引用不能初始化为左值，只能使用右值进行初始化
int && a = 10;
 
int && a = 10;//右值引用可对右值进行修改
a = 100;
cout << a << endl;
//程序输出结果为 100。

const int&& a = 10;//编译器不会报错，右值不能修改将变得毫无意义 


```

## 多态

#### 实现多态的条件：

有继承关系；

子类重写父类的方法；

父类指针指向子类对象；

​												函数重载

​					静态多态------->

多态----->								泛型编程（模板编程）			

​					动态多态--------> 虚函数

##### 静态绑定

该绑定发生在**编译期**

##### 动态绑定（虚函数）

该绑定发生在**运行期**，虽然降低了运行效率，但是实现了多态

父类中的函数没有virtual声明，则调用父类的方法，即静态绑定

父类中的函数有virtual声明，则绑定子类的方法，子类同名函数默认为virtual虚函数，不管声明与否



#### 指针问题

##### 一、父指针指向子类对象

##### 二、子类指针指向父类对象



## 类型强制转换

C++11四种强制转换

static_cast

const_cast



## 智能指针

从比较简单的层面来看，智能指针是RAII(Resource Acquisition Is Initialization，资源获取即初始化)机制对普通指针进行的一层封装。这样使得智能指针的行为动作像一个指针，本质上却是一个对象，这样可以方便管理一个对象的[生命周期](https://so.csdn.net/so/search?q=生命周期&spm=1001.2101.3001.7020)

#### 强指针，弱指针

- **强智能指针**：资源每被强智能指针引用一次，引用计数+1，释放引用计数-1，如shared_ptr;
- **弱智能指针**：仅仅起到观察作用，观察对象释放还存在，不改变资源的引用计数，也就是说对象的引用计数是否等于0,如weak_ptr.

C++项目指针的初始化上

  1. 原则上只使用智能指针，不用普通指针，风格更加统一

  2. 强指针的使用范围：局部变量、子对象指针、可影响其生命周期的对象指针

   该条即是利用强指针进行资源回收，不需要再人工计算new和delete，一个对象在何处（父类中或函数中）创建，就在何处（父类析构或函数结束）回收。

  3. 弱指针的使用范围：父对象指针、某些不能影响其生命周期的对象指针

   该条一是避免强指针循环依赖，二是保障线程安全。其他对象成员不是在该类中创建，则不需要该类负责回收，因此使用弱指针。


## 虚函数

## 大端格式和小端格式

大端格式：高地址存在低字节，低地址存在高字节

小端格式：低地址存在低字节，高地址存在高字节



