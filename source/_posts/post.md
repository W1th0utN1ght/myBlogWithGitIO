---
title: Spring IOC 容器
date: 2020-08-19 15:56:38
tags: 
- Spring
categories: 
- 业务开发相关
---

IOC容器在Spring中实质上往往是一个不可见的角色，当SpringBoot被大量装配之后，使用者真正意义上的只需要提供功能与消费功能提供方所提供的功能，而中间所转接这些功能模块的中间人已经不断被弱化和模糊。

但是回归到Spring，实质上IOC容器仍然是其不可忽略的核心模块。BeanFactory与ApplicationContext似乎都可以提供注入之后的Bean，那么<!--more-->：

* ### BeanFactory与ApplicationContext谁才是SpringIOC容器？

  总的来说，都是。因为实际上在继承这个角度来说的话，ApplicationContext是继承自BeanFactory的，同时提供了getBeanFactory的方式来获取到其对应的BeanFactory，但是与想象中的不一样的是，其中的BeaFactory实际上是通过组合的方式被引入到ApplicationContext中，ApplicationContext比之BeanFactory有更多的一些功能与实现。当然，最终来看两者都是可以正常使用的。

  #### 除了IoC容器角色以外，ApplicationContext还提供了哪些特性？

  * 面向切面
  * 配置元信息
  * 资源管理
  * 事件
  * 注解
  * Environment抽象

   BeanFactory它是一个容器，但也仅仅是一个容器，不会有再多的含义，可以认为，Bean会再这个Factory中取出来之后对外提供该Bean的相关能力，因此其实就是说，如果我有一个Bean需要使用，BeanFactory可以将其进行外露。

    但是Bean是如何进入到BeanFactory中，以及当前上下文的一些信息，对于BeanFactory而言都是对其的强求。它的作用正如它的名称一样，仅仅是一个提供Bean的Factory。

    而ApplicationContext则是对刚刚我所说的一些特殊的解法，因此可以简单的认为ApplicationContext就是BeanFactory的超集。

  