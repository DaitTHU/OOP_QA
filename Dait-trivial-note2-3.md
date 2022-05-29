# Lecture Note 2-3 
## Object and Class
1. Object 对象
   * static 静态：attribute 属性，status 状态
   * dynamic 动态：behavior 行为，function 功能
2. Class 类
   * abstruction 抽象
   * encapsulation 封装
   * inheritance 继承
   * polymorphism 多态
  
成员变量、成员函数

### `public`, `protected`, `private`
`publice` member function: interface 接口

`private`: only accseeible within menber functions.

类内声明，类外定义。

scope resolution operator `::` 范围解析

### `inline` function 内联函数
to improve efficiency.
* declared in .h
* simple enough (<10 lines)
* no contain loops or recursive functions
  
### `this` 当前 object 的地址指针
## Constructor and Destructor 构造函数和析构函数
Lifetime (生命期) or scope (作用域) of objects
* Constructor 构造函数 initialization 初始化
* Destructor 析构函数 cleanup 清除
### default constructor 缺省构造函数
default: without function arguments

default default constructor: by compiler, when no constructor is defined. (avoid)

`default` 关键词

### `explicit` 关键词
禁用 implicit type conversion 隐式类型转换

### delegating constructor 委托构造函数
depends on other constructors.

### Destructor
prepare-to-die menber function.

using `delete`

modern: `std::unique_ptr<>`, `std::shared_ptr<>`

DO NOT explicit call 不要显式调用 unless necessary.

## Stack vs. Heap 