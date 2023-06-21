# 目录

- [目录](#目录)
  - [目标](#目标)
  - [1.起步-关于版本控制](#1起步-关于版本控制)
    - [1.1 文件的版本](#11-文件的版本)
    - [1.2 版本控制软件](#12-版本控制软件)
      - [1.2.1 概念](#121-概念)
      - [1.2.2 通俗的理解](#122-通俗的理解)
    - [1.3、使用版本控制软件的好处](#13使用版本控制软件的好处)
    - [1.4、版本控制系统的分类](#14版本控制系统的分类)
      - [1.4.1 本地版本控制系统](#141-本地版本控制系统)
      - [1.4.2 集中化的版本控制系统](#142-集中化的版本控制系统)
      - [1.4.3分布式版本控制系统](#143分布式版本控制系统)
    - [1.5.起步-GIt基础概念](#15起步-git基础概念)
      - [1.5.1 什么是Git](#151-什么是git)
      - [1.5.2 Git的特性](#152-git的特性)
        - [1.5.2.1 SVN的差异比较](#1521-svn的差异比较)
        - [1.5.2.2 Git的记录快照](#1522-git的记录快照)
        - [1.5.2.3 近乎所有操作都是本地执行](#1523-近乎所有操作都是本地执行)
      - [1.5.3 Git中的三个区域](#153-git中的三个区域)
      - [1.5.4 Git中的三种状态](#154-git中的三种状态)
      - [1.5.5 基本的GIt工作流程](#155-基本的git工作流程)
  - [2.GIt基础-安装并配置Git](#2git基础-安装并配置git)
    - [2.1 在windows中下载Git](#21-在windows中下载git)
    - [2.2.配置用户信息](#22配置用户信息)
    - [2.3 git的全局配置文件](#23-git的全局配置文件)
    - [2.4 检查配置信息](#24-检查配置信息)
    - [2.5.获取帮助信息](#25获取帮助信息)
  - [3 Git基础-Git的基本操作](#3-git基础-git的基本操作)
    - [3.1.获取GIt仓库的两种方式](#31获取git仓库的两种方式)
    - [3.2.在现有目录中初始化仓库](#32在现有目录中初始化仓库)
    - [3.3 工作区中文件的四种状态](#33-工作区中文件的四种状态)
    - [3.4 检查文件状态](#34-检查文件状态)
    - [3.5 以精简方式显示文件状态](#35-以精简方式显示文件状态)
    - [3.6 跟踪新文件](#36-跟踪新文件)
    - [3.7 提交更新](#37-提交更新)
    - [3.8 对已提交的文件进行修改](#38-对已提交的文件进行修改)
    - [3.9 暂存已修改的文件](#39-暂存已修改的文件)
    - [3.10 提交已暂存的文件](#310-提交已暂存的文件)
    - [3.11 撤销对文件的修改](#311-撤销对文件的修改)
    - [3.12 向暂存区中一次性添加多个文件](#312-向暂存区中一次性添加多个文件)
    - [3.13 取消暂存的文件](#313-取消暂存的文件)
    - [3.14 跳过使用暂存区域](#314-跳过使用暂存区域)
    - [3.15 移除文件](#315-移除文件)
    - [3.16.忽略文件](#316忽略文件)
    - [3.17 glob模式](#317-glob模式)
    - [3.18 `.gitignore`文件的例子](#318-gitignore文件的例子)
    - [3.19 查看项目的提交历史](#319-查看项目的提交历史)
    - [3.20.回退到指定版本](#320回退到指定版本)
    - [3.21 小结](#321-小结)
    - [3.22 git常见错误](#322-git常见错误)
      - [3.22.1 git提交时拒绝访问](#3221-git提交时拒绝访问)

## 目标

- 能够掌握Git基本命令的使用
- 能够使用Github创建和维护远程仓库
- 能够掌握Git分支的基本使用

## 1.起步-关于版本控制

### 1.1 文件的版本

> - 操作麻烦：每次都需要复制→粘贴→重命名
> - 命名不规范:无法通过文件名知道具体做了哪些修改
> - 容易丢失:如果硬盘故障或不小心删除，文件很容易丢失
> - 协作困难:需要手动合并每个人对项目文件的修改，合并时极易出错

![文件的版本](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113094059.png)

### 1.2 版本控制软件

#### 1.2.1 概念

> 版本控制软件是一个用来记录文件变化，以便将来查阅特定版本修订情况的系统，因此有时也叫做“版本控制系统”。

#### 1.2.2 通俗的理解

> 把手工管理文件版本的方式，改为由软件管理文件的版本;这个负责管理文件版本的软件，叫做“版本控制软件”。

### 1.3、使用版本控制软件的好处

> 操作简便：只需识记几组简单的终端命令，即可快速上手常见的版本控制软件。
> 易于对比：基于版本控制软件提供的功能，能够方便地比较文件的变化细节，从而查找出导致问题的原因。
> 易于回溯：可以将选定的文件回溯到之前的状态，甚至将整个项目都回退到过去某个时间点的状态。
> 不易丢失:在版本控制软件中，被用户误删除的文件，可以轻松的恢复回来。
> 协作方便:基于版本控制软件提供的分支功能，可以轻松实现多人协作开发时的代码合并操作。

### 1.4、版本控制系统的分类

本地版本控制系统：
> 单机运行，使维护文件版本的操作工具化

集中化的版本控制系统：
> 联网运行，支持多人协作开发;性能差、用户体验不好

分布式版本控制系统：
> 联网运行，支持多人协作开发;性能优秀、用户体验好

#### 1.4.1 本地版本控制系统

![本地版本控制系统](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113094728.png)
特点:
> 使用软件来记录文件的不同版本，提高了工作效率，降低了手动维护版本的出错率

 缺点:

> 1. 单机运行，不支持多人协作开发
> 2. 版本数据库故障后，所有历史更新记录会丢失

#### 1.4.2 集中化的版本控制系统

典型代表：SVN

![集中化的版本控制系统](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113094929.png)

特点:==基于服务器、客户端==的运行模式

- 服务器保存文件的所有更新记录
- 客户端==只保留最新的文件版本==

优点:联网运行，支持多人协作开发

缺点:

- 不支持离线提交版本更新
- 中心服务器崩溃后，所有人无法正常工作
- 版本数据库故障后，所有历史更新记录会丢失

#### 1.4.3分布式版本控制系统

典型代表：git

![分布式版本控制系统](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113095240.png)

特点:基于服务器、客户端的运行模式

- 服务器保存文件的所有更新版本
- 客户端是服务器的完整备份，并不是只保留文件的最新版本

优点:

- 联网运行，支持多人协作开发
- 客户端断网后支持离线本地提交版本更新
- 服务器故障或损坏后，可使用任何一个客户端的备份进行恢复

### 1.5.起步-GIt基础概念

#### 1.5.1 什么是Git

Git是一个开源的分布式版本控制系统，是目前世界上最先进、最流行的版本控制系统。可以快速高效地处理从很小到非常大的项目版本管理。

特点:项目越大越复杂，协同开发者越多，越能体现出Git的高性能和高可用性!

#### 1.5.2 Git的特性

Git 之所以快速和高效，主要依赖于它的如下两个特性:

- 直接记录快照，而非差异比较
- 近乎所有操作都是本地执行

##### 1.5.2.1 SVN的差异比较

传统的版本控制系统（例如SVN）是基于差异的版本控制，它们存储的是一组基本文件和每个文件随时间==逐步累积的差异==。
![SVN的差异比较](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113095633.png)
好处:节省磁盘空间缺点:耗时、效率低
在每次切换版本的时候，都需要在基本文件的基础上，应用每个差异，从而生成目标版本对应的文件。

##### 1.5.2.2 Git的记录快照

Git快照是在原有文件版本的基础上重新生成一份新的文件，类似于备份。为了效率，如果文件没有修改，Git不再重新存储该文件，而是只保留一个链接指向之前存储的文件。
![Git的记录快照](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113095753.png)

缺点:占用磁盘空间较大
优点:==版本切换时非常快==，因为每个版本都是完整的文件快照，切换版本时直接恢复目标版本的快照即可。

##### 1.5.2.3 近乎所有操作都是本地执行

在Git中的绝大多数操作都只需要访问本地文件和资源，一般不需要来自网络上其它计算机的信息。

![近乎所有操作都是本地执行](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113095845.png)

特性:

- 断网后依旧可以在本地对项目进行版本管理
- 联网后，把本地修改的记录同步到云端服务器即可

#### 1.5.3 Git中的三个区域

使用Git管理的项目，拥有三个区域，分别是工作区、暂存区、Git仓库。

![工作区](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113100036.png)
工作区
处理工作的区域

![暂存区](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113100117.png)
暂存区
已完成的工作的临时存放区域,
等待被提交

![Git仓库](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113100150.png)
Git仓库
最终的存放区域

#### 1.5.4 Git中的三种状态

| 已修改                                       | 已暂存                                                         | 已提交                                  |
| :------------------------------------------- | :------------------------------------------------------------- | :-------------------------------------- |
| 表示修改了文件，但还没将修改的结果放到暂存区 | 表示对已修改文件的当前版本做了标记，使之包含在下次提交的列表中 | 表示文件已经安全地保存在本地的Git仓库中 |

注意:

- 工作区的文件被修改了，但还没有放到暂存区，就是已修改状态。
- 如果文件已修改并放入暂存区，就属于已暂存状态。
- 如果Git仓库中保存着特定版本的文件，就属于已提交状态。

#### 1.5.5 基本的GIt工作流程

基本的Git工作流程如下:

1. 在工作区中修改文件
2. 将你想要下次提交的更改进行暂存
3. 提交更新，找到暂存区的文件，将快照永久性存储到Git仓库

![基本的GIt工作流程](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113100726.png)

## 2.GIt基础-安装并配置Git

### 2.1 在windows中下载Git

在开始使用Git管理项目的版本之前，需要将它安装到计算机上。可以使用浏览器访问如下的网址，根据自己的操作系统，选择下载对应的Git安装包:
https://git-scm.com/downloads

### 2.2.配置用户信息

安装完Git之后，要做的第一件事就是设置自己的用户名和邮件地址。因为通过Git对项目进行版本管理的时候，Git需要使用这些基本信息，来记录是谁对项目进行了操作:

![配置用户信息](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113100931.png)

注意:如果使用了--global选项，那么该命令只需要运行一次，即可永久生效

```Git
git config --global user.name "auroramanito"
git config --global user.email "xxxxx@qq.com"
```

### 2.3 git的全局配置文件

通过`git config --global user.name`和 `git config --global user.email`配置的用户名和邮箱地址，会被写到`C:/Users/用户名文件夹/.gitconfig`文件中。这个文件是Git的==全局配置文件，配置一次即可永久生效==。

### 2.4 检查配置信息

除了使用记事本查看全局的配置信息之外，还可以运行如下的终端命令，快速的查看Git的全局配置信息:

```git
#查看所有的全局配置项
git config --list --global
```

![检查配置信息](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113101300.png)

```git
#查看指定的全局配置项
git config user.name
git config user.email
```

![查看指定的全局配置项](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113101339.png)

### 2.5.获取帮助信息

可以使用`git help <verb>`命令，无需联网即可在浏览器中打开帮助手册，例如:

![获取帮助信息命令](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113101426.png)

![获取帮助信息命令-效果图](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113101455.png)

如果不想查看完整的手册，那么可以用-h选项获得更简明的“help”输出:

```git
#想要获取git config 命令的快速参考
git config -h
```

## 3 Git基础-Git的基本操作

### 3.1.获取GIt仓库的两种方式

> - 将尚未进行版本控制的本地目录转换为Git仓库
> - 从其它服务器克隆一个已存在的Git仓库

以上两种方式都能够在自己的电脑上得到一个可用的Git 仓库

### 3.2.在现有目录中初始化仓库

如果自己有一个尚未进行版本控制的项目目录，想要用Git来控制它，需要执行如下两个步骤:

> 1. 在项目目录中，通过鼠标右键打开“Git Bash"
> 2. 执行git init命令将当前的目录转化为Git仓库

![在现有目录中初始化仓库](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113101743.png)

git init命令会创建一个名为.qit的隐藏目录，==这个.git目录就是当前项目的Git仓库==，里面包含了初始的必要文件，这些文件是Git仓库的必要组成部分。

![git init](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113101820.png)

### 3.3 工作区中文件的四种状态

工作区中的每一个文件可能有4种状态，这四种状态共分为两大类，如图所示:

- 未跟踪（Untracked):不被Git所管理的文件。
- 未修改(Unmodified)：工作区中文件的内容和Git仓库中文件的内容保持一致。
- 已修改(Modified)：工作区中文件的内容和Git仓库中文件的内容不一致。
- 已暂存(Staged)：工作区中被修改的文件已被放到暂存区，准备将修改后的文件保存到Git仓库中。

![工作区中文件的四种状态](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113101918.png)

Git 操作的终极结果:让工作区中的文件都处于“未修改”的状态。

### 3.4 检查文件状态

可以使用git status 命令查看文件处于什么状态，例如

![检查文件状态](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102000.png)

在状态报告中可以看到新建的testgit.docx文件出现在Untracked files(未跟踪的文件）下面。
未跟踪的文件意味着Git 在之前的快照（提交）中没有这些文件;Git不会自动将之纳入跟踪范围，除非明确地告诉它“我需要使用Git跟踪管理该文件”。

### 3.5 以精简方式显示文件状态

使用git status 输出的状态报告很详细，但有些繁琐。如果希望以精简的方式显示文件的状态，可以使用如下两条完全等价的命令，其中-s是--short的简写形式:

```git
#以精简的方式显示文件状态
git status -s
git status --short
```

![以精简方式显示文件状态](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102100.png)

### 3.6 跟踪新文件

使用命令 git add开始跟踪一个文件。所以，要跟踪testgit.docx文件，运行如下的命令即可:
`git add testgit.docx`

1. 此时再运行git status命令，会看到testgit.docx文件在Changes to be committed这行的下面，说明已被跟踪，并处于暂存状态:
2. 以精简的方式显示文件的状态:新添加到暂存区中的文件前面有绿色的A标记

![跟踪新文件](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102227.png)

### 3.7 提交更新

现在暂存区中有一个testgit.docxtestgit.docx文件等待被提交到Git 仓库中进行保存。可以执行git commit命令进行提交，其中-m选项后面是本次的提交消息，用来对提交的内容做进一步的描述:

```git
git commit -m "新建了testgit.docx文件"
```

提交成功后会显示如下的信息：
![提交更新](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102333.png)

`clear`命令可以清空命令行

提交成功之后，再次检查文件的状态，得到提示如下:

![提交更新-再次检查](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102424.png)

证明工作区中所有的文件都处于“未修改”的状态，没有任何文件需要被提交。

![提交更新-流程](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102453.png)

### 3.8 对已提交的文件进行修改

目前，testgit.docx文件已经被Git跟踪，并且工作区和Git仓库中的testgit.docxl文件内容保持一致。当我们修改了工作区中testgit.docx的内容之后，再次运行git status和 git status -s命令，会看到如下的内容:

![对已提交的文件进行修改](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102535.png)

文件testgit.docx出现在Changes not staged for commit这行下面，说明==已跟踪文件的内容发生了变化==，但还没有放到暂存区。
注意:修改过的、没有放入暂存区的文件前面有红色的M标记。

### 3.9 暂存已修改的文件

目前，工作区中的 index.html文件已被修改，如果要暂存这次修改，需要再次运行git add 命令，
这个命令是个多功能的命令，主要有如下3个功效:

- 可以用它开始跟踪新文件
- 把已跟踪的、且已修改的文件放到暂存区
- 把有冲突的文件标记为已解决状态。

![暂存已修改的文件](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102657.png)

### 3.10 提交已暂存的文件

再次运行`git commit -m` "提交消息"命令，即可将暂存区中记录的index.html的快照，提交到Git仓库中进行保存:

![提交已暂存的文件](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102738.png)
运行`git status`查看文件状态
![提交已暂存的文件-文件状态](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102754.png)

### 3.11 撤销对文件的修改

撤销对文件的修改指的是:把对工作区中对应文件的修改，还原成Git仓库中所保存的版本。操作的结果:所有的修改会丢失，且无法恢复!危险性比较高，请慎重操作!
![撤销对文件的修改](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113102920.png)
撤销操作的本质:用Git仓库中保存的文件，覆盖工作区中指定的文件。

### 3.12 向暂存区中一次性添加多个文件

如果需要被暂存的文件个数比较多，可以使用如下的命令，一次性将所有的新增和修改过的文件加入暂存区:
`git add .`
![向暂存区中一次性添加多个文件](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103007.png)

### 3.13 取消暂存的文件

`git reset HEAD 要移除的名称`

![取消暂存的文件](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103046.png)

全部移除

`git reset HEAD .`

### 3.14 跳过使用暂存区域

Git 标准的工作流程是工作区→暂存区→Git仓库，但有时候这么做略显繁琐，此时可以跳过暂存区，直接将工作区中的修改提交到Git仓库，这时候Git工作的流程简化为了工作区→Git仓库。
Git提供了一个跳过使用暂存区域的方式，只要在提交的时候，给git commit加上-a选项，Git就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过git add步骤:

`git commit -a -m "消息"`

![跳过使用暂存区域](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103150.png)

### 3.15 移除文件

从Git仓库中移除文件的方式有两种:

- 从Git 仓库和工作区中同时移除对应的文件
- 只从Git仓库中移除指定的文件，但保留工作区中对应的文件

```git
#从Git仓库和工作区中同时移除index.js 文件
git rm -f index.js
#只从Git仓库中移除index.css，但保留工作区中的 index.css文件
git rm --cached index.css
```

移除文件-当前文件目录
![移除文件-当前文件目录](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103302.png)
移除文件-同时删除文件
![移除文件-同时删除文件](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103342.png)
移除文件-保留工作区文件
![移除文件-保留工作区文件](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103417.png)

### 3.16.忽略文件

一般我们总会有些文件无需纳入Git的管理，也不希望它们总出现在未跟踪文件列表。在这种情况下，我们可以创建一个名为`.gitignore`的配置文件，列出要忽略的文件的匹配模式。

- 以#开头的是注释
- 以/结尾的是目录
- 以/开头防止递归
- 以!开头表示取反
- 可以使用glob模式进行文件和文件夹的匹配(glob指简化了的正则表达式）
  
### 3.17 glob模式

所谓的glob模式是指简化了的正则表达式:

- 星号*匹配零个或多个任意字符
- [abc]匹配任何一个列在方括号中的字符（此案例匹配一个a或匹配一个b或匹配一个c)
- 问号?只匹配一个任意字符
- 在方括号中使用短划线分隔两个字符，表示所有在这两个字符范围内的都可以匹配（比如[0-9]表示匹配
所有0到9的数字)
- 两个星号**表示匹配任意中间目录（比如a/**/z可以匹配 a/z、 a/b/z或 a/b/c/z等)

### 3.18 `.gitignore`文件的例子

![gitignore文件的例子](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103710.png)

![gitignore文件的例子-上传示例](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103752.png)

### 3.19 查看项目的提交历史

如果希望回顾项目的提交历史，可以使用git log这个简单且有效的命令。

![查看项目的提交历史](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103831.png)

### 3.20.回退到指定版本

![回退到指定版本](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103901.png)

回退到指定版本-查看项目的提交历史
![回退到指定版本-查看项目的提交历史](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113103917.png)

回退到指定版本-回退到新建了gittest文档版本
==切换为“新建了gittest文档”版本 当返回旧版本之后，git log --pretty=online就无法展示全部历史版本信息==

![回退到指定版本-回退到新建了gittest文档版本](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113104050.png)

使用git reflog --pretty=online 查看完整记录，切换到最新版本。

![回退到指定版本-查看完整记录](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113104234.png)

### 3.21 小结

1. 初始化Git仓库的命令
`git init`
2. 查看文件状态的命令
`git status` 或 `git status -s`
3. 一次性将文件加入暂存区的命令
`git add .`
4.将暂存区的文件提交到Git仓库的命令
`git ciammit -m "提交消息"`

### 3.22 git常见错误

#### 3.22.1 git提交时拒绝访问

remote: [session-cd4e539a] Access denied
fatal: unable to access 'https://gitee.com/AuroraManito/note.git/': The requested URL returned error: 403

>解决方法
可能原因是之前缓存的账号和密码与当前的不一致，要删除系统里缓存的git凭证！
一行指令搞定：
`git config --global --unset credential.helper`