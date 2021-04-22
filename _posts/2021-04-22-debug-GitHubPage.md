---
layout: post
title: "Troubleshooting: GitHub Page 404"
date: 2021-04-22
author: Lu Nie 
category: troubleshooting
tags: [blog]
---
解决GitHub page 404 以及 git pull 报错




> BUG1:  There isn't a GitHub Pages site here, 个人网站搭建好输入网址却找不到

原因：仓库个人网站设置没有打开，[*点击参考*](https://zhuanlan.zhihu.com/p/91652100)


> BUG2:  在使用git 对源代码进行push到gitHub时报错，如下：
```
error: failed to push some refs to 'xxx(远程库)'
```
原因：README.md文件不在本地代码目录中，因为我是选择创建网站时自动生成README，而另外用了别的jekyll theme

解决：可以通过如下命令进行代码合并 -- 没用
```
git pull --rebase origin master
```

解决： 直接一开始就创建新仓库，README.md 自己新建 --- 有用
[*点击参考*](https://blog.csdn.net/qq_45893999/article/details/106273214?utm_medium=distribute.pc_feed_404.none-task-blog-2~default~BlogCommendFromBaidu~default-3.nonecase&dist_request_id=&depth_1-utm_source=distribute.pc_feed_404.none-task-blog-2~default~BlogCommendFromBaidu~default-3.nonecas)









