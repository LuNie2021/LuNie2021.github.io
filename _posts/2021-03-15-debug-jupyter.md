---
layout: post
title: "Troubleshooting: jupyter not found"
subtitle: 
date: 2021-03-15
author: Lu Nie 
category: troubleshooting
tags: python jupyter

---
解决 pip3安装jupyter notebook后无法在terminal调用




> #### 1. install jupyter 
python version: python3
MacOS terminal 
安装：
```
pip3 install jupyter 
```
调用：在terminal中输入
```
jupyter notebook
```
> #### 2. bug 
报错：
“jupyter cannot found” 
原因：安装的jupyter的路径没有存入根目录

> #### 3. solution: 导入路径
1 检查已安装，并查找位置
```
pip3 show jupyter
```
得到一堆反馈，其中有：
```
Location: /Library/Frameworks/Python.framework/Versions/3.6/lib/python3.7/site-packages
```
2 将位置添加进入路径
方法一：
```
vim ~/.zshrc
```
##### 障碍：不会 vim 语法
基本语句：待补充（网上搜一下）

方法二：直接用echo命令（参考blog教程中的echo用法）
3 重载
```
source .zshrc 
```
4 jupyter notebook 
##### 报错：还是找不到
```
jupyter-notebook
```
可以！！！ 
我也不知道为啥？？ 

> #### 3. bug：无法加入自动补全代码扩展功能
原因：还是找不到路径
解决：用VScode + kite软件替代


