# 1_Linux前置基础

## 概览

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

提交地址：<https://aicarrier.feishu.cn/share/base/form/shrcnUqshYPt7MdtYRTRpkiOFJd>

## 文档

### 1. InternStudio开发机介绍

InternStudio 是大模型时代下的云端算力平台。基于 InternLM 组织下的诸多算法库支持，为开发者提供开箱即用的大语言模型微调环境、工具、数据集，并完美兼容 🤗 HugginFace 开源生态。

InternStduio介绍文档： [InternStudio](https://studio.intern-ai.org.cn/)

开发机有三种模式可以选择：JupyterLab、终端和VScode

### 2. SSH及端口映射

#### SSH

SSH（Secure Shell）是一种网络协议，用于在网络上的计算机之间加密数据传输。它主要用于远程登录到服务器、执行远程命令、传输文件以及管理服务器。SSH 提供了一个安全的方式来访问和控制远程系统，即使这些系统位于不安全的网络（如互联网）上。

>特性

- 加密：SSH 使用加密技术来保护数据传输，防止数据被窃听或篡改。
- 认证：SSH 支持多种认证方式，包括密码、公钥/私钥对、一次性密码等。
- 端口转发：SSH 允许端口转发，可以通过 SSH 连接将本地或远程端口转发到另一台服务器，实现安全的数据传输。
- 隧道：SSH 可以创建隧道，用于安全地传输其他协议的数据，如 HTTP、HTTPS、FTP 等。
- 压缩：SSH 可以在传输数据之前对其进行压缩，以减少带宽消耗。
- 代理连接：SSH 可以作为 SOCKS 代理，用于通过 SSH 连接转发其他网络流量。

> 用途

- 远程登录：使用 SSH 命令 ssh 用户名@服务器地址 登录到远程服务器。
- 远程执行命令：通过 SSH 连接执行远程服务器上的命令。
- 文件传输：使用 scp（Secure Copy）或 sftp（Secure File Transfer Protocol）安全地传输文件。
- 端口转发：使用 SSH 端口转发访问远程网络服务，如数据库、内部网站等。
- 隧道：创建 SSH 隧道，为其他网络流量提供加密通道。
- 集群管理：管理多个服务器和集群，自动化部署和配置。
- VPN 替代：作为 VPN 的替代方案，为网络流量提供加密。

#### 端口映射

端口映射（Port forwarding）是一种网络技术，它允许网络数据通过一个中间设备（如路由器或防火墙）从一个端口转发到另一个端口。在使用 SSH（Secure Shell）时，端口映射可以用于安全地访问内部网络中的服务器或服务，或者在远程工作时访问家庭或办公室网络中的设备。

> 本地端口转发， 远程端口转发，动态端口转发

- 本地端口转发（Local Port Forwarding）

本地端口转发将本地计算机上的一个端口转发到远程服务器上的服务。这通常用于访问远程网络上的服务，如数据库或内部网站。

`ssh -L 本地端口:目标主机:目标端口 用户名@SSH服务器`

> 示例

将本地计算机的 3307 端口映射到 SSH 服务器上的 3306 端口，然后你可以在本地计算机上使用数据库客户端连接到 localhost:3307 来访问远程的 MySQL 服务器。

```bash
ssh -L 3307:localhost:3306 用户名@SSH服务器
```

- 远程端口转发（Remote Port Forwarding）

远程端口转发将远程计算机上的一个端口转发到本地计算机上的服务。这通常用于将远程服务暴露给本地网络。

```bash
ssh -R 远程端口:目标主机:目标端口 用户名@SSH服务器
```

> 示例

将 SSH 服务器上的 80 端口映射到本地计算机的 8080 端口，然后 SSH 服务器上的其他用户可以通过连接到 SSH 服务器的 80 端口来访问你的 Web 服务。

```bash
ssh -R 80:localhost:8080 用户名@SSH服务器
```

- 动态端口转发（Dynamic Port Forwarding）

动态端口转发，也称为 SOCKS 代理，允许你通过 SSH 隧道转发任意 TCP 流量。

```bash
ssh -D 本地端口 用户名@SSH服务器
```

> 示例

将创建一个 SOCKS 代理，监听本地计算机的 1080 端口, 配置完成后，你可以在浏览器或其他应用程序中设置 SOCKS 代理为 localhost:1080，通过 SSH 隧道安全地访问互联网。

```bash
ssh -D 1080 用户名@SSH服务器
```

### 3. Linux 基础命令

#### 1. 文件操作命令

查看文件内容：cat, more, less, head, tail
文件复制：cp
文件移动和重命名：mv
删除文件：rm
创建文件和目录：touch, mkdir
查看文件属性：ls, stat
修改文件权限：chmod
查找文件：find

#### 2. 文本处理命令

文本搜索：grep
文本替换：sed, awk
文本排序：sort
文本比较：diff

#### 3. 磁盘管理命令

查看磁盘空间：df, du
格式化磁盘：mkfs
挂载和卸载磁盘：mount, umount

#### 4. 系统监控命令

查看系统信息：uname, hostname
查看进程信息：ps, top, htop
杀死进程：kill
系统性能监控：vmstat, iostat, mpstat
查看系统日志：dmesg, journalctl

#### 5. 网络管理命令

查看网络配置：ifconfig, ip
查看网络连接：netstat
网络测试：ping, traceroute
服务管理：systemctl, service

#### 6. 用户和权限管理命令

用户管理：useradd, usermod, userdel
用户组管理：groupadd, groupmod, groupdel
权限管理：chown, chmod

#### 7. 压缩和解压缩命令

压缩文件：tar, gzip, zip
解压缩文件：tar, gunzip, unzip

#### 8. 备份和恢复命令

备份：rsync, tar
恢复：tar

#### 9. 包管理命令

Debian/Ubuntu：apt, apt-get, dpkg
Red Hat/CentOS：yum, dnf
Arch Linux：pacman

#### 10. 帮助命令

man：显示命令的手册页。
info：提供比手册页更详细的文档。
help：显示内置shell命令的帮助信息。
apropos：搜索命令关键字。

#### 11. 脚本编程命令  

基本的脚本语言：bash, sh
函数和循环控制：if, for, while, until, case

### 4. Conda和Shell介绍

## 作业

### 闯关任务 | 完成SSH连接与端口映射并运行`hello_world.py`

### 可选任务 1 | 将Linux基础命令在开发机上完成一遍

### 可选任务 2 | 使用 VSCODE 远程连接开发机并创建一个conda环境

## 小结

### 1. 如何在InternStudio创建开发机

1. 了解InternStudio开发机及三种开发模式：JupyterLab、终端和VScode
2. 每一个开发机都是一个Docker 容器

### 2. SSH，远程连接和端口映射

1. 熟悉ssh相关命令，配置ssh公钥
2. 了解并使用3种端口映射。（本地端口转发， 远程端口转发，动态端口转发）
3. 使用终端和vscode远程连接开发

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
