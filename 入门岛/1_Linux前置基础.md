# 1_Linux前置基础

## 概览【入门岛】

|         | 关卡名称                | 资料                                                                                                                                                                                                       | 闯关激励   |
| :------ | :--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- |
| 第 1 关 | Linux 前置基础          | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/linux/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/linux)、[视频](https://www.bilibili.com/video/BV13U1VYmEUr)   | 50元算力点 |
| 第 2 关 | Python 前置基础         | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/Python/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/Python)、[视频](https://www.bilibili.com/video/BV1u61jYSExg) | 50元算力点 |
| 第 3 关 | Git 前置基础            | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/git/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/git/)、[视频](https://www.bilibili.com/video/BV15MShYkEgg)      | 50元算力点 |
| 第 4 关 | 玩转「HF/魔搭/魔乐」平台 | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/maas/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/maas)、[视频](https://www.bilibili.com/video/BV1XxStYYEH1/)    | 50元算力点 |

## 任务

> [task.md](https://github.com/InternLM/Tutorial/blob/camp4/docs/L0/Linux/task.md)

闯关任务需要在关键步骤中截图：

|            | 任务描述                                      | 完成所需时间 |
| ---------- | --------------------------------------------- | ------------ |
| 闯关任务   | 完成SSH连接与端口映射并运行`hello_world.py`   | 10min        |
| 可选任务 1 | 将Linux基础命令在开发机上完成一遍             | 10min        |
| 可选任务 2 | 使用 VSCODE 远程连接开发机并创建一个conda环境 | 10min        |


请将作业发布到知乎、CSDN等任一社交媒体，将作业链接提交到以下问卷，助教老师批改后将获得 50 算力点奖励！！！

提交地址：https://aicarrier.feishu.cn/share/base/form/shrcnUqshYPt7MdtYRTRpkiOFJd

## 文档
### 1. InternStudio开发机介绍

InternStudio 是大模型时代下的云端算力平台。基于 InternLM 组织下的诸多算法库支持，为开发者提供开箱即用的大语言模型微调环境、工具、数据集，并完美兼容 🤗 HugginFace 开源生态。

InternStduio介绍文档： [InternStudio](https://studio.intern-ai.org.cn/)

开发机有三种模式可以选择：JupyterLab、终端和VScode

### 2. SSH及端口映射


### 3. Linux 基础命令
1. 文件操作命令：

查看文件内容：cat, more, less, head, tail
文件复制：cp
文件移动和重命名：mv
删除文件：rm
创建文件和目录：touch, mkdir
查看文件属性：ls, stat
修改文件权限：chmod
查找文件：find

2. 文本处理命令：

文本搜索：grep
文本替换：sed, awk
文本排序：sort
文本比较：diff

3. 磁盘管理命令：

查看磁盘空间：df, du
格式化磁盘：mkfs
挂载和卸载磁盘：mount, umount

4. 系统监控命令：

查看系统信息：uname, hostname
查看进程信息：ps, top, htop
杀死进程：kill
系统性能监控：vmstat, iostat, mpstat
查看系统日志：dmesg, journalctl

5. 网络管理命令：

查看网络配置：ifconfig, ip
查看网络连接：netstat
网络测试：ping, traceroute
服务管理：systemctl, service

6. 用户和权限管理命令：

用户管理：useradd, usermod, userdel
用户组管理：groupadd, groupmod, groupdel
权限管理：chown, chmod

7. 压缩和解压缩命令：

压缩文件：tar, gzip, zip
解压缩文件：tar, gunzip, unzip

8. 备份和恢复命令：

备份：rsync, tar
恢复：tar

9. 包管理命令：

Debian/Ubuntu：apt, apt-get, dpkg
Red Hat/CentOS：yum, dnf
Arch Linux：pacman

10. 帮助命令：

man：显示命令的手册页。
info：提供比手册页更详细的文档。
help：显示内置shell命令的帮助信息。
apropos：搜索命令关键字。

11. 脚本编程命令：

基本的脚本语言：bash, sh
函数和循环控制：if, for, while, until, case

### 4. Conda和Shell介绍

## 作业

###  闯关任务 | 完成SSH连接与端口映射并运行`hello_world.py`


### 可选任务 1 | 将Linux基础命令在开发机上完成一遍


### 可选任务 2 | 使用 VSCODE 远程连接开发机并创建一个conda环境


## 小结
### 1. 如何在InternStudio创建开发机
### 2. SSH，远程连接和端口转发
### 3. Linux常用命令
1. 文件操作命令：用于文件和目录的创建、删除、复制、移动、查看等。
2. 文本处理命令：用于文本的搜索、替换、排序、比较等。
3. 磁盘管理命令：用于磁盘的分区、格式化、挂载、空间查看等。
4. 系统监控命令：用于系统性能监控、进程管理、系统信息查看等。
5. 网络管理命令：用于网络配置、网络状态查看、网络测试等。
6. 用户和权限管理命令：用于用户和组的创建、删除、权限设置等。
7. 压缩和解压缩命令：用于文件的压缩和解压缩。
8. 备份和恢复命令：用于数据的备份和恢复。
9. 包管理命令：用于软件包的安装、升级、卸载等。
10. 帮助文档命令：查看命令手册、获取帮助信息等。
11. 脚本编程命令：用于编写和执行Shell脚本。