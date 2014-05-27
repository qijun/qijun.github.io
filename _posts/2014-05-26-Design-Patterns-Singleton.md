---
date: 2014-05-25 20:58:00+00:00
layout: post
title: 设计模式笔记:单例
categories : Design Patterns
thread: 104
tags : [Design Patterns,Notes]
---

###设计模式:单例
***
####场景
单例，简单理解就是只能实例化一个对象，和静态类使用意图相似，但是类不可赋值和传递。使用场景多用于一些工具类（不想重复使用static），含有系统限制资源的类（如数据库，日志工具）和一些全局计数的类。暂时就想到这些...
单例不是用来适应变化的，而是为了限制扩展。
####常见实现
    public sealed class Singletons
    {
        private static readonly Singletons _instance = new Singletons();

        private Singletons() { }

        public static Singletons Instance
        {
            get { return _instance; }
        }
    }
缺点：无法控制实例化时间
####加锁版本
	///<summary>
    ///知识点：
    ///[静态构造函数](http://msdn.microsoft.com/zh-cn/library/k9x6w0hc.aspx)
    ///[readonly](http://msdn.microsoft.com/zh-cn/library/acdd6hb7.aspx)
    ///</summary>
    public sealed class Singleton
    {
        private static volatile Singleton _instance;
        private static readonly object _syncRoot;

        private Singleton() { }

        public static Singleton Instance
        {
            get
            {
                if(_instance==null)
                    lock (_syncRoot)
                    {
                        if (_instance == null)
                            _instance = new Singleton();
                    }
                return _instance;
            }
        }
    }
	
####泛型版本
	 public abstract class Singleton<T>
		{
			private static readonly Lazy<T> _instance = new Lazy<T>(() =>
			{
				var ctors = typeof(T).GetConstructors(
					BindingFlags.Instance
					| BindingFlags.NonPublic
					| BindingFlags.Public);
				if (ctors.Count() != 1)
					throw new InvalidOperationException(string.Format("Type {0} must have exactly one constructor.", typeof(T)));
				var ctor = ctors.SingleOrDefault(c => c.GetParameters().Count() == 0 && c.IsPrivate);
				if(ctor==null)
					throw new InvalidOperationException(string.Format("The constructor for {0} must be private and take no parameters.",typeof(T)));
				return (T)ctor.Invoke(null);

			});

			public static T Instance
			{
				get { return _instance.Value; }
			}
		}

###总结
####扩展应用
*单例集合
####优点:
1.只有一个实例
2.类自身负责实例化过程
####缺点:
1.增加开销
2.无法销毁对象
***
参考文档
汤姆大叔的博客：[别再让面试官问你单例（暨6种实现方式让你堵住面试官的嘴）]（http://www.cnblogs.com/TomXu/archive/2011/12/19/2291448.html）