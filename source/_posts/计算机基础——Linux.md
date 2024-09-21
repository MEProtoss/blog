---
title: 计算机基础——Linux
abbrlink: f7999b22
date: 2024-09-20 15:33:09
tags:
---

## inode

index + node

inode就是用来维护某个文件被分成几块、每一块在的地址、文件拥有者，创建时间，权限，大小等信息。

## Linux常用指令

| 指令| 作用    |
|--------------- | --------------- |
| stat   | 查看文件的 inode 信息   |
| ln   | 创建硬链接   |
| file   | 查看文件类型信息   |
| tar | 压缩和解压缩|
| ls -l| 查看某个目录下的文件或目录的权限|
| top | 查看系统的 CPU 使用率、内存使用率、进程信息等|
|systemctl| 查看系统服务的状态、启动、停止、重启等|

## Linux获取实时刷新的日志

```bash
# 实时刷新
tail -f logfile.log
# 每5分钟执行一次查询
watch -n 300 'tail logfile.log'

journalctl -f
```

