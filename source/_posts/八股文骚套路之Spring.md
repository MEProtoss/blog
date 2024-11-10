---
title: 八股文骚套路之Spring
abbrlink: 5b1a3186
date: 2024-10-21 11:55:52
tags:
---

## 谈谈对ioc的理解

- 将手动**创建对象的控制权**交由**外部环境**Spring框架处理

## 什么是Bean?

- 代指被IoC容器管理的对象

## 将一个类声明为Bean的注解有哪些？

- @Component
- @Repository
- @Service
- @Controller

## @Component 和 @Bean 的区别是什么？

- @Component 注解作用于类，而@Bean注解作用于方法
- @Component通常是通过类路径扫描来自动侦测以及**自动装配**到 Spring 容器中（我们可以使用@ComponentScan 注解定义要扫描的路径,从中找出标识了需要装配的类自动装配到 Spring 的 bean 容器中）。@Bean 注解通常是我们在标有该注解的方法中定义产生这个 bean,@Bean告诉了 Spring 这是某个类的实例，当我需要用它的时候还给我。
- @Bean 注解比 @Component 注解的自定义性更强，而且很多地方我们只能通过 @Bean 注解来注册 bean。比如当我们引用第三方库中的类需要装配到 Spring容器时，则只能通过 @Bean来实现

## @Autowired 和 @Resource 的区别是什么？

- @Autowired 是 Spring 提供的注解，@Resource 是 JDK 提供的注解。
- Autowired 默认的注入方式为byType（根据类型进行匹配），@Resource默认注入方式为 byName（根据名称进行匹配）。当一个接口存在多个实现类的情况下，@Autowired 和@Resource都需要通过名称才能正确匹配到对应的 Bean。
- Autowired 可以通过 @Qualifier 注解来显式指定名称，@Resource可以通过 name 属性来显式指定名称。
- @Autowired 支持在构造函数、方法、字段和参数上使用。@Resource 主要用于字段和方法上的注入，不支持在构造函数或参数上使用。
