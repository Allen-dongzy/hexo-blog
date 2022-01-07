---
title: C语言文件读写
top_img:
cover:
date: 2022-01-07 17:19:17
tags:
  - C语言
  - C语言数据类型
categories:
  - [教程, C语言, 数据类型]
description: C语言数据类型
---

## 文件打开

### fopen()

**原型：**

```c
FILE *fopen(const char *filename, const char *mode)
```

**解析：**

在 fopen 中传入文件名(带路径)filename、打开模式 mode。fopen 会打开该文件并返回一个指向该文件的 FILE 类型的文件流指针。

**mode 类型：**

| 模式 | 描述                                                                       |
| ---- | -------------------------------------------------------------------------- |
| r    | 打开一个已有的文本文件，允许读取。                                         |
| w    | 打开一个文本文件，若有则抹去内容重新写入，若无则新建文件并写入。           |
| a    | 打开一个文本文件，若有则在现有内容后面追加新内容，若无则新建文件并写入。   |
| r+   | 打开一个文本文件，允许读写。                                               |
| w+   | 打开一个文本文件，允许读写。若有则抹去内容重新写入，若无则新建文件并写入。 |
| a+   | 打开一个文本文件，允许读写。若有则追加新内容，若无则新建文件并写入。       |

若是处理二进制文件，则需要加上访问模式“b”，如：

```c
"rb", "wb", "ab", "rb+", "r+b", "wb+", "w+b", "ab+", "a+b"
```

## 文件关闭

### fclose()

**原型：**

```c
int fclose(FILE *stream)
```

**解析：**

在 fclose 中传入文件流 stream。fclose 会关闭 stream 流，刷新所有缓冲区。成功则返回 0，失败则返回 EOF。

## 文件写入

### fputc()

**原型：**

```c
int fputc(int c, FILE *stream)
```

**解析：**

在 fputc 中传入字符 c、文件流 stream。fput 会将 c 写入到 stream 流中，并把位置标识符往前移动。成功则将写入的字符强转为 int 后返回它，失败则返回 EOF。

### fputs()

**原型：**

```
int fputs(const char *s, FILE *stream)
```

**解析：**

在 fputs 中传入字符串 s、文件流 stream。fputs 会把 s 写入到 stream 流中，但不包括空字符。成功则返回一个非负数，失败则返回 EOF。

### fprintf()

**原型：**

```c
int fprintf(FILE *stream, const char *format, ...)
```

**解析：**

在 fprintf 中传入文件流 stream、格式控制字符串 format、参数列表...。fprintf 会将参数列表里的值代入到 format 中，写入到 stream 流中。成功则返回写入的字符的个数，失败则返回负数。

### fwrite()

**原型：**

```c
size_t fwrite(void *ptr, size_t size, size_t nmemb, FILE *stream)
```

**解析：**

在 fwrite 中传入空内存指针 ptr、元素大小 size、元素个数 nmemb、文件流 stream(size_t 对象是类型数据类型，类似 int)。fwrite 会在 ptr 中找到 nmemb 个 size 大小的数据，把它们写入到 stream 流中。如果成功，该函数返回一个 size_t 对象，表示元素的总数。如果该数字与 nmemb 参数不同，则会显示一个错误。

## 文件读取

### fgetc()

**原型：**

```c
int fgetc(FILE *stream)
```

**解析：**

在 fgetc 中传入文件流 stream。fgetc 会在 stream 流中读取下一个字符，并把位置标识符往前移动，最后将字符强转为 int 后返回它。如果到达文件末尾或发生读错误，则返回 EOF。

### fgets()

**原型：**

```c
char *fgets(char *s, int n, FILE *stream)
```

**解析：**

在 fgets 中传入缓冲区字符指针 s、个数 n、文件流 stream。fgets 会从 stream 流中读取 n-1 个字符存储到 s 中，并在最后追加一个 null 字符来终止字符串。最后返回该字符串。如果到达文件末尾或者没有读取到任何字符，s 的内容保持不变，并返回一个空指针。如果发生错误，返回一个空指针。

**如果在读取到 stream 指向的文件的最后一个字符之前就遇到换行符‘\n’或文件的末尾 EOF，则只会返回读取到的字符，包括换行符。**

### fscanf()

**原型：**

```c
int fscanf(FILE *stream, const char *format, ...)
```

**解析：**

在 fscanf 中传入文件流 stream、格式控制字符串 format、参数列表...。fscanf 会在 stream 流中将符合 format 规则的字符串选出，按照格式控制依次赋值到参数列表中的地址中。如果成功，该函数返回成功匹配和赋值的个数。如果到达文件末尾或发生读错误，则返回 EOF。

### fread()

**原型：**

```c
size_t fread(void *ptr, size_t size, size_t nmemb, FILE *stream)
```

**解析：**

在 fread 中传入空内存指针 ptr、元素大小 size、元素个数 nmemb、文件流 stream(size_t 对象是类型数据类型，类似 int)。fread 会在 stream 流中读取 nmemb 个 size 大小的数据赋值到 ptr 中。成功读取的元素总数会以 size_t 对象返回。如果总数与 nmemb 参数不同，则可能发生了一个错误或者到达了文件末尾。

## 文件定位

### rewind()

**原型：**

```c
void rewind(FILE *stream)
```

**解析：**

在 rewind 中传入文件流 stream。rewind 会设置文件位置为 stream 流文件的开头

### fseek()

**原型：**

```c
int fseek(FILE *stream, long int offset, int whence)
```

**解析：**

在 fseek 中传入文件流 stream、偏移量 offset、偏移的根源 whence。fseek 会设置 stream 流的文件位置为 whence 位置开始，偏移 offset 个位置后的位置。成功则该函数返回零，失败则返回非零值。
