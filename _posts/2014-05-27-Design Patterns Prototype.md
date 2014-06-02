---
date: 2014-05-27 16:56:00+00:00
layout: post
title: 设计模式笔记:原型
categories : Design Patterns
thread: 107
tags : [Design Patterns,Notes]
---

###设计模式:原型模式
***
####场景
原型，通过一个原型对象来创建更多同类型的对象。在C#中有ICloneable接口可供需要克隆自身对象的类实现，克隆有浅拷贝和深拷贝（复制引用和实例）。
####常见实现
类的结构图如下。
![](/album/Screencap/prototype.jpg)
####小结
1. 对类的结构没有要求
2. 对原有类没有影响

