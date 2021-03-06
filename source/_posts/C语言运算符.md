---
title: C语言运算符
top_img:
cover:
date: 2021-10-13 10:54:54
tags:
  - C语言
  - C语言运算符
categories:
  - [教程, C语言, 运算符]
description: C语言运算符的优先级
---

| 优先级 |    运算符    |      含义      |            使用方法            |  结合性  |    几目    |    类别    |
| :----: | :----------: | :------------: | :----------------------------: | :------: | :--------: | :--------: |
|   1    |      []      |    数组下标    |          数组名[下标]          | 从左到右 |            |            |
|        |      ()      |     圆括号     |    (表达式)/函数名(表达式)     |          |            |            |
|        |      ->      |  指针成员选择  |         对象指针->成员         |          |            |            |
|        |      .       |  对象成员选择  |           对象.成员            |          |            |            |
|   2    |      -       |      符号      |            -表达式             | 从右到左 | 单目运算符 |            |
|        |    (类型)    |  强制类型转换  |        (数据类型)表达式        |          |            |            |
|        |      ++      |    前置自增    |            ++变量名            |          | 单目运算符 |            |
|        |      ++      |    后置自增    |            变量名++            |          | 单目运算符 |            |
|        |      --      |    前置自减    |            --变量名            |          | 单目运算符 |            |
|        |      --      |    后置自减    |            变量名--            |          | 单目运算符 |            |
|        |      &       |     取地址     |            &变量名             |          | 单目运算符 |            |
|        |      \*      |      取值      |           \*指针变量           |          | 单目运算符 |            |
|        |      !       |     逻辑否     |            !表达式             |          | 单目运算符 |            |
|        |      ~       |    按位取反    |            ~表达式             |          | 单目运算符 |            |
|        |   sizeof()   |  判断类型大小  |         sizeof(表达式)         |          |            |            |
|   3    |      \*      |      乘法      |         表达式\*表达式         | 从左到右 | 双目运算符 | 算数运算符 |
|        |      /       |      除法      |         表达式/表达式          |          | 双目运算符 |            |
|        |      %       |      取模      |         表达式%表达式          |          | 双目运算符 |            |
|   4    |      +       |      加法      |         表达式+表达式          | 从左到右 | 双目运算符 |            |
|        |      -       |      减法      |         表达式-表达式          |          | 双目运算符 |            |
|   5    |      <<      |      左移      |          变量<<表达式          | 从左到右 | 双目运算符 | 移位运算符 |
|        |      >>      |      右移      |          变量>>表达式          |          | 双目运算符 |            |
|   6    |      >       |      大于      |         表达式>表达式          | 从左到右 | 双目运算符 | 关系运算符 |
|        |      >=      |    大于等于    |         表达式>=表达式         |          | 双目运算符 |            |
|        |      <       |      小于      |         表达式<表达式          |          | 双目运算符 |            |
|        |      <=      |    小于等于    |         表达式<=表达式         |          | 双目运算符 |            |
|   7    |      ==      |      等于      |         表达式==表达式         | 从左到右 | 双目运算符 |            |
|        |      !=      |     不等于     |         表达式!=表达式         |          | 双目运算符 |            |
|   8    |      &       |     按位与     |         表达式&表达式          | 从左到右 | 双目运算符 |  位运算符  |
|   9    |      ^       |    按位异或    |         表达式^表达式          | 从左到右 | 双目运算符 |            |
|   10   |    &#124;    |     按位或     |      表达式 &#124; 表达式      | 从左到右 | 双目运算符 |            |
|   11   |      &&      |     短路与     |         表达式&&表达式         | 从左到右 | 双目运算符 | 逻辑运算符 |
|   12   | &#124;&#124; |     短路或     |   表达式 &#124;&#124; 表达式   | 从左到右 | 双目运算符 |            |
|   13   |      ?:      |    条件判断    | 表达式 1 ? 表达式 2 : 表达式 3 | 从右到左 | 三目运算符 | 条件运算符 |
|   14   |      =       |      赋值      |          变量=表达式           | 从右到左 |            | 赋值运算符 |
|        |     \*=      |    乘后赋值    |         变量\*=表达式          |          |            |            |
|        |      /=      |    除后赋值    |          变量/=表达式          |          |            |            |
|        |      %=      |   取模后赋值   |          变量%=表达式          |          |            |            |
|        |      +=      |    加后赋值    |          变量+=表达式          |          |            |            |
|        |      -=      |    减后赋值    |          变量-=表达式          |          |            |            |
|        |     <<=      |   左移后赋值   |         变量<<=表达式          |          |            |            |
|        |     >>=      |   右移后赋值   |         变量>>=表达式          |          |            |            |
|        |      &=      |  按位与后赋值  |          变量&=表达式          |          |            |            |
|        |      ^=      | 按位异或后赋值 |          变量^=表达式          |          |            |            |
|        |   &#124;=    |  按位或后赋值  |       变量 &#124;=表达式       |          |            |            |
|   15   |      ,       | 间隔后依次运算 |     表达式, 表达式, 表达式     | 从左到右 |            | 逗号运算符 |
