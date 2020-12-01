---
title: "Git常用命令整理"
subtitle: ""
date: 2020-11-25T21:32:35+08:00
lastmod: 2020-11-25T21:32:35+08:00
draft: false
author: "imicrocode"
authorLink: ""
description: "Git常用命令整理"

tags: ["git"]
categories: ["commands"]

hiddenFromHomePage: false
hiddenFromSearch: false

resources:
- name: featured-image
  src: git.jpg
- name: featured-image-preview
  src: git.jpg

toc:
  enable: true
math:
  enable: false
lightgallery: true
license: ""
---

Git常用命令整理.

<!--more-->

{{< admonition >}}
本文只包含对常用git命令的整理，后续会不定时更新......
{{< /admonition >}}

### ssh-keygen

```shell
ssh-keygen -t rsa -C "your email adress"
```

### git config

```shell
# 配置用户名
git config --global user.name "your name"
# 配置用户邮箱
git config --global user.email "your email"
# 配置pull合并方式
git config --global pull.rebase false
# 查看全局配置
git config --global --list
```

### git clone

```shell
git clone <repository>
# 递归拉取(一般用在仓库中有子模块的时候)
git clone <repository> --recursive
```

### git branch

```shell
# 查看本地分支列表
git branch -l
# 查看远程分支列表
git branch -r
# 查看本地+远程分支列表
git branch -a
# 新建一个分支，但依然停留在当前分支
git branch <branchname>
# 现有分支与指定的远程分支建立追踪关系
git branch -u <remote-branchname>
# 删除本地分支
git branch -d <branchname>
```

### git add

```shell
# 添加所有变化
git add .
git add -A
# 添加被修改，被删除的变化，不包括新增的文件
git add -u
```

### git checkout

```shell
# 切换到指定分支
git checkout <branch>
# 基于现有分支创建新分支，并切换至新分支
git checkout -b <branch>
# 基于远程分支创建新分支，并切换至新分支
git checkout -b <branch> <remote-branch>
# 恢复暂存区指定文件到工作区
git checkout <file>
```

### git restore

```shell
# 丢弃工作区指定文件的变化
git restore <file>
# 丢弃工作区所有变化
git restore .
```

### git commit

```shell
# 提交暂存区文件到仓库
git commit -m <message>
```

### git tag

  ```shell
  # 列出所有tag
  git tag -l
  # 查看tag信息
  git show <tagname>
  # 在当前commit新建一个tag
  git tag <tagname>
  # 在指定commit新建一个tag
  git tag <tagname> <commit>
  # 推送指定tag至远程仓库
  git push origin <tagname>
  # 推送所有tag至远程仓库
  git push origin --tags
  # 删除本地tag
  git tag -d <tagname>
  # 删除远程tag
  git push origin :refs/tags/<tagname>
  ```

### git status

  ```shell
  # 显示所有变更的文件
  git status
  ```

### git log

  ```shell
  # 显示所有提交过的版本信息
  git log --graph
  # 显示过去n次提交过的版本信息
  git log -n
  # 根据关键词搜索提交历史
  git log -S <keyword>
  # 显示某个文件的版本历史，包括文件改动
  git log --follow <file>
  # 显示暂存区和工作区的差异
  git diff
  # 显示两次提交之间的差异
  git diff <commit1> <commit2>
  ```

### git reflog

  ```shell
  # 显示所有分支的操作记录，包括已经被删除的 commit 记录和 reset 的操作
  git reflog
  git reflog -n
  ```

### git reset

  ```shell
  # 回退至指定commit
  git reset --hard <commit>
  ```

### git push

```shell
# 推送本地分支至对应的远程分支
git push
# 推送本地分支至指定的远程分支，并建立追踪
git push -u origin <branch>
# 强制推送
git push --force
# 删除远程分支
git push origin --delete <branchname>
```

### git pull

```shell
# 拉取远程仓库的变化，并与本地分支合并
git pull
```

### git fetch

```shell
# 拉取远程仓库的变化，但不合并
git fetch
```

### git remote

```shell
# 显示所有远程仓库
git remote -v
# 把本地仓库和远程仓库关联
git remote add origin <repository>
```

### git submodule

```shell
# 添加子模块
git submodule add <repository> <path>
# 初始化子模块
git submodule init
# 更新子模块
git submodule update
# 拉取所有子模块
git submodule foreach git pull
```

### git rebase

```shell
# 合并当前commit到指定commit的记录
git rebase -i <commit>
```
