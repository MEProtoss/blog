---
title: Java新特性
abbrlink: 9ac696fa
date: 2024-05-08 22:54:02
tags:
---
## 函数式接口(functional interface)
定义：也称 SAM 接口，即 Single Abstract Method interfaces，有且只有一个抽象方法，但可以有多个非抽象方法的接口。

在 java 8 中专门有一个包放函数式接口java.util.function，该包下的所有接口都有 @FunctionalInterface 注解，提供函数式编程。在其他包中也有函数式接口，其中一些没有@FunctionalInterface 注解，但是只要符合函数式接口的定义就是函数式接口，与是否有@FunctionalInterface注解无关，注解只是在编译时起到强制规范定义的作用。其在 Lambda 表达式中有广泛的应用。

基本上，函数式编程是一种编程风格，它将计算看作为是数学函数的求值。

在数学中，函数是将输入集与输出集相关联的表达式。函数的输出仅取决于其输入。我们也可以将两个或多个函数组合在一起得到一个新函数
