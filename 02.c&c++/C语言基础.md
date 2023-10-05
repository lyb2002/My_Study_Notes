# C语言

 ### 1、编译过程

C程序编译步骤：

C代码编译可执行程序经过4步：

1. 预处理：宏定义展开、头文件展开、条件编译等，同时将代码中的注释删除，这里并不会检查语法。
2. 编译：检查语法，将预处理后的文件编译转成汇编文件（将C语言转换为汇编语言）
3. 汇编：将汇编文件生成目标文件（二进制文件）（将汇编语言转换为机器语言）
4. 链接：C语言写的程序是需要依赖各种库的，所以编译之后还需要把库链接到最终的可执行程序中去。



gcc编译过程：

1、分布编译

```bash
# 预处理
gcc -E hello.c -o hello.i
# 编译
gcc -S hello.i -o hello.s
# 汇编
gcc -c hello.s -o hello.o
# 链接
gcc hello.o -o hello
```

| 选项       | 含义                        |
| ---------- | --------------------------- |
| -E         | 只进行预处理                |
| -S（大写） | 只进行预处理和编译          |
| -c（小写） | 只进行预处理、编译和汇编    |
| -o file    | 指定生出的输出文件名为 file |

| 文件后缀 | 含义                |
| :------: | ------------------- |
|    .c    | C语言源文件         |
|    .i    | 预处理后的C语言文件 |
|    .s    | 编译后的汇编文件    |
|    .o    | 编译后的目标文件    |



## 2、关键字

32个关键字：

| auto     | break  | case    | char     | const  | continue |
| -------- | ------ | ------- | -------- | ------ | -------- |
| default  | do     | double  | else     | enum   | extern   |
| float    | for    | goto    | if       | int    | long     |
| register | return | short   | signed   | sizeof | static   |
| struct   | switch | typedef | unsigned | union  | void     |
| volatile | while  |         |          |        |          |

9个控制语句：

| if()~else~ | for()~   | while()~ |
| ---------- | -------- | -------- |
| do~while() | continue | break    |
| switch     | goto     | return   |



System函数

```c
#include<stdlib.h>

int main(){
    system("notepad");
    system("pause");
    return 0;
}
```



## 3、内存四区和汇编

内存四区：

- 代码区
- 数据区
- 栈区
- 堆区

  

汇编语言：

```c
int a;
int b;
int c;

__asm
{
    mov a, 10
    mov b, 20
    mov eax, a
    add eax, b
    mov c, eax
}
```

- mov：移动
- add：添加
- push：压栈
- pop：出栈
- call：调用



寄存器名字：

| 8位  | 16位 | 32位 | 64位 |
| :--: | :--: | :--: | :--: |
|  A   |  AX  | EAX  | RAX  |
|  B   |  BX  | EBX  | RBX  |
|  C   |  CX  | ECX  | RCX  |
|  D   |  DX  | EDX  | RDX  |



## 4、







