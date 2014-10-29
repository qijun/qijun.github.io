---
date: 2014-05-26 20:58:00+00:00
layout: post
title: 设计模式笔记:建造者
categories : Design Patterns
thread: 106
tags : [Design Patterns,Notes]
---

###设计模式:建造者模式
***
####场景
建造者，将一个对象复杂的构建过程和表示相分离。
####常见实现
>类的结构图如下，可根据ConcreteBuilder个数简化掉Director和Builder。
![](/album/Screencap/builder.jpg)
####小结
1. 隐藏对象的创建步骤和内部结构。
2. 每个ConcreteBuilder相对独立

