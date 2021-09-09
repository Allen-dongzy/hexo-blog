---
title: C语言数据类型
top_img: 
cover: 
date: 2021-09-07 16:22:17
tags: 
  - C语言
  - C语言数据类型
categories:
  - [教程, C语言, 数据类型]
description: C语言数据类型
---

## 基本数据类型汇总

| 最初的标准 | C90标准 | C99标准    |
| ---------- | ------- | ---------- |
| int        | signed  | _Bool      |
| long       | void    | _Complex   |
| short      |         | _Imaginary |
| unsigned   |         |            |
| char       |         |            |
| float      |         |            |
| double     |         |            |

这里主要讲解C90

### 位，字节，字

- 位（bit）是最小的存储单元，可以储存0或1（2种变化）。
- 字节（byte）是常用的计算机存储单位。对于几乎所有的机器，1字节均为8位。（2的8次方种变化=>256）。
- 字（word）是设计计算机时给定的自然存储单位。8位计算机中1个字长就是8位，后来经过16，32，直到现在的64位机，1个字长变为为64位（64位机中1个字长就是8字节，32位机种1个字长就是4字节）。

**在C语言种所有的数据最终都会对照ASC II码被转化为二进制，存到真实的内存地址中，存储空间的最小单位是位（bit）。**

**注意：C语言把1字节定义为char 类型占用的位（bit ）数，某些情况下char类型要存储的内容超过了256种，这时候1字节为16位。因此在C语言中1字节可能是8位也可能是16位（几乎在所有机器中都是8位）。**

### 变量的存储方式

<img src="variable.png" style="zoom: 33%;" />

### 值的存储方式

假设现在的环境是**8位机**，声明`int num = 7;`，创建内存空间`num`后应当存入7，但是计算机只认识二进制，7以二进制写是111。因此，要在8位长度的字节(`num`)中储存该数字，需要把前5位都设置成0，后3位设置成1

下列数据字长8位=>1字节

| 长度： | 第7位 | 第6位 | 第5位 | 第4位 | 第3位 | 第2位 | 第1位 | 第0位 |
| ------ | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 数据： | 0     | 0     | 0     | 0     | 0     | 1     | 1     | 1     |

二进制编码根据字长位数从右往左正序相加逆推得到十进制整数: 0+0+0+0+0+$2^2$+$2^1$+$2^0$ = 7

## 整型

**所有整型在不同进制下的书写格式**：

- 十进制：20
- 八进制：024
- 十六进制：0x14 \| 0X14

**所有整型在不同进制下的打印格式**：

| 打印格式       | int  | long | long long | short | unsigned | unsigned long | unsigned long long |
| -------------- | ---- | ---- | --------- | ----- | -------- | ------------- | ------------------ |
| 十进制         | %d   | %ld  | %lld      | %hd   | %u       | %lu           | %llu               |
| 八进制         | %o   | %lo  | %llo      | %ho   | %o       | %lo           | %llo               |
| 十六进制       | %x   | %lx  | %llx      | %hx   | %x       | %lx           | %llx               |
| 八进制(显式)   | %#o  | %#lo | %#llo     | %#ho  | %#o      | %#lo          | %#llo              |
| 十六进制(显式) | %#x  | %#lx | %#llx     | %#hx  | %#x      | %#lx          | %#llx              |

所有的x都可以替换成X，对应的表现形式则是0x和0X的区别。

**验证**

```c
	int num1 = 20; // 十进制
	int num2 = 024; // 八进制
	int num3 = 0x14; // 十六进制

	printf("-----num1-----\n");
	printf("十进制：%d\n", num1); // 20
	printf("八进制：%o\n", num1); // 24
	printf("带前缀的八进制：%#o\n", num1); // 024
	printf("十六进制：%x\n", num1); // 14
	printf("带前缀的十六进制：%#x\n", num1); // 0x14

	printf("-----num2-----\n");
	printf("十进制：%d\n", num2); // 20
	printf("八进制：%o\n", num2); // 24
	printf("带前缀的八进制：%#o\n", num2); // 024
	printf("十六进制：%x\n", num2); // 14
	printf("带前缀的十六进制：%#x\n", num2); // 0x14

	printf("-----num3-----\n");
	printf("十进制：%d\n", num3); // 20
	printf("八进制：%o\n", num3); // 24
	printf("带前缀的八进制：%#o\n", num3); // 024
	printf("十六进制：%x\n", num3); // 14
	printf("带前缀的十六进制：%#x\n", num3); // 0x14
```



### int类型

整数 是没有小数部分的数。例如，2、−23和2456都是整数。计算机以二进制数字储存整数。

#### 声明

```c
int sows;
int boars = 2;
```

### short int类型

`short int` 类型（或者简写为`short` ）占用的存储空间可能比`int` 类型少，常用于较小数值的场合以节省空间。与`int` 类似，`short` 是有符号类型。

#### 声明

```c
short int erns;
short ribs;
short num = 1;
```

### long int类型

`long int` 或`long` 占用的存储空间可能比`int` 多，适用于较大数值的场合。与`int`类似，`long` 是有符号类型。

#### 声明

```c
long int estine;
long johns;
long num = 1;
```

### long long int类型(C99)

`long long int` 或`long long` （C99标准加入）占用的储存空间可能比`long` 多，适用于更大数值的场合。该类型至少占`64` 位。与`int` 类似，`long long` 是有符号类型。

#### 声明

```c
// C99新增类型
long long int year;
long long ago;
long long num = 1;
```

### unsigned 类型

`unsigned` 只用于非负值的场合。这种类型与有符号类型表示的范围不同。例如，16位`unsigned int` 允许的取值范围是`0` ～`65535` ，而不是`-32768` ～`32767` 。用于表示正负号的位现在用于表示另一个二进制位，所以无符号整型可以表示更大的数。

#### 声明

```c
// unsigned可以修饰 int、long、shart类型，默认简写下指的是 unsigned int
unsigned int s_count;
unsigned players;
unsigned long headcount;
unsigned short yesvotes;
```

### signed类型

所有不加`unsigned`修饰的整型都是`signed`类型的。

#### 声明

```c
int sows;
short erns;
long estine;
long long num = 1;
```



## 浮点型

**所有浮点型的声明格式**：

```c
// float(后缀用f或F)
float a = 2.0f;
float b = 2E-2F;

// double(无后缀默认为double)
double c = 2.34;
double d = .5E-3
  
// long double(后缀用l或L)
long double e = 3.1415926L;
long double f = 67.45E2L
```

浮点型中，正号可以省略。可以没有小数点（如，2E5）或指数部分（如，19.28），但是不能同时省略两者。可以省略小数部分（如，3.E16）或整数部分（如，.45E-6），但是不能同时省略两者。也就是说不能表现出整型形态。

**所有浮点型的打印格式**：

|            | float | double | long double |
| ---------- | ----- | ------ | ----------- |
| 常规       | %f    | %f     | %Lf         |
| 指数计数法 | %e    | %e     | %Le         |

那些未在函数原型中显式说明参数类型的函数（如，`printf()` ）传递参数时，C编译器会把`float` 类型的值自动转换成`double` 类型。例如：

```c
float aboat = 32000.0;
printf("%f can be written %e\n", aboat, aboat); // 32000.000000 can be written 3.200000e+04
```

**默认情况下，编译器假定浮点型常量是`double` 类型的精度。**

### float类型

`float` 类型必须至少能表示6位有效数字，且取值范围至少是$10^{-37}$ ～$10^{+37}$ 。前一项规定指`float` 类型必须能够表示33.333333的前6位数字，而不是精确到小数点后6位数字。通常，系统储存一个浮点数要占用32位。

#### 声明

```c
float noah, jonah;
float num = -1.56E12;
float planck = 2.87e-3;
```

### double类型

`double` 类型和`float` 类型的最小取值范围相同，但至少必须能表示10位有效数字。一般情况下，`double` 占用64位而不是32位。

#### 声明

```c
double trouble;
double num = 56;
```

### long double类型

C只保证`long double` 类型至少与`double` 类型的精度相同。

#### 声明

```c
long double a;
long double b;
```

## 字符型(char)

`char` 类型用于储存字符（如，字母或标点符号），但是从技术层面看，`char` 是整数类型。因为`char` 类型实际上储存的是整数而不是字符。计算机使用数字编码来处理字符，即用特定的整数表示特定的字符。最常用的编码是ASCII编码。

标准ASCII码的范围是0～127，只需7位二进制数即可表示。通常，`char` 类型被定义为8位的存储单元，因此容纳标准ASCII码绰绰有余。

C语言把1字节定义为`char` 类型占用的位（*bit* ）数，因此无论是16位还是32位系统，都可以使用`char` 类型。

### 声明

```c
char response = 'A';
char itable, latan;
```

单引号为字符，双引号为字符串。

### 转义字符

| 转义序列 |                             含义                             |
| :------: | :----------------------------------------------------------: |
|   `\a`   |                        警报（ANSI C）                        |
|   `\b`   |                             退格                             |
|   `\f`   |                             换页                             |
|   `\n`   |                             换行                             |
|   `\r`   |                             回车                             |
|   `\t`   |                          水平制表符                          |
|   `\v`   |                          垂直制表符                          |
|   `\\`   |                         反斜杠（\）                          |
|   `\'`   |                            单引号                            |
|   `\"`   |                            双引号                            |
|   `\?`   |                             问号                             |
|  `\0oo`  | 八进制值（`oo` 必须是有效的八进制数，即每个`o` 可表示`0` ～`7` 中的一个数） |
|  `\xhh`  | 十六进制值（`hh` 必须是有效的十六进制数，即每个`h` 可表示`0` ～`f` 中的一个数） |

### 字符的存储方式

<img src="char.png" style="zoom:33%;" />

字符c的ASC II码是67，那么存入该字符时，存入的就是67的二进制(与值的存储方式原理相同，最后都是二进制)。

## void型

值为空则是`void`。

### 声明

```c
void main(void) {
	printf("该函数返回值和参数都是空");
}
```