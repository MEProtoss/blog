---
title: 八股文骚套路之Linux
abbrlink: f7999b22
date: 2024-09-20 15:33:09
tags:
---

## inode（索引节点）

unix系统中用于存储文件元数据的数据结构

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
# 每5分钟执行一次查询(watch -n 300 表示每300s执行一次后面的命令)
watch -n 300 'tail logfile.log'

journalctl -f
```

## 进程相关

```bash
# 查看进程
ps -ef | grep xxx

# 杀死进程
kill -9 PID

# 查看端口号
lsof -i:PORT

# 查看系统进程
top
ps

# 查看文件a的第7到9行 (head表示展示前几行，tail表示展示后几行)
cat a.txt | tail -n +7 | head -n 9

# 查看a.txt的第5行
head a.txt -n 5 | tail -n 1
```

## 给文件夹或者文件增加权限

```bash
chmod +777
```

## 一次性关闭所有和qq相关的进程

```shell
killall qq

```
