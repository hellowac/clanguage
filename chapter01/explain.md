
## 空白和注释

```c
/*
** 这个程序从标准输入中读取输入行并在标准输出中打印这些输出行
** 每个输入行的后面一行是该行内容的一部分
**
** 输入的第一行是一串列标号，串的最后以一个负数结尾。
** 这些列标号成对出现，说明需要打印的输入行的列的范围。
** 例如：0 3 10 12 -1 表示第0列到第3列，第10列到第12列的内容将被打印.
*/
```
更好的显示程序的结构.

- 注释以`/*`开始，以`*/`结束.
- 注释不能嵌套
- 注释一段代码可不能使用 `/*` 和 `*／` 如果代码内部中原先就有注释存在，这样做会出问题.
- 从逻辑上删除一段C代码，使用`#if`指令。

```c
#if 0
    statments
#endif
```

## 预处理指令

- #include <stdio.h>
- #include <stdlib.h>
- #include <string.h>
- #define MAX_COLS 20
- #define MAX_INPUT 1000

这5行为`预处理指令`. 他们由 `预处理器` 解释.

预处理器根据预处理指定对源码进行修改，然后把修改过的源代码递交给编译器.

\#include <stdio.h> 的内容将被逐字写到源文件的那个位置. stdlib.h 和 string.h 也是类似的.

stdio.h 是标准I/O库(Standard I/O Libaray)的函数包. 里面的函数用于执行输入和输出.

stdlib.h 定义了 EXIT_SUCCESS 和 EXIT_FAILURE 符号.

string.h 提供了操作字符串的函数.

\#define 定义了字面常量,通常使用大写，提醒它们并非普通常量. 所以定义的常量不能出现在有些普通变量可以出现的地方,比如 赋值符号的左边.

```
int read_column_numbers(int columns[], int max);
void rearrange(char *output, char const *input,
               int n_columns, int const columns[]);
```

这些声明被称为 `函数原型`(function prototype) , 它们告诉编译器这些以后将在源文件中定义的函数特征.[被调用时，编译器就能对它们进行准确性检查.]

const 变量，表示该函数将不会修改 函数调用者 所传递的这两个参数.

void 表示 函数并不返回任何值. 有时，无返回值的函数被称为 `过程(procedure)`

## main 函数

每个C程序都必须有一个main函数，作为程序的起点. int 表示 返回一个 整数值，关键字void表示函数不接受任何参数.

**n_columns = read_column_numbers(columns, MAX_COLS);**

在C中，数组是按`引用`(reference)形式传递的，也就是传址调用. 而标量和常量则是按`值`(value)传递.

实际上C函数的参数传递规则可以表述为：“所有传递给函数的参数都是按值传递的.” ， 但是数据传递时就会产生按引用传递的效果，将数字开始的地址传递了.

gets 函数从标准输入读取一行文本并把它存储于作为参数传递给它的数组中。 gets 函数丢弃换行符，并在该行的末尾存储一个NUL字节(一个NUL字节是指字节模式为全0的字节.类似'\0'这样的字符常量).

gets 函数返回一个非NULL值表示该行已被成功读取。

gets 函数被调用但事实上不存在输入行时，返回NULL值，表示它到达了输入的末尾（文件尾）。

C中不存在“字符串”数据类型，但有一个约定：字符串就是一串以NUL字节结尾的字符.NUL是作为字符串终止符，它本身并不被看做是字符串的一部分.

**字符串常量**(string literal)就是源程序中被双引号括起来的一串字符。如：“Hello”，在内存中占用6个字节的空间，顺序为H、e、l、l、o和NUL。

printf 函数执行格式化的输出.

**常用printf格式代码**

格式 | 含义
-----|-----
%d | 以十进制形式打印一个整数值.
%o | 以八进制形式打印一个整数值.
%x | 以十六进制打印一个整数值.
%g | 打印一个浮点数
%c | 打印一个字符
%s | 打印一个字符串
\n | 换行

## read_column_numbers 函数





















啊
