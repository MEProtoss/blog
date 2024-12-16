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

## nvim中的可视化数据库插件

```shell
url:mysql://root:123456@127.0.0.1:3306/name


```

## linux命令行下spring的使用

```shell
# 刷新pom文件
mvn clean install

# 启动springboot项目
mvn spring-boot:run
```

## 字体问题

```shell

# 安装win11系统中提取的简体中文的镜像
yay -S ttf-ms-win11-fod-auto-hans

# 刷新缓存

fc-cache


```

## Linux解压windows压缩文件出现乱码

- 病因：字符集问题
- 解决方案：使用中文字符集解压

```shell

unzip -O gb18030 example.zip

```

## mount: unknown filesystem type ‘ntfs’

病因：使用的U盘文件为ntfs类型

- 安装ntfs-3g

## 如何将损坏的archlinux 恢复到之前的工作状态 尤其是无法正常进入系统的时候

- 单用户模式进入系统

  - grub 菜单的时候输入e
  
    ![img](/home/time/文档/Notes/CS自学笔记/Linux笔记/linux疑难杂症.assets/edit-grub-1.jpg)

- 找到以linux开头的行 在末尾添加 `init=/bin/bash` ，然后按F10或c-x进入单系统模式

![img](/home/time/文档/Notes/CS自学笔记/Linux笔记/linux疑难杂症.assets/edit-grub-1-1.jpg)

- 以读/写模式挂载根文件系统

  ```bash
  mount -n -o remount,rw /
  ```

- 去解决问题(例如通过日志解决)

```bash
tail -n 200 /var/log/pacman.log | less
# tail 命令将仅显示最后 10 条条目。因此，请将 200 替换为您自己的号码，以查看 pacman.log 文件。我将 "tail" 命令的输出通过管道传输到 "less" 命令以逐页显示结果。
```

## linux配置开机免密码登录

step1:

```shell
~ sudo nvim /etc/systemd/system/getty.target.wants/getty@tty1.service

  ExecStart=-/sbin/agetty --autologin time --noclear %I $TERM

```

step2:

```shell
~ sudo visudo
[用户名] ALL=(ALL:ALL) NOPASSWD: ALL

用户提权
yay -S polkit


```

## 可视化网络管理工具

nm-connection-editor

## 一些好玩的小工具

[终端玩具](https://arch.icekylin.online/guide/advanced/beauty-3.html#_2-zsh-%E7%BE%8E%E5%8C%96)

## 包管理工具pacman和yay

```bash
sudo pacman -S package_name # 安装软件包
pacman -Ss # 在同步数据库中搜索包，包括包的名称和描述
sudo pacman -Syu # 升级系统。 -y:标记刷新、-yy：标记强制刷新、-u：标记升级动作（一般使用 -Syu 即可）
sudo pacman -Rns package_name # 删除软件包，及其所有没有被其他已安装软件包使用的依赖包
sudo pacman -R package_name # 删除软件包，保留其全部已经安装的依赖关系
pacman -Qi package_name # 检查已安装包的相关信息。-Q：查询本地软件包数据库
pacman -Qdt # 找出孤立包。-d：标记依赖包、-t：标记不需要的包、-dt：合并标记孤立包
sudo pacman -Rns $(pacman -Qtdq) # 删除孤立包
sudo pacman -Fy # 更新命令查询文件列表数据库
pacman -F some_command # 当不知道某个命令属于哪个包时，用来在远程软件包中查询某个命令属于哪个包（即使没有安装）
pactree package_name # 查看一个包的依赖树

```

- yay 的用法和 Pacman 是基本一样的。有额外几条常用命令：

```bash
yay # 等同于 yay -Syu
yay package_name # 等同于 yay -Ss package_name && yay -S package_name
yay -Ps # 打印系统统计信息
yay -Yc # 清理不需要的依赖

```

- 可视化包管理工具

```bash
yay -S octopi
```

## 安装conda以及安装conda之后的问题

### 安装

- 原生的Python环境建议安装一个pip

```bash
sudo pacman -S python-pip
```

- 安装conda:yay包管理工具中有两个关于miniconda的包，但是关于写入opt/miniconda权限会有问题，因此建议自己从官网下载，然后添加到环境变量

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```

- 添加环境变量，本来是 PATH=~/miniconda3/bin:$PATH
修改为 -> PATH=$PATH:~/miniconda3/bin
因为在安装软件时，使用 conda 作为基础 Python 环境时，会发生错误，要求使用系统自带的 Python3。

```bash
eval "$(~/miniconda3/bin/conda shell.zsh hook)"
export PATH=$PATH:~/miniconda3/bin
```

### 一打开终端就默认进入conda的base环境

- 在终端修改配置：conda官方文档中有conda config 的相关使用介绍，其中有conda config --show的说明：
Display configuration values as calculated and compiled. If no arguments given,
show information for all configuration values.

所以在终端输入conda config --show，会显示所有的配置信息。

然后就可利用`conda config --set`来修改配置

```bash
conda config --set auto_activate_base false

```
