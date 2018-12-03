### 1、预处理指令
    
凡事以‘#’开头的行，都属于预处理指令：`include define ifndef endif` 等

    例如：
        #include <stdio.h>
        #define N 10    
### 2、定义语句    

结构体类型定义、别名定义、全局变量定义等。

    例如：    
        struct student{
            int id;
            int score;
        };
        
        typedef int int32;
        
        int value = 10;
        
### 3、声明语句

函数原型声明、全局变量声明等。

    例如：
        extern int fun(void);
        extern int value;
### 4、函数
指令的集合，C语言执行语句的基本单元，任何表达式都要被包含在函数内部。


    
