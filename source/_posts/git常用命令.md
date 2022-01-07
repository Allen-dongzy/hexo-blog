---
title: git常用命令
top_img: 
cover: 
date: 2021-10-13 11:33:56
tags:
  - git
  - git常用命令
categories:
  - [教程, git, 常用命令]
description: git常用命令
---

## 创建类

**初始化git本地仓库：**

```shell
git init
```

**将git的本地仓库与远程仓库关联：**

```shell
git remote add origin <gitUrl>
```

**修改与git的本地仓库关联的远程仓库地址：**

```shell
git remote set-url origin <gitUrl>
```

**克隆git远程仓库：**

```shell
git clone <gitUrl>
```

**克隆git远程仓库的指定分支：**

```shell
git clone -b <branchName> <gitUrl>
```

## 常用操作类

**git添加到暂存区：**

```shell
git add <fileName>
```

**git提交到本地仓库：**

```shell
git commit -m "<commitMessage>"
```

**git第一次提交到远程仓库(默认master分支)：**

```shell
git push -u origin master
```

**git提交到远程仓库(默认master分支)：**

```shell
git push
```

**git提交到远程仓库指定分支：**

```shell
git push origin <branchName>
```

## 查看类

**查看git状态：**

```shell
git status
```

**查看提交记录：**

```shell
git log
```

**查看真实提交记录：**

```shell
git reflog
```

## 分支操作类

**查看git当前所在分支：**

```shell
git branch
```

**git创建新分支：**

```shell
git branch <branchName>
```


**git创建没有指向的新分支：**

```shell
git checkout --orphan <branchName>
```

**git删除本地分支**

```shell
git branch -d <branchName>
```

**git删除未上传的本地分支**

```shell
git branch -D <branchName>
```

**git删除远程分支**

```shell
git push origin -d <branchName>
```

**切换git分支：**

```shell
git checkout <branchName>
```

**git创建新分支并切换到该分支：**

```shell
git checkout -b <branchName>
```

**git查看本地分支与远程分支的映射关系：**

```shell
git branch -v
```

**git修改当前分支所对应的远程默认分支：**

```shell
git branch --set-upstream-to origin/<branchName>
```

**git撤销本地分支与远程分支的映射关系：**

```shell
git branch --unset-upstream
```

## 标记类

**创建本地标记：**

```shell
git tag <tagName>
```

**在指定commit上新增标记：**

```shell
git tag <tagName> <commitId>
```

**将指定本地标记推送到远程仓库：**

```shell
git push origin <tagName>
```

**将全部本地标记推送到远程仓库：**

```shell
git push origin --tags
```

**查看本地某个标记的详细信息：**

```shell
git show <tagName>
```

**查看本地所有标记：**

```shell
git tag
```

**删除指定的本地标记：**

```shell
git tag -d <tagName>
```

## 修改类

**撤销暂存区(git add的产物)的内容：**

```shell
git restore --staged <fileName>
or
git reset HEAD <fileName>
```

**撤销本地仓库(git commit的产物)到指定版本：**

```shell
git reset --hard <commitId>
```

**删除所有文件：**

```shell
git rm -rf .
```

**忽略指定的文件的版本控制(停止追踪)：**

```shell
git rm -r --cached xxx
```

**删除远程分支的内容：**

```shell
git remote rm origin
```

## 配置git本地账户

**全局配置本地账户密码：**

```shell
git config --global <user.name> "<Your Name>"
git config --global <user.email> "<email@example.com>"
```

**查看全局配置：**

```shell
git config --list
```

**删除一个全局配置：**

```shell
git config --global --unset <user.name>
```

**修改全局配置：**

```shell
git config --global --edit
```


**单独项目配置(在项目根目录下输入)：**

```shell
git config <user.name> "<Your Name>"
git config <user.email> "<email@example.com>"
```
