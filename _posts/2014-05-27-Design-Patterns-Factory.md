---
date: 2014-05-25 20:58:00+00:00
layout: post
title: 设计模式笔记:工厂
categories : Design Patterns
thread: 105
tags : [Design Patterns,Notes]
---

###设计模式:工厂模式
***
####场景
工厂，生产一组具有相同行为的对象，封装对象的创建过程。使用场景如多数据库工具类，多协议匹配等。工厂是为了适应产品和实现途径的扩展。
####常见实现
代码太多，就先不写了
>类的结构图如下，可根据抽象产品创建过程的复杂度决定工厂的个数
![结构](/album/Screencap/factory1.jpg)
####小结
1.client和实现者都依赖抽象，而不是某个具体实现，符合设计原则
2.控制类的实例化时机，必要时可管理所创建的对象。client不用到处充斥着new。

####注册工厂
>在实际项目中，大多数情况下并不能照搬某个设计模式，现实总是比理想情况要复杂，还是要具体分析不同因素。很久之前的一个项目，可以说是工厂模式的演化。
![](/album/Screencap/factory2.jpg)
![](/album/Screencap/factory3.jpg)