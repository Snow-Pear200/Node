# 目录

- [目录](#目录)
  - [目标](#目标)
  - [1.Github- 了解开源相关的概念](#1github--了解开源相关的概念)
    - [1.1 什么是开源](#11-什么是开源)
    - [1.2 什么是开源许可协议](#12-什么是开源许可协议)
    - [1.3 常见的5种开源许可协议](#13-常见的5种开源许可协议)
    - [1.4 为什么要拥抱开源](#14-为什么要拥抱开源)
    - [1.5 开源项目托管平台](#15-开源项目托管平台)
    - [1.6 什么是Github](#16-什么是github)
  - [2Github -注册账号](#2github--注册账号)
    - [2.1 注册Github账号的流程](#21-注册github账号的流程)
    - [2.2 激活账号](#22-激活账号)
  - [3 Github远程仓库的使用](#3-github远程仓库的使用)
    - [3.1.新建空白远程仓库](#31新建空白远程仓库)
    - [3.3 远程仓库的两种访问方式](#33-远程仓库的两种访问方式)
    - [3.4 基于HTTPS将本地仓库上传到Github(gitee)](#34-基于https将本地仓库上传到githubgitee)
    - [3.4.1 git push](#341-git-push)
    - [3.5 SSH key](#35-ssh-key)
    - [3.6 SSH key](#36-ssh-key)
    - [3.7 配置SSH key](#37-配置ssh-key)
    - [3.8.检测Github的SSH key是否配置成功](#38检测github的ssh-key是否配置成功)
    - [3.9 基于SSH将本地仓库上传到Github(gitee)](#39-基于ssh将本地仓库上传到githubgitee)
  - [4 Git分支-本地分支操作](#4-git分支-本地分支操作)
    - [4.1 分支的概念](#41-分支的概念)
    - [4.2 分支在实际开发中的作用](#42-分支在实际开发中的作用)
    - [4.3 master主分支](#43-master主分支)
    - [4.4 功能分支](#44-功能分支)
    - [4.5 查看分支列表](#45-查看分支列表)
    - [4.6 创建新分支](#46-创建新分支)
    - [4.7 切换分支](#47-切换分支)
    - [4.8 分支的快速创建和切换](#48-分支的快速创建和切换)
    - [4.9 分支合并](#49-分支合并)
    - [4.10 删除分支](#410-删除分支)
    - [4.11 遇到冲突时的分支合并](#411-遇到冲突时的分支合并)
  - [5 Git 分支-远程分支操作](#5-git-分支-远程分支操作)
    - [5.1 将本地分支推送到远程仓库](#51-将本地分支推送到远程仓库)
    - [5.2 查看远程仓库中所有的分支列表](#52-查看远程仓库中所有的分支列表)
    - [5.3 跟踪分支](#53-跟踪分支)
    - [5.4 拉取远程分支的最新的代码](#54-拉取远程分支的最新的代码)
    - [5.5 删除远程分支](#55-删除远程分支)
  - [总结](#总结)

## 目标

能够掌握Git中基本命令的使用
能够使用Github创建和维护远程仓库
能够掌握Git分支的基本使用

## 1.Github- 了解开源相关的概念

### 1.1 什么是开源

| 关键词 | 概念                              | 基本含义                   | 特点                                   |
| :----- | :-------------------------------- | :------------------------- | :------------------------------------- |
| 开源   | 开源即开放源代码Open source code) | 代码是公开的               | 任何人都可以去查看，修改和使用开源代码 |
| 闭源   | 软件的代码是封闭的                | 只有作者能看得到闭源的代码 | 只有作者能修改闭源的代码               |
通俗的理解：开源是指不仅提供程序还提供程序的源代码，闭源是只提供程序，不提供源代码。

### 1.2 什么是开源许可协议

开源并不意味着完全没有限制，为了限制使用者的使用范围和保护作者的权利，每个开源项目都应该遵守开源许可协议（ open Source License ) 。

### 1.3 常见的5种开源许可协议

- BSD ( Berkeley Software Distribution)
- Apache Licence 2.0
- GPL(GNu General Public License)
  具有传染性的一种开源协议，不允许修改后和衍生的代码做为闭源的商业软件发布和销售
  使用GPL的最著名的软件项目是: Linux
- LGPL (GNU Lesser General Public License)
- MIT ( Massachusetts Institute of Technology,MIT)
  是目前限制最少的协议，唯一的条件:在修改后的代码或者发行包中，必须包含原作者的许可信息
  使用MIT的软件项目有: jquery、Node.js

  关于更多开源许可协议的介绍，可以参考博客https://www.runoob.com/w3cnote/open-source-license.html

### 1.4 为什么要拥抱开源

开源的核心思想是“我为人人，人人为我”，人们越来越喜欢开源大致是出于以下3个原因:开源给使用者更多的控制权

- 开源让学习变得容易
- 开源才有真正的安全
- 开源是软件开发领域的大趋势，拥抱开源就像站在了巨人的肩膀上，不用自己重复造轮子，让开发越来越容易。

### 1.5 开源项目托管平台

专门用于免费存放开源项目源代码的网站，叫做==开源项目托管平台==。目前世界上比较出名的开源项目托管平台主要有以下3个:

- Github(全球最牛的开源项目托管平台，没有之一)
- Gitlab(对代码私有性支持较好，因此企业用户较多)
- Gitee(又叫做码云，是国产的开源项目托管平台。访问速度快、纯中文界面、使用友好)

注意:以上3个开源项目托管平台，只能托管以Git管理的项目源代码，因此，它们的名字都以Git开头。

### 1.6 什么是Github

Github是全球最大的开源项目托管平台。因为只支持Git作为唯一的版本控制工具
故名GitHub。

在Github 中，你可以:

- 关注自己喜欢的开源项目，为其点赞打call
- 为自己喜欢的开源项目做贡献（Pull Request)
- 和开源项目的作者讨论Bug和提需求( lssues)
- 把喜欢的项目复制一份作为自己的项目进行修改( Fork)
- 创建属于自己的开源项目
- etc...

## 2Github -注册账号

### 2.1 注册Github账号的流程

1. 访问Github的官网首页https://github.com/
2. 点击“Sign up”按钮跳转到注册页面
3. 填写可用的用户名、邮箱、密码
4. 通过点击箭头的形式，将验证图片摆正
5. 点击“Create account”按钮注册新用户
6. 登录到第三步填写的邮箱中，点击激活链接，完成注册

### 2.2 激活账号

1. 进入你的邮箱
2. 点击GitHub发送的激活连接

## 3 Github远程仓库的使用

### 3.1.新建空白远程仓库

   ![新建空白远程仓库](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113110546.png)
   创建成功
   ![创建成功](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113110623.png)

### 3.3 远程仓库的两种访问方式

Github 上的远程仓库，有两种访问方式，分别是HTTPS和SSH。它们的区别:

- HTTPS:零配置;但是每次访问仓库时，需要重复输入Github的账号和密码才能访问成功
  `https://gitee.com/AuroraManito/note.git`
- SSH:需要进行额外的配置;但是配置成功后，每次访问仓库时，不需重复输入Github 的账号和密码
  `git@gitee.com:AuroraManito/note.git`
==注意:在实际开发中，推荐使用SSH 的方式访问远程仓库。==

### 3.4 基于HTTPS将本地仓库上传到Github(gitee)

![基于HTTPS将本地仓库上传到Github](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113111347.png)

### 3.4.1 git push

`git push`用来把将代码推送到远程仓库

```git
git status -s
git add .
git status -s
git commit -m "新增了index jS"
git push
```

### 3.5 SSH key

- SSH key的作用:实现本地仓库和Github之间免登录的加密数据传输。
- SSH key的好处:免登录身份认证、数据加密传输。
- SSH key由两部分组成，分别是:

1. id_rsa(私钥文件，存放于客户端的电脑中即可)
2. id_rsa.pub(公钥文件，需要配置到Github 中)

### 3.6 SSH key

1. 打开Git Bash
2. 粘贴如下的命令，并将your_email@example.com替换为注册Github账号时填写的邮箱:
 `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
3. 连续敲击3次回车，即可在C:\Users\用户名文件夹\.ssh目录中生成id_rsa和id_rsa.pub两个文件
![生成的密钥](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113124203.png)

### 3.7 配置SSH key

1. 使用记事本打开id_rsa.pub文件，复制里面的文本内容
2. 在浏览器中登录Github，点击头像->Settings -> SSH and GPG Keys -> New SSH key
3. 将id_rsa.pub文件中的内容，粘贴到Key对应的文本框中
4. 在Title文本框中任意填写一个名称，来标识这个Key从何而来

### 3.8.检测Github的SSH key是否配置成功

打开Git Bash，输入如下的命令并回车执行:
`ssh -T git@github.com`
gitee
`ssh -T git@gitee.com`
上述命令执行后
![gitee验证密钥](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113125113.png)
输入yes之后，如果能看到类似于下面的提示消息，证明SSH key已经配置成功了∶
![验证成功](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113125235.png)

### 3.9 基于SSH将本地仓库上传到Github(gitee)

![基于SSH将本地仓库上传到Github](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113125928.png)

## 4 Git分支-本地分支操作

### 4.1 分支的概念

分支就是科幻电影里面的平行宇宙，当你正在电脑前努力学习Git的时候，另个你正在另一个平行宇宙里努力学习SVN。
如果两个平行宇宙互不干扰，那对现在的你也没啥影响。
不过，在某个时间点，两个平行宇宙合并了，结果，你既学会了Git又学会了SVN
![本地分支操作](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113130124.png)

### 4.2 分支在实际开发中的作用

在进行多人协作开发的时候，为了防止互相干扰，提高协同开发的体验，建议每个开发者都基于分支进行项功能的开发，例如:
![分支在实际开发中的作用](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113130230.png)

### 4.3 master主分支

在初始化本地Git仓库的时候，Git默认已经帮我们创建了一个名字叫做master的分支。通常我们把这个master分支叫做主分支。

![master主分支](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113130320.png)

在实际工作中，master主分支的作用是:==用来保存和记录整个项目已完成的功能代码。==
因此，不允许程序员直接在master分支上修改代码，因为这样做的风险太高，容易导致整个项目崩溃。

### 4.4 功能分支

由于程序员不能直接在master分支上进行功能的开发，所以就有了功能分支的概念。
==功能分支==指的是专门用来开发新功能的分支，它是临时从master主分支上分叉出来的，当新功能开发且测试完毕后，最终需要合并到master主分支上，如图所示:
![功能分支](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113130457.png)

### 4.5 查看分支列表

使用如下的命令，可以查看当前Git仓库中所有的分支列表:

`git branch`
运行的结果如下所示：
![查看分支列表](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113130711.png)
注意:分支名字前面的*号表示当前所处的分支。

### 4.6 创建新分支

使用如下的命令，可以基于当前分支，创建一个新的分支，此时，新分支中的代码和当前分支完全一样:
`git branch` 分支名称

图示如下：
![创建新分支](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113130857.png)

### 4.7 切换分支

使用如下的命令，可以切换到指定的分支上进行开发:
`git chechout login`
如图所示：
![切换分支](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113131057.png)
![切换分支-代码](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113131245.png)

### 4.8 分支的快速创建和切换

使用如下的命令，可以创建指定名称的新分支，并立即切换到新分支上:

```git
# -b 表示创建一个新分支
# checkout  表示切换到刚才新建的分支上
git checkout -b 分支名称
```

图示如下：
![分支的快速切换](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113131822.png)
**==注意：在快速创建和切换分支之前要先进入主分支==**

### 4.9 分支合并

功能分支的代码开发测试完毕之后，可以使用如下的命令，将完成后的代码合并到 master主分支上:

```git
# 1.切换到master分支
git checkout master
# 2.在master分支上运行git merge命令，将login分支的代码合并到master分支
git merge login
```

图示如下：
![分支合并](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113132259.png)
合并分支时的注意点:
假设要把C分支的代码合并到A分支,则必须**先切换到A分支上，再运行gitmerge命令**，来合并C分支!

将zpxx分支的代码添加提交，然后合并到master分支
![示例](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113132635.png)

### 4.10 删除分支

当把功能分支的代码合并到master主分支上以后，就可以使用如下的命令，删除对应的功能分支:
`git branch -d 分支名称`
图示如下
![删除分支图示](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113132843.png)
注意：在删除分支zpxx的时候不能在分支zpxx上，需要切换到别的分支上(通常是主分支)
![删除分支代码](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113132952.png)

### 4.11 遇到冲突时的分支合并

如果在两个不同的分支中，对同一个文件进行了不同的修改，Git就没法干净的合并它们。此时，我们需要打开这些包含冲突的文件然后**手动解决冲突**。

```git
#假设:在把reg分支合并到 master 分支期间，代码发生了冲突
git checkout master
git merge reg
#打开包含冲突的文件，手动解决冲突之后，再执行如下的命令
git add .
git commit -m"解决了分支合并冲突的问题"
```

案例-准备工作：

1. 从主分支切换到reg分支
  `git chechout reg`
2. 在reg 分支上修改源代码 （新建Login.html 并在`<body>`标签中编写`<h2>我在reg分支修改了login.html</h2>`)
3. 将reg分支的代码添加到暂存区
  `git add .`
4. 将reg分支的代码添加到git仓库
   `git commit -m "修改了checkout分支的内容"`
5. 切换到master分支
   `git chechout master`
6. 在master 分支上修改源代码 （新建Login.html 并在`<body>`标签中编写`<h2>我在master分支修改了login.html</h2>`)
7. 将master分支的代码添加到暂存区
  `git add .`
8. 将master分支的代码添加到git仓库
   `git commit -m "修改了checkout分支的内容"`

---
案例-合并分支：
9. 切换到主分支
  `git chechout master`
10. 合并分支
  `git merge reg`
![分支冲突](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113134729.png)
11. 手动解决冲突
![分支冲突-1](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113135038.png)
12. 执行`git add .`处理冲突.
13. 执行`git commot -m "解决了冲突问题"`提交代码
![解决分支冲突后提交](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113135303.png)

## 5 Git 分支-远程分支操作

### 5.1 将本地分支推送到远程仓库

如果是第一次将本地分支推送到远程仓库，需要运行如下的命令:

```git
# -u表示把本地分支和远程分支进行关联，只在第一次推送的时候需要带-u参数
git push -u 远程仓库的别名本地分支名称:远程分支名称
#实际案例:
git push -u origin payment: pay
#如果希望远程分支的名称和本地分支名称保持一致，可以对命令进行简化:
git push -u origin payment
```

注意:第一次推送分支需要带-u参数，此后可以直接使用git push推送代码到远程分支。

将reg 分支推送到远程仓库
![将本地分支推送到远程仓库-代码](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113135744.png)
![将本地分支推送到远程仓库-git仓库](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113135800.png)

### 5.2 查看远程仓库中所有的分支列表

通过如下的命令，可以查看远程仓库中，所有的分支列表的信息:
`git remote show 远程仓库名称`
**注意**:默认远程仓库名称都是**origin**
![查看远程仓库中所有的分支列表](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113140140.png)

### 5.3 跟踪分支

跟踪分支指的是:从远程仓库中，把远程分支下载到本地仓库中。需要运行的命令如下:

```git
#从远程仓库中，把对应的远程分支下载到本地仓库，保持本地分支和远程分支名称相同
git checkout 远程分支的名称
#示例:
git checkout pay
#从远程仓库中，把对应的远程分支下载到本地仓库，并把下载的本地分支进行重命名
git checkout -b 本地分支名称远程仓库名称/远程分支名称
#示例:
git checkout -b payment origin/pay
```

### 5.4 拉取远程分支的最新的代码

可以使用如下的命令，把远程分支最新的代码下载到本地对应的分支中:
`git pull`从远程仓库，拉取当前分支最新的代码，保持当前分支的代码和远程分支代码一致。

### 5.5 删除远程分支

可以使用如下的命令，删除远程仓库中指定的分支:

```git
#删除远程仓库中，指定名称的远程分支
git push 远程仓库名称 --delete 远程分支名称
#示例:
git push origin --delete pay
```

成功将远程仓库中的register仓库删除了
![删除远程分支](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113140955.png)

## 总结

>1. 能够掌握Git中基本命令的使用
    - git init
    - git add .
    - git commit -m "提交消息"
    - git status和git status -s
>2. 能够使用Github创建和维护远程仓库
    - 能够配置Github的SSH访问
    -  能够将本地仓库上传到Github
>3. 能够掌握Git分支的基本使用
    - git checkout -b新分支名称
    - git push -u origin新分支名称
    - git checkout分支名称
    - git branch
