---
layout: w
title: Java Exception体系
date: 2021-01-01 16:44:42
tags:
---

先看下Java异常处理类体系
=============

![throwable](/images/throwable.png)
主要分不可恢复的Error类，和异常类exception。Exception又分为checked和unchecked Exception，通俗的讲就是分编译器检查异常类和非编译器检查类，Exception的子类除RuntimeException以外都是checked Exception, RuntimeException的子类都是unchecked Exception；
<!-- more -->

Java Exception 关键字
=============

涉及五个关键字：try， catch， finally， throw， throws，一一解释下
try是指定我们需要捕捉异常的代码块；
catch是处理捕捉的异常；
finally是执行关键代码；
throw是抛出异常；
throws是定义异常，和try catch写法作用一样；

throw和throws区别
=============

![Throw](/images/different_throw_and_throws.png)

参考：https://www.javatpoint.com/difference-between-throw-and-throws-in-java
以上内容参考：https://www.javatpoint.com/exception-handling-in-java
