---
title: typescript中常用的utility types
top_img: 
cover: 
date: 2021-09-01 16:16:50
tags:
  - typescript
  - utility-type
categories:
  - [教程, typescript, utility-type]
description: 解析typescript中的utility type
---

## 基础操作符

### keyof T

`keyof T` 是将`T`类型对象中所有的键都提取成一个联合类型，比如

```typescript
type Person = {
  name: string
  age: number
}

type PersonKeys = keyof Person
// PersonKeys类型的值为 'name' | 'age'
```

### [P in T]

`[P in T]`是将`T`联合类型集合遍历，获取每一个`P`，比如

```typescript
type Person = {
  name: string
  age: number
}

type PersonTest = {
  [P in keyof Person]: boolean
}
// PersonTest类型中的name和age都被改成boolean类型了
// type PersonTest = {
//   name: boolean
//   age: boolean
// }
```

### K extends T

`K extends T`是说`K`联合类型集合必须是`T`联合类型集合的子集，如果`K`中包含`T`没有的元素，那么会自动忽略`T`所没有的这些元素

```typescript
type Person = {
  name: string
  age: number
  height: number
  weight: number
}

Robot<K extends keyof Person>
// 这里的K只能是 'name' | 'age' | 'height' | 'weight' 联合类型合集的子集，比如 'name' | 'age'
```

## Partial<T>

将 `T` 中所有属性转换为可选属性，返回的类型可以是 `T` 的任意子集

### 源码

```typescript
type Partial<T> = {
  [P in keyof T]?: T[P]
}
```

### 解析

先使用`keyof T`获取`T`类型中所有`key`的字面量联合类型，再遍历这个联合类型，将其中每一个单独的字面量`P`都变成`?:`可选的，其`value`对应的类型为`T[P]`（`P`原本的类型）

### 实例

```typescript
interface Person {
  name: string
  age: number
}

const personToString(person: Partial<Person>) {
  console.log(`我的名字叫${person.name}，今年${person.age}岁了。`)
}

personToString({
  name: '董正阳'
})
```

使用`Partial<Person>`作为类型后，即使不传`age`属性也不会报错了。

## Pick<T, K>

### 源码

```typescript
type Pick<T, K extends keyof T> = {
 [P in K]: T[P]
}
```

### 解析

传入类型`T`以及`T`的`key`值的联合类型集合的子集（如果不是子集会报错），遍历这个子集联合类型得到每个`key`值字面量`P`，每一个`P`所对应的`value`的类型为`T[P]`（`P`原本的类型），最后返回这个新类型

### 实例

```typescript
type Person = {
  name: string
  age: number
  height: number
  weight: number
}

type RobotPerson = Pick<Person, 'name' | 'age'>

const robotPerson = {
  name: 'siri'
  age: 12
}
```

使用`Pick<Person, 'name' | 'age'>`返回的新类型作为约束，`robotPerson`就只有`name`和`age`两个属性了

## Exclude<T, U>

### 源码

```typescript
type Exclude<T, U> = T extends U ? never : T
```

### 解析

传入`T`联合类型集合和`U`联合类型集合，若`T`中含有`U`包含的元素，则将`T`中的这些元素替换成`never`（抹除掉），剩下的元素组成一个新的联合类型集合并返回

### 实例

```typescript
type Test1 = 'a' | 'b' | 'c'

type Test2 = Exclude<Test1, 'a'>
// Test2类型包含 'b' | 'c'

const test: Test2 = {
  b: 1,
  c: 2
}
```

使用`Exclude<Test1, 'a'>`返回的新类型作为约束，`test`就只有`b`和`c`两个属性了

## Omit<T, K>

### 源码

```typescript
type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>
```

### 解析

结合`Pick<T, K>`和`Exclude<T, K>`来看，传入类型`T`和`K`，先使用`Exclude<T, K>`来过滤掉`T`中含有`K`的元素，剩下的的元素组合成一个新的联合类型。再使用`Pick<T, K>`，选取T中包含新联合类型的那部分，组合成一个新的类型返回。

### 实例

```typescript
type Person {
  name: string
  age: number
  height: number
  weight: number
}

const person: Omit<Person, 'height' | 'weight'> = {
  name: 'dzy',
  age: 24
}
// 在Person筛选掉height和weight，留下name和age
```

使用` Omit<Person, 'height' | 'weight'>`返回的新类型作为约束，`person`就只有`name`和`age`两个属性了

## Parameters<T>

### 源码

```typescript
type ConstructorParameters<T extends new (...args: any) => any> = T extends new (...args: infer P) => any ? P : never;
```

### 解析

返回类型为 T 的函数的参数的类型所组成的数组。

### 实例

```typescript
declare function func1(arg: { a: number, b: string }): void

type Test = Parameters<typeof func1>
// [{ a: number, b: string }]
```

使用`Parameters<typeof func1>`可以获取到func1所有参数的类型数组。在第三方库没有暴露类型的情况下可以使用。