# 函数

- 声明方法：


    返回值  函数名(参数1,参数2,...);
    例如：
    
    int add(int num1, int num2);
    
    int add(int,int); //注意:可以省略具体形参名
    
- 定义方法:


    返回值 函数名(参数1,参数2,...)
    {
        语句1;
        语句2;
        ...
        
        返回值表达式;
    }
    
    例如：
    
    int add(int num1, int num2)
    {
        return num1+num2;
    }
    
- 调用方法：
    
    
    函数名(参数1,参数2,...);
    
    例如：
    
    add(100,200);

**1、名词解释**
- 主调函数：调用者
- 被调函数：被调用者
- 回调函数：
- 可重入函数

- 形参：形势参数，函数声明或定义时用来接收实参的参数名
- 实参：实际参数，函数调用时传递给被调用函数的参数名

**2、函数传参**
- 值传参：直接将参数的值传递给被调函数，被调函数获得的是实际参数的副本，因此被调函数无法更改主调函数实参的值
- 地址传参：将实参的地址传递给被调函数，被调函数获得是实参的地址，因此被调函数可以通过该地址访问或修改实参的值
- 全局变量传参：函数本身不需要传参，通过共享全局变量

**3、常用C库函数**
- 输入输出类：getchar putchar gets puts printf scanf
- 字符串操作类： strlen strcpy strcat strncpy strncat atoi strtok sprintf sscanf
- 内存操作类：malloc free memset bzeor memcpy memmove
- 数据计算类： sqrt sin cos rand
