---
title: typescript-plugin-css-modules的使用方法
date: 2021-08-17 17:45:20
top_img: top-img.png
cover: cover.png
tags:
  - npm插件
  - typescript
  - css
categories:
  - [教程, npm插件, typescript-plugin-css-modules]
description: 使用typescript-plugin-css-modules插件提示module.css中的css属性
---

## 安装

```
yarn add typescript-plugin-css-modules --dev
```

## tsconfig.json

在 tsconfig.json 中的`compilerOptions`>`plugins`中配置`typescript-plugin-css-modules`插件

```
{
    "compilerOptions": {
        "plugins": [{
            "name": "typescript-plugin-css-modules"
        }]
    }
}
```

## settings.json

在`vscode`中的`settings.json`中指明 ts 的 sdk 的位置以及开题 ts 提示

```
{
    "typescript.tsdk": "node_modules/typescript/lib", // ts的sdk位置
    "typescript.enablePromptUseWorkspaceTsdk": true // 开启ts提示
}
```

**至此，重启 `vscode`，你在项目中使用 `css moudule` 时，就可以享受到 `typescript` 提示的 `css` 属性了**
