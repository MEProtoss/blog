---
title: 八股文骚套路之Java集合
abbrlink: 2ca694ee
date: 2024-06-08 15:04:20
tags:
---
## 集合概述

Java集合，也叫容器主要有两大接口派生而来

- Collection
  - List(列表):有序可重复
    - ArrayList
    - Vector
    - LinkedList(双向链表)
  - Set(集合)：不可重复/唯一
    - HashSet(无序唯一)
      - LinkedHashSet:底层使用LinkedHashMap实现
    - TreeSet(有序唯一)：红黑树(自平衡排序二叉树)
  - Queue(队列)：特定的排序规则，有序可重复
- Map(映射 可以多对一，不能一对多)
  - HashMap：JdK1.8之前是数组+链表，JdK1.8之后在链表长度大于阈值8的时候会将链表转化为红黑树以减少搜索时间，但是在转化之前还会判断当前的哈希桶数组(用来存键值对的数组)的长度是不是小于64，如果不是，那么会先对数组进行扩容。
    - LinkedHashMap:在HashMap的基础上增加了一条双向链表，使HashMap的结构可以保持键值对的插入顺序
  - Hashtable
  - SortedMap

> [!TIP]
> 在 HashMap 中，主要有一个用于存储键值对的数组，这个数组被称为“哈希桶数组”或“Entry 数组”。在 JDK 1.8 之前，HashMap 的底层数据结构由一个数组 + 链表组成。数组的每个元素（称为桶或者 Entry）都是一个链表的头节点，每个节点存储一个键值对。当发生哈希冲突时，具有相同哈希值的键值对会被放置在同一个桶中，通过链表形式串联在一起。
>
### 如何选用集合？

- 需要根据键值获取元素则选Map接口下的集合，需要排序则用TreeMap，不需要排序则选HashMap，需要线程安全就用ConcurrentHashMap,尽量不用HashTable

- 当只需要存放元素值的时候选用Collection接口的集合，需要唯一用Set接口下的集合，比如TreeSet和HashSet，不需要就用List下的接口比如ArrayList和LinkedList。


### ArrayList(数组列表) 和 Array（数组）的区别？

ArrayList 内部基于动态数组实现，比 Array（静态数组） 使用起来更加灵活

- ArrayList可以动态地扩容或缩容，而 Array 被创建之后就不能改变它的长度了。
- ArrayList 允许你使用泛型来确保类型安全，Array 则不可以。
- ArrayList 中只能存储对象。对于基本类型数据，基本数据类型要使用包装类。Array 可以直接存储基本类型数据，也可以存储对象。
- ArrayList 支持插入、删除、遍历等常见操作，并且提供了丰富的 API 操作方法，比如 add()、remove()等。Array 只是一个固定长度的数组，只能按照下标访问其中的元素，不具备动态添加、删除元素的能力。
- ArrayList创建时不需要指定大小，而Array创建时必须指定大小。

### ArrayList 与 LinkedList 区别?

两者都是线程不安全的

然后记住ArrayList 采用数组存储 LinkedList 采用链表存储,再根据底层数据结构从插入删除元素，随机访问，内存空间占用上展开来将就行

## Set

### Comparable 和 Comparator 的区别

Comparable 接口和 Comparator 接口都是 Java 中用于排序的接口, 用于在类对象之间比较大小、排序

一般我们需要对一个集合使用自定义排序时，我们就要重写compareTo()方法或compare()方法

### 无序性和不可重复性的含义是什么

- 无序性指的是存储的数据在底层数组中的顺序不是按照数组索引的顺序添加，而是根据数据的哈希值决定

- 不可重复性指 equals() 判断的时候返回false，所以需要同时重写equals方法和hashcode方法

