---
title: Linux系统疑难杂症
abbrlink: c66bafdb
date: 2024-05-07T09:36:08.000Z
tags: null
---
## ideaVim中英文输入法切换问题

1. 安装ideaVimExtension 插件
2. .ideavimrc中开启

```language
set keep-english-in-normal
set keep-english-in-normal-and-restore-in-insert
```

## idea中输入法不跟随鼠标的问题

### 问题原因

具体问题官方其实七年前就有了（参考 <https://youtrack.jetbrains.com/issue/JBR-2460），但是比较坑的是官方也一直没有解决这个问题🐶（此处忍不住吐槽一下哈）。简单来说就是> Idea 的 jre 运行环境一个 bug，导致输入法无法定位到鼠标位置。因此，我们要解决该问题必须要修改 JetBrainsRuntime 的运行代码。

### 解决方法

- 下载已经修改好的 JRE 环境
[下载地址](https://www.jianguoyun.com/p/De33XAgQ89jhCRjDh8EFIAA：)
- 替换idea目录的JRE

## 无法识别移动硬盘和U盘

### 问题原因

文件系统不兼容

### 解决方法

```shell
sudo pacman -S ntfs-3g

```

## steam加速

```shell
yay -S watt-toolkit-bin

```

