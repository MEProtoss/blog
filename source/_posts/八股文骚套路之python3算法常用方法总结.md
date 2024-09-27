---
title: 八股文骚套路之python3算法常用方法总结
abbrlink: 495bdedc
date: 2024-09-26 14:12:57
tags:
---
## 遍历

- enumerate() 函数用于同时获取字符的索引 j 和字符值 c。

- set(nums) 可以将数组直接转化为集合，做到去重获取其中所有元素

- 交换数组中的两个元素，不需要像java那样使用temp，直接写在一行中交换即可

```python3

nums[cur], nums[index] = nums[index], nums[cur]

```

- map() 是一个内置函数，用于将函数应用于可迭代对象（如列表、元组等）的每个元素，**并返回一个迭代器**。它的基本语法如下：

map(function, iterable)

例如：

```python3
# 注意 因为返回的是一个迭代器，因此注意使用的时候要进行类型转换
nums_ = list(map(int, nums)) 

```
