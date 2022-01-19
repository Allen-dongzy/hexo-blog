---
title: eslint的使用方法
top_img:
cover:
date: 2022-01-18 16:13:27
tags:
  - npm插件
  - eslint
categories:
  - [教程, npm插件, eslint]
description: eslint的入门使用方法
---

## 安装

```shell
yarn add eslint --dev
```

## 验证

```shell
./node_modules/.bin/eslint -v
```

## 使用

```shell
./node_modules/.bin/eslint --init
```

### 勾选服务

```shell
√ How would you like to use ESLint? · problems

√ What type of modules does your project use? · esm

√ Which framework does your project use? · none

√ Does your project use TypeScript? · No / Yes

√ Where does your code run? · browser

√ What format do you want your config file to be in? · JSON

The config that you've selected requires the following dependencies:



@typescript-eslint/eslint-plugin@latest @typescript-eslint/parser@latest

√ Would you like to install them now with npm? · No / Yes
```

**这里选择的是**：

- 检查语法和问题

- esm 模块

- 没有使用框架

- 使用 ts

- 在浏览器中运行

- 使用 json 作为配置文件

- 使用 npm 来安装这些依赖项

### 注意事项

这里开启了 ts 服务并安装了@typescript-eslint/eslint-plugin@latest @typescript-eslint/parser@latest 这两个插件，所以需要实现安装好 ts

```shell
yarn add typescript --dev
```

## 验证

**在根目录创建 src/demo.ts**

```typescript
const str: string = "abc";
console.log(str);
```

**在 terminal 中校验**

```shell
./node_modules/.bin/eslint ./src/demo.ts
```

**提示**

```shell
 1:7  error  Type string trivially inferred from a string literal, remove type annotation  @typescript-eslint/no-inferrable-types



✖ 1 problem (1 error, 0 warnings)

 1 error and 0 warnings potentially fixable with the `--fix` option.
```

提示我们说“从字符串字面量能推断出的类型字符串，需要删除类型注释” ，这说明`eslint`已经生效，有效的拦截到了。之后需要新增的规则可以在根目录的`.eslintrc.json`的`rules`中配置。

## 相关配置

### .eslintrc.json

刚刚`√ What format do you want your config file to be in? · JSON`这一项会在根目录创建.eslintrc.json 文件，里面可以配置 eslint 的规则。

根据上述勾选情况，生成的内容如下：

```json
{
  "env": {
    "browser": true,
    "es2021": true
  },
  "extends": ["eslint:recommended", "plugin:@typescript-eslint/recommended"],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "plugins": ["@typescript-eslint"],
  "rules": {}
}
```

我们可以根据官网的文档来一一配置它们。
[.eslintrc配置规则](http://eslint.cn/docs/user-guide/configuring)

### .eslintignore

如果我们不想检测项目中某些目录的内容，那么可以在根目录创建.eslintignore 文件。在里面添加要忽略的目录或文件类型。比如 build 文件夹通常是 webpack 的配置目录，我们是不需要校验它的，所以可以在里面添加：

```tex
build
```

这样一来 build 文件夹下所有的文件都不会被校验了。
