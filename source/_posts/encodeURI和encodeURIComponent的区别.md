---
title: encodeURI和encodeURIComponent的区别
top_img: images/top-img.jpg
cover: images/top-img.jpg
date: 2021-08-23 18:15:53
tags:
  - js
  - URI
categories:
  - [教程, js, URI]
description: encodeURI和encodeURIComponent的具体使用场景
---

## encodeURI、decodeURI、encodeURIComponent 和 decodeURIComponent 之间的关系

- `encodeURI`不会对本身属于`URI`的特殊字符进行编码，例如冒号":"、正斜杠"/"、问号"?"和井字号"#"。
- `encodeURIComponent`则会对它发现的任何非标准字符进行编码。
- `decodeURI`和`decodeURIComponent`是解除对应编码的。

## 常用适用范围

- `encodeURI`: 适用于编码一个 url。
- `encodeURIComponent`: 适用于编码 url 中的 params 的参数。

## 举例

**定义 `url`**

```
const url1 = 'http://106.54.253.194/some thing'
const url2 = `http://106.54.253.194?params=${url1}`
```

**原本的 `url`**

```
console.log(url1)
// http://106.54.253.194/some thing

console.log(url2)
// http://106.54.253.194?params=http://106.54.253.194/some thing

```

**使用 `encodeURI` 后的 `url`**

```
console.log(encodeURI(url1))
// http://106.54.253.194/some%20thing

console.log(encodeURI(url2))
// http://106.54.253.194?params=http://106.54.253.194/some%20thing
```

**使用 `encodeURIComponent` 后的 `url`**

```

console.log(encodeURIComponent(url1))
// http%3A%2F%2F106.54.253.194%2Fsome%20thing

console.log(encodeURIComponent(url1))
// http%3A%2F%2F106.54.253.194%3Fparams%3Dhttp%3A%2F%2F106.54.253.194%2Fsome%20thing
```

可以看到 `encodeURI` 会把非 `URI` 的内容编码，而 `encodeURIComponent` 会把所有非数字和英文的内容编码。 主流框架中路由跳转 `url` 后面的参数不能包含 `url` ，这时候就只能将后面的参数用 `encodeURIComponent` 来编码传递了。