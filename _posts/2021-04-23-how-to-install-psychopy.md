---
layout: post
toc: ture
title: "PsychoPy Install"
date: 2021-04-23
author: Lu Nie 
category: Experimental-Design 
tags: [Python PsychoPy toolbox]  
---
本文为心理学实验编写软件PsychoPy的安装和调试记录。




## 1 前情提要

**操作系统**：macOS Catalina 

**Anaconda Version**: 

**Python Version**: 3.8.0


#### 为什么要用PsychPy 

因为新的实验设计需求，需要更加方便和细致的实验设计，PsychPy和PTB都是必学项目。不过Mac OS似乎对于PTB运行不太友好。遂尝试PsychoPy 

其次，有许多学习材料，借助python发展的东风，也会很活跃。

更重要的是，基于Python, 开源免费


## 2 环境准备以及软件安装

### 2.1 什么是安装环境？
虚拟环境可以理解为人们为了独立的开发不同的项目，因为很大可能不同项目使用到的包版本会有冲突，为了避免下载到同一个地方而报错，我们可以为不同的项目开发一块"净土"。 

比如，虽然目前我的电脑Python版本为3.8, 而PsychoPy更加支持Python 3.6，因此之后我会使用Anaconda单独创建一个Python 3.6的虚拟环境

Anaconda中的conda可以理解为一个工具，核心功能就是进行包管理与环境管理。通过conda的一系列命令实现。

#### 创建环境：

```
conda create -n <envname> <python版本>
conda create -n py2 python=2.7  #  创建python2.7版本的环境，命名为py2
```
#### 查看已安装环境：

```
conda env list # 查看已安装环境
conda activate <env name> # 激活环境
conda deactivate    # 退出当前环境
conda install package_name(包名) # 安装包
conda update conda  #检查更新 
```
#### 删除环境
```
conda remove -n your_env_name(虚拟环境名称) --all  # 删除环境
conda remove --name $your_env_name  $package_name（包名）  #删除环境中的具体包
```
#### 生成环境：
```
conda env export > environment.yml  
```


#### 切换环境：
如果电脑中有多个环境，那么在需要使用某个具体环境时，一定要记得切换，不然会报错
 
#### 查看已有环境：
```
conda env list
```

#### 进行环境切换：
```
conda activate XXX(环境名)
```

### 2.2 安装 

有前辈推荐使用Anaconda来安装，避免pip的一些环境依赖问题；

方法一： Anaconda + environment file 

***官网***安装方式，仅列出，因为你懂的原因，无法下载官方提供的***environment file*** 

Download the environment file, open your terminal, navigate to the directory you saved the file to, and run:

```
conda env create -n psychopy -f psychopy-env.yml
```

To activate the newly-created environment and run PsychoPy, exceute:

```
conda activate psychopy
psychopy
```
方法二： Anaconda + creat environment file

此外，这里参照[这篇文档](https://mrswolf.github.io/zh-cn/2018/11/10/%EF%BC%88%E4%B8%80%EF%BC%89Psychopy%E5%AE%89%E8%A3%85%E5%92%8C%E4%BD%BF%E7%94%A8/) 可以自己**创建环境**并安装

在终端中创建环境文件
```
conda create -n psypy3 python=3.6
```
激活环境：
```
conda activate psypy3
```
报错：
```
CommandNotFoundError: Your shell has not been properly configured to use 'conda activate'.
To initialize your shell, run

    $ conda init <SHELL_NAME>

Currently supported shells are:
  - bash
  - fish
  - tcsh
  - xonsh
  - zsh
  - powershell

See 'conda init --help' for more information and options.

IMPORTANT: You may need to close and restart your shell after running 'conda init'.

```
原因：当前使用的shell(zsh)没有配置好conda activate, 需要运行 conda init 初始化(一般首次激活会遇到这种情况)

解决：选择zsh
```
conda init zsh
```
安装：

注意，此时终端一开始有显示(psypy3) 表明我们现在的操作均在刚刚创建的环境中进行。
```
conda install numpy scipy matplotlib pandas pyopengl pillow lxml openpyxl xlrd configobj pyyaml gevent greenlet msgpack-python psutil pytables requests[security] cffi seaborn wxpython cython pyzmq pyserial
conda install -c conda-forge pyglet pysoundfile python-bidi moviepy pyosf
pip3 install zmq json-tricks pyparallel sounddevice pygame pysoundcard psychopy_ext psychopy # 耐心等待吧
```
安装完毕检查：
```import psychopy
print(psychopy.__version__)
```
该方法安装完毕后，能够print出version信息，但是无法打开软件：

```
cd [Psychopy_Source_Path] # 定位到安装路径
python psychopyApp.py -b #打开builder
#报错如下：
No such file or directory: '/opt/anaconda3/envs/psypy3/bin/pythonw': '/opt/anaconda3/envs/psypy3/bin/pythonw'
```
原因：暂未找到




方法三：一键安装
[官网封装包一键安装](https://www.psychopy.org/download.html#pip-install) 
害，这个是最简单放便的方法！！

安装完毕打开psychopy, coder显示的python版本号就是理想的version3.6

方法四：pip
1. 先使用conda创建python 3.6环境，然后在环境下pip3 install psychopy -- 安装完毕报错找不到路径
2. 直接用[conda](https://anaconda.org/conda-forge/psychopy)安装：


```
在base环境下（即默认环境）
conda install -c conda-forge psychopy  # 运行正常，只是coder对应的是python3.8 
# 新建python3.6环境，然后再重复
conda install -c conda-forge psychopy   # 软件打不开，看起来还是环境文件的问题
```

综上：使用封装好的dmg文件一键安装吧！！ 害！！ 

## 3 使用初体验

Psychopy提供两种刺激界面设计方式，一种是GUI界面Builder，另一种是普通的脚本编写方式Coder。Builder可以转换成code, 另外，builder可能更好实现实验的整合(某b站博主说的，没有验证过)。

### 3.1 Builder
[使用文档](https://www.psychopy.org/builder/builder.html)

### 3.2 Coder 

[使用文档](http://www.psychopy.org/coder/coder.html)

推荐用pycharm编写



## 4 参考资料
【1】[Pychopy官方指导](https://discourse.psychopy.org/) 

【2】[PsychopyAPI手册](http://www.psychopy.org/api/api.html)

【3】[PsychoPy论坛](https://discourse.psychopy.org/)

【4】[exp-sources](https://pavlovia.org/docs/home/about)

【5】[指路b站](https://www.bilibili.com/video/BV1n7411d7A3?from=search&seid=2641410729730121304)

【6】[指路b站](https://www.bilibili.com/video/BV1zW411C79Y?from=search&seid=2641410729730121304)

