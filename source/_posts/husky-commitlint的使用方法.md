---
title: husky+commitlint的使用方法
date: 2021-08-17 15:22:35
top_img: top-img.png
cover: cover.png
tags:
  - npm插件
  - husky
  - commitlint
categories:
  - [教程, npm插件, commitlint]
  - [教程, npm插件, husky]
description: 使用husky+commitlint来拦截不合法的git commit提交
---

## 引入

**yarn**

```shell
// 添加husky
yarn add husky --dev
// 添加commitlint
yarn add @commitlint/cli  @commitlint/config-conventional --dev
```

**npm**

```shell
// 添加husky并初始化
npm install husky --save-dev
// 添加commitlint
npm install @commitlint/cli @commitlint/config-conventional --save-dev
```

## 安装 husky 脚本

```shell
npx husky install
```

**此时项目根目录会出现`.husky`目录。**

## 注册 package.json 命令

```json
// package.json
{
  "scripts": {
    "prepare": "husky install"
  }
}
```

**在`package.json`的`scripts`中加入`prepare`的脚本命令，该命令是用来安装已下载好的`husky`脚本的。(也可省略，但考虑到协作最好加上)**

## 添加钩子

```shell
// 添加git时commit-msg钩子函数的脚本，此时commitlint奏效
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
```

## 根目录添加 commitlint.config.js

```javascript
module.exports = {
  extends: ['@commitlint/config-conventional']
}
```

**此时我们乱提交就会报错:**

**`commit message: <type>: <subject>` (注意冒号后面有空格)**

```shell
// 错误示例
git add .
git commmit -m "test"

// 提示主题和类型是空的
⧗   input: test
✖   subject may not be empty [subject-empty]
✖   type may not be empty [type-empty]
```

```shell
// 正确示例
git add .
git commmit -m "test: add test demos"

// 提示主题和类型是空的
[feature-type d279352] test: add test demos
 1 file changed, 4 insertions(+)
 create mode 100644 .husky/commit-msg
```

## commitlint 中自带的 type 类型:

- 地址：node_modules/@commitlint/config-conventional/index.js
- 规则：
  - feat: 新功能的开发
  - fix: 修补 bug
  - docs: 添加或修改文档
  - style: 添加或修改代码格式
  - refactor: 重构，即不是新增功能，也不是修改 bug 的代码变动
  - perf: 提高性能的代码更改
  - test: 添加或修改测试用例
  - build: 影响构建系统或外部依赖的更改
  - ci: 对 CI 配置文件和脚本的更改
  - chore: 其他不修改 src 或测试文件的更改
  - revert: 恢复上一次提交

## 提示

**若需要格式化代码的功能，与`husky`+`pretter`结合使用更佳**
