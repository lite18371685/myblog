---
title: git常用命令总结
date: 2020-03-14 11:27:10
tags:
- git
- 常用

---

##  文件状态

![img](http://q76gbpmd0.bkt.clouddn.com/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20200314174407.jpg)







## 回退

git reset \<commit ID\>

git reflog 查看所有的commit，相比git log 更全

git pull可以直接回到最新分支

git reset一共有三种模式

- --hard：不保存所有变更
- --soft：保留变更且变更内容处于Staged
- --mixed（默认）：保留变更且变更内容处于Modified

## 分支

git checkout -b \<name\> \<template\>  创建新的分支，name：分支名，template：以某个分支为模板

git checkout \<name> 切换分支， 切换后仓库内的文件也会切换

## 合并

git merge可以合并分支的变更（不是合并分支）

如遇到冲突，可以手动修改后再 add，commit

## 远程

git push --set-upstream origin bc-a

set-upstream是指设置上流分支，origin是指远端仓库，

这句话的意思是将远端仓库的bc-a分支作为本地分支的上流分支

小结：如果我们本地的分支是新切的，则需要先通过 git push --set-upstream设置上流分支，后面就可使用git push了

pull = 先fetch再自动merge

## 变基

![img](http://q76gbpmd0.bkt.clouddn.com/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20200314192114.jpg)

rebase的原理是枚举变更的commit，依次变基。

rebase就是重新排列base，而base就是指commit