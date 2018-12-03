### 1、关键字
C语言内置保留的符号，用作语法控制，组成了C语言的语法框架。

- 存储类：   `auto extern register static`
- 数据类型： `int char short long float double signed unsigned void`
- 控制语句： `if else for while do break continue switch case default goto return`
- 其他：`sizeof volatile const union struct typedef enum`

### 2、标识符
用户自定义的符号，用来标记变量、函数、类型等

标识符的定义规则：
    
        1）只能由英文大小写、下划线、数字组成。
        2）不能与关键字重名。
        3）不能以数字开头。
        4）长度限制（非标准）。

### 3、运算符
C语言内置的符号，用作计算。在使用时要非常注意优先级和结核性。

- 算术： `+ - * / %`
- 关系： `> >= == < <= !=`
- 逻辑： `&& || !`
- 位 ：   `& | ~ ^ << >>`
- 赋值： `= += -= *= /= %= >>= <<= &= ^= |=`
- 其他： `() [] -> . & *(类型) sizeof ++ -- + - ？: ,`

### 4、间隔符
空格、换行、制表、注释


### 5、标点
'' "" ; , () {} 