# 3_Git前置基础

## 概览

|         | 关卡名称                | 资料                                                                                                                                                                                                       | 闯关激励   |
| :------ | :--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- |
| 第 1 关 | Linux 前置基础          | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/linux/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/linux)、[视频](https://www.bilibili.com/video/BV13U1VYmEUr)   | 50元算力点 |
| 第 2 关 | Python 前置基础         | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/Python/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/Python)、[视频](https://www.bilibili.com/video/BV1u61jYSExg) | 50元算力点 |
| 第 3 关 | Git 前置基础            | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/git/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/git/)、[视频](https://www.bilibili.com/video/BV15MShYkEgg)      | 50元算力点 |
| 第 4 关 | 玩转「HF/魔搭/魔乐」平台 | [任务](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/maas/task.md)、[文档](https://github.com/InternLM/Tutorial/tree/camp4/docs/L0/maas)、[视频](https://www.bilibili.com/video/BV1XxStYYEH1/)    | 50元算力点 |

## 任务

```html
<table style="width: 100%; margin: auto;">
  <tr>
    <th>任务编号</th>
    <th>任务名称</th>
    <th>任务描述</th>
  </tr>
  <tr>
    <td>1</td>
    <td>破冰活动</td>
    <td>提交一份自我介绍。</td>
  </tr>
  <tr>
    <td>2</td>
    <td>实践项目</td>
    <td>创建并提交一个项目。</td>
  </tr>
</table>
```

### 任务1: 破冰活动：自我介绍

每位参与者提交一份自我介绍。
提交地址：<https://github.com/InternLM/Tutorial> 的 class 分支～

1. 命名格式为 `<id>.md`，其中 `<id>` 是您的报名问卷UID。
2. 文件路径应为 `./icamp4/`。
3. 【大家可以叫我】内容可以是 GitHub 昵称、微信昵称或其他网名。
4. 在 GitHub 上创建一个 Pull Request，提供对应的 PR 链接。

### 任务2: 实践项目：构建个人项目

1. 创建并维护一个公开的大模型相关项目或笔记仓库。
2. 提交作业时，提供您的 GitHub 仓库链接。
3. 如果您不常使用 GitHub，您可以选择其他代码管理平台，如 Gitee，并提交相应的链接。
4. 仓库介绍中添加超链接跳转 [GitHub 仓库](https://github.com/InternLM/Tutorial)（`<u>[https://github.com/InternLM/Tutorial](https://github.com/InternLM/Tutorial)</u>`）
5. 将此项目报名参加第四期实战营项目评选将解锁 30% A100 和 168 团队算力点资源，报名链接：<https://aicarrier.feishu.cn/wiki/JuXvwHzGni2A2Rksd8Rczpvxngb>

## 文档

### 1. Git基本概念

Git 是一个分布式版本控制系统，广泛用于软件开发和协作项目管理。它允许开发者跟踪代码的变化历史，协同工作，并在多个分支之间切换。

#### 工作区、暂存区和 Git 仓库区

- 工作区（Working Directory）： 当我们在本地创建一个 Git 项目，或者从 GitHub 上 clone 代码到本地后，项目所在的这个目录就是“工作区”。这里是我们对项目文件进行编辑和使用的地方。

- 暂存区（Staging Area）： 暂存区是 Git 中独有的一个概念，位于 .git 目录中的一个索引文件，记录了下一次提交时将要存入仓库区的文件列表信息。使用 git add 指令可以将工作区的改动放入暂存区。

- 仓库区 / 本地仓库（Repository）： 在项目目录中，.git 隐藏目录不属于工作区，而是 Git 的版本仓库。这个仓库区包含了所有历史版本的完整信息，是 Git 项目的“本体”

#### 文件状态

文件在 Git 工作区中的状态可以是：

- 已跟踪：文件已被纳入版本控制，根据其是否被修改，可以进一步分为未修改（Unmodified）、已修改（Modified）或已暂存（Staged）。
- 未跟踪：文件存在于工作目录中，但还没被纳入版本控制，也未处于暂存状态。

| 状态 |         未跟踪Untrack         |           未修改Unmodified           |           已修改Modified            |         已暂存Staged          |
| ---- | ----------------------------- | ------------------------------------ | ---------------------------------- | ----------------------------- |
| 说明 | "即新建的文件，并未被git所管理" | "文件的内容没有写入修改，已经被git管理" | "文件的内容被写入修改，已经被git管理" | "文件的内容暂存，已经被git管理" |

#### 分支

分支是 Git 的一大特性，支持轻量级的分支创建和切换。Git 鼓励频繁使用分支和合并，使得并行开发和错误修正更为高效。

#### 主要功能

- 代码历史记录跟踪

Git 记录每一次代码提交，允许用户查看项目的历史版本和变更记录，从而理解每个阶段的开发细节。

- 团队协作

支持多人同时对同一项目工作，提供了合并、分支和版本控制的功能，以确保多人协作的效率和代码的整合性。

- 变更审查

允许开发者查看代码变更的具体内容，了解谁在何时做了哪些修改，这对于代码审查和质量控制至关重要。

- 实现机制

|    特性    |                                                                   描述                                                                    |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| 分布式架构 | 与集中式版本控制系统不同，Git 在每个开发者的机器上都存有完整的代码库副本，包括完整的历史记录。这种分布式的特性增强了数据的安全性和获取效率。             |
| 分支管理   | Git 的分支管理功能非常灵活，支持无缝切换到不同的开发线路（分支），并允许独立开发、测试新功能，最终通过合并操作将这些功能稳定地集成到主项目中。           |
| 快照系统   | Git 通过快照而非差异比较来管理数据。每次提交更新时，Git 实际上是在存储一个项目所有文件的快照。如果文件没有变化，Git 只是简单地链接到之前存储的文件快照。 |

### 2. Git 平台介绍

#### **2.1 [**GitHub**](https://github.com/)**

是全球最大的代码托管平台之一，拥有丰富的开源项目和活跃的开发者社区。它提供了版本控制、项目管理、协作开发等功能，并支持多种编程语言。

#### **2.2 [**GitLab**](https://gitlab.com/)**

一个自托管或基于云的平台，提供了完整的 DevOps 工具链，包括代码托管、持续集成/持续部署（CI/CD）、问题跟踪等。

#### **2.3 [**Gitee**](https://gitee.com/)**

国内的代码托管平台，提供了代码托管、项目管理、协作开发等功能，对国内开发者来说，访问速度可能更快，也更符合国内的使用习惯。

### 3. Git 下载配置验证

#### 3.1 下载 Git

##### Windows

- 下载并安装适合您 Windows 版本的安装程序：[下载地址](https://git-scm.com/download/win)
- 按照安装向导完成安装。(默认设置安装即可)
- 打开终端（win+r→cmd），输入指令 `git --version` 检查是否安装成功。

##### Linux

- 打开终端，输入指令

   ```bash
   sudo apt-get install git #安装 Git。
   sudo apt-get update
   sudo apt-get upgrade
   ```

- 输入指令 `git --version` 检查是否安装成功。

#### 3.2 配置 Git

```html
<details>

<summary>全局设置于本地设置的区别：</summary>

**全局设置**：这些设置影响你在该系统上所有没有明确指定其他用户名和电子邮件的 Git 仓库。这是设置默认用户名和电子邮件的好方法。

**本地设置**：这些设置仅适用于特定的 Git 仓库。这对于你需要在不同项目中使用不同身份时很有用，例如区分个人和工作项目。

</details>
```

##### 全局设置 (要是私人电脑可以直接用全局设置)

   打开终端或命令提示符，并输入以下命令来设置全局用户名和电子邮件地址：

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

   这里的 `"Your Name"` 和 `"your.email@example.com"` 应替换为你自己的姓名和电子邮件。

##### 本地设置

   首先，确保你当前处于你想要配置的 Git 仓库的目录中。然后，输入以下命令来仅为该仓库设置用户名和电子邮件地址：

   ```bash
   git config --local user.name "Your Name"
   git config --local user.email "your.email@example.com"
   ```

   同样，替换 `"Your Name"` 和 `"your.email@example.com"` 为该特定项目中使用的姓名和电子邮件。

#### 3.3 验证 Git配置

验证这些设置以确保它们被正确应用。

- **查看全局配置**：

```bash
  git config --global --list
```

- **查看仓库配置**：

```bash
  git config --local --list
```

- **永久保存信息至本地**:

```bash
   #来设置 Git自动记录密码(token)，从而无需在每次 pull 或 push 时输入# 注意:信息会以明文存储在本地，需考虑安全性
   git config --global credential.helper store
```

- **查看特定配置项**：

```bash
  git config user.name
  git config user.email
```

### 4. Git常用操作

#### 4.1 Git简易入门四部曲

在Git入门当中我们只需要明白一下常用四个指令，即可轻松玩耍

对这四个指令我们可以称为 **"Git 经典四步曲"**

在Git的日常使用中，下面四步曲是常用的流程，尤其是在团队协作环境中。

- **添（Add）**
  - **命令**：`git add <文件名>` 或 `git add .`
  - **作用**：将修改过的文件添加到本地暂存区（Staging Area）。这一步是准备阶段，你可以选择性地添加文件，决定哪些修改应该被包括在即将进行的提交中。

- **提（Commit）**
  - **命令**：`git commit -m '描述信息'`
  - **作用**：将暂存区中的更改提交到本地仓库。这一步是将你的更改正式记录下来，每次提交都应附带一个清晰的描述信息，说明这次提交的目的或所解决的问题。

- **拉（Pull）**
  - **命令**：`git pull`
  - **作用**：从远程仓库拉取最新的内容到本地仓库，并自动尝试合并到当前分支。这一步是同步的重要环节，确保你的工作基于最新的项目状态进行。在多人协作中，定期拉取可以避免将来的合并冲突。

- **推（Push）**
  - **命令**：`git push`
  - **作用**：将本地仓库的更改推送到远程仓库。这一步是共享你的工作成果，让团队成员看到你的贡献。

帮助团队成员有效地管理和同步代码，避免工作冲突，确保项目的顺利进行。正确地使用这些命令可以极大地提高开发效率和协作质量。

#### 4.2 Git其他指令

> 常用指令

```html
<table align="center">
  <tr>
    <th>指令</th>
    <th>描述</th>
  </tr>
  <tr>
    <td><code>git config</code></td>
    <td>配置用户信息和偏好设置</td>
  </tr>
  <tr>
    <td><code>git init</code></td>
    <td>初始化一个新的 Git 仓库</td>
  </tr>
  <tr>
    <td><code>git clone</code></td>
    <td>克隆一个远程仓库到本地</td>
  </tr>
  <tr>
    <td><code>git status</code></td>
    <td>查看仓库当前的状态，显示有变更的文件</td>
  </tr>
  <tr>
    <td><code>git add</code></td>
    <td>将文件更改添加到暂存区</td>
  </tr>
  <tr>
    <td><code>git commit</code></td>
    <td>提交暂存区到仓库区</td>
  </tr>
  <tr>
    <td><code>git branch</code></td>
    <td>列出、创建或删除分支</td>
  </tr>
  <tr>
    <td><code>git checkout</code></td>
    <td>切换分支或恢复工作树文件</td>
  </tr>
  <tr>
    <td><code>git merge</code></td>
    <td>合并两个或更多的开发历史</td>
  </tr>
  <tr>
    <td><code>git pull</code></td>
    <td>从另一仓库获取并合并本地的版本</td>
  </tr>
  <tr>
    <td><code>git push</code></td>
    <td>更新远程引用和相关的对象</td>
  </tr>
  <tr>
    <td><code>git remote</code></td>
    <td>管理跟踪远程仓库的命令</td>
  </tr>
  <tr>
    <td><code>git fetch</code></td>
    <td>从远程仓库获取数据到本地仓库，但不自动合并</td>
  </tr>
</table>
```

> 进阶指令

```html
<table align="center">
  <tr>
    <th>指令</th>
    <th>描述</th>
  </tr>
  <tr>
    <td><code>git stash</code></td>
    <td>暂存当前工作目录的修改，以便可以切换分支</td>
  </tr>
  <tr>
    <td><code>git cherry-pick</code></td>
    <td>选择一个提交，将其作为新的提交引入</td>
  </tr>
  <tr>
    <td><code>git rebase</code></td>
    <td>将提交从一个分支移动到另一个分支</td>
  </tr>
  <tr>
    <td><code>git reset</code></td>
    <td>重设当前 HEAD 到指定状态，可选修改工作区和暂存区</td>
  </tr>
  <tr>
    <td><code>git revert</code></td>
    <td>通过创建一个新的提交来撤销之前的提交</td>
  </tr>
  <tr>
    <td><code>git mv</code></td>
    <td>移动或重命名一个文件、目录或符号链接，并自动更新索引</td>
  </tr>
  <tr>
    <td><code>git rm</code></td>
    <td>从工作区和索引中删除文件</td>
  </tr>
</table>
```

每个指令都有其特定的用途和场景，详细的使用方法和参数可以通过命令行的帮助文档（`git command -h`,例如 `git pull -h`）来获取更多信息。

### 5. Git使用流程

#### 5.1 先注册一个github账号

本次学习项目的链接： <https://github.com/InternLM/Tutorial/tree/camp4>

#### 5.2 fork项目

> 注意取消勾选仅克隆当前分支

#### 5.3配置git并克隆项目到InternStudio本地

```bash
# 修改为自己fork的仓库，改为上图中你的https仓库的git地址,将random-zhou改为自己的用户名
git clone https://github.com/random-zhou/Tutorial.git 
#git clone git@github.com:random-zhou/Tutorial.git 
#git clone https://github.com/InternLM/Tutorial.git
cd Tutorial/
git branch -a
git checkout -b class origin/class
```

#### 5.4 创建分支

```bash
git checkout -b class_036 # 自定义一个新的分支
#git checkout -b class_id 分支名字改为你的uid分支名称
```

#### 5.5 创建自己的介绍文件

介绍文件的模板（路径 ./icamp4/id.md）

> 注意，在GitHub中需要再每一行的后面多打几个空格才能换行

```markdown
【大家可以叫我】:InternLM
【坐标】:上海
【专业/职业】:小助手
【兴趣爱好】:乒乓球
【项目技能】:cv、nlp
【组队情况】:未组队，快来一起!
【本课程学习基础】:CV、NLP、LLM
【本期活动目标】:一起学习，快乐暑假，闯关达人!
```

#### 5.6 提交更改分支

```bash
git add .
git commit -m "add git_camp4_036_introduction" # 提交信息记录,这里需要修改为自己的uid
```

#### 5.7 推送分支到远程仓库

```bash
git push origin class_036
#注意，这里要改为你自己的分支名称
#大家提交使用英文，避免同步错误
```

#### 5.8 检查提交内容

> 查看分支是否被推送到远程仓库

1. 点击右上角Compare & pull request
2. 在“Add a title中”输入 "add git_< id >_introduction",将
3. 请按要求填写相关title，方便审核。然后点击“Create pull request”
4. 等待管理员审核合并

## 作业

### 任务1: 破冰活动 自我介绍

### 任务2: 实践项目 构建个人项目

## 小结
