# Lecture Note 1
* POP (面向过程) 难以复用
* OOP (面向对象) 易于复用
## Linux Bases
* `sudo`: as administrator
* `vi`: edit files
* `rwx`: read, write, execute
## Command-line Arguments 命令行参数
cinfiguration file 配置文件

save ints in file & rerad.

```C++
int main(int argc, char *argv[], char *envp[])
{
    // write sth here...
    return 0;
}
```
* `argc`: `argv` 的参数个数
* `envp`: 环境变量

## Complilation and multiple-file projects 多文件工程
* Translators 翻译器
* Interpreter 解释器
* Complier 编译器：code -> machine code 机器代码

### Declaration 声明 vs. Definition 定义
declaration: `extern`

definition: only once.

### Preprocessor directive 预编译命令
`#include`
```C++
#include <systemheaders>
#include "functions.h"
```
include related .h in all the source files.

## make and makefile
* 直接编译
  ```
  g++ main.cpp sum.cpp
  ```
* 分段编译

  relocatable object file (.o/.obj)
  ```
  g++ -c main.cpp -o main.o
  ```
  executable object file (.exe) linker 
  ```
  g++ main.o sum.o -o test.exe
  ```
* makefile
    ```
    test.exe: product.o sum.o main.o
        g++ product.o sum.o main.o -o test.exe
    product.o: product.cpp functions.h
        g++ -c product.cpp -o product.o
    sum.o: sum.cpp functions.h
        g++ -c sum.cpp -o sum.o
    main.o: main.cpp functions.h
        g++ -c main.cpp -o main.o
    ```
## Library 库
archive-format (.a) 档案规划

静态库/动态库