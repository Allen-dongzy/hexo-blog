---
title: husky+prettier的使用方法
date: 2021-08-17 15:32:47
tags:
  - npm插件
  - husky
  - prettier
categories:
  - 教程
  - npm插件
  - prettier
description: 使用husky+prettier在git commit提交前进行代码格式化操作
---

## 引入

**yarn**

```
// 添加prettier
yarn add prettier --dev --exact
```

**npm**

```
// 添加prettier
npm install prettier --save-dev --save-exact
```

## 添加.prettierrc.json 规则文件

```
echo {}> .prettierrc.json
```

**此时项目根目录会出现.prettierrc.json。**

## 添加.prettierignore 忽略文件

```
// .prettierignore
build
coverage
```

**此时项目根目录会出现 prettierignore。**

## 添加 lint-staged 插件

如果没有安装`husky`，此步骤后将自动安装`husky`并创建`pre-commit`钩子，在`git`执行到`pre-commit`时会自动执行`lint-staged`来格式化文件

```
npx mrm@2 lint-staged
```

安装好后，修改`package.js`中的`lint-staged`属性，配置中加入`jsx`,`ts`,`tsx`类型文件的支持

```
"lint-staged": {
    "*.{js,jsx,ts,tsx,css,md}": "prettier --write"
}
```

**`js`,`jsx`,`ts`,`tsx`,`css`,`md`类型的文件将在执行`lint-staged`时自动调用`prettier --write`来格式化代码**

## prettier 兼容 eslint

**yarn**

```
// 添加eslint-config-prettier
yarn add eslint-config-prettier --dev
```

**npm**

```
// 添加eslint-config-prettier
npm install eslint-config-prettier --save-dev
```

**进入`package.json`中，在`eslintConfig`的`extends`选项中添加`prettier`**

```
"eslintConfig": {
    "extends": [
      "prettier"
    ]
}
```

**使用`eslint-config-prettier`并配置`eslintConfig`后，`prettier`与`eslint`冲突的部分将会以`prettier`的格式来覆盖**

**至此，我们使用`git add .`和`git commit -m "xxx: xxx"`后，`prettier`会自动帮我们格式化指定的类型文件**

## 提示

**若需要拦截不规范的`commit`提交的功能，与`husky`+`commint`结合使用更佳**
