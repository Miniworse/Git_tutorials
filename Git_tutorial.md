# Git 版本控制教程

_30/JUN/2025_  

_ref: [如何使用GitHub进行版本控制与项目协作](https://zhuanlan.zhihu.com/p/685785542);
[人人都能学会的git教程，版本控制、分支管理、开源协作一次讲清楚](https://www.bilibili.com/video/BV1B3fQYYEzY)_

## 基础配置

1. 安装git
2. 配置用户Git信息

```git
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱地址"
```

可以通过`--list`命令查看用户信息, 键盘输入`q`退出list。

```
git config --list
```

3. 在本地项目文件目录下创建仓库，这样文件中就会生成一个`.git`的隐藏文件。

```
git init
```

4. 将本地仓库与GitHub上的远程仓库进行关联：

```
git remote add origin 远程服务地址
```

其中，“远程仓库地址”是你在GitHub上创建仓库时得到的HTTPS或SSH地址。  
这样就实现了建立本地git仓库并与远程仓库建立了连接。

## 提交代码到GitHub

1. 将项目文件夹中的所有文件添加到Git的暂存区：

```
git add .
```

如果需要只提交某个特定文件则将“.”改为相应的文件名，例如：

```
git add Git_tutorial.md
```

2. 提交代码并添加提交信息，这个信息必须要有,不然命令行会要求你输入。

   
```
git commit -m "提交信息"
```

3. 将本地仓库的代码推送到GitHub上的远程仓库

```
git push -u origin master
```

推送到远程仓库后就可以看到在github上存储了这次提交的代码。分支要从main(default)切换到master，master是一个版本指针，这也就是为什么github下载的代码文件夹有时会出现“*****-master”的原因。

## 更多命令

首先要明确几个不同的工作状态，简单来说：  
工作区：所有修改发生在工作区，工作区的改动未被 Git 跟踪，需手动添加到暂存区；  
暂存区：一个中间过渡区域，临时存放你准备提交的改动；  
版本库：Git 的永久存储区域，保存所有提交的历史记录。  

>工作区 -(git add)-> 暂存区 -(git commit)-> 版本库


```
git add #修改从工作区放到暂存区
git restore #撤销工作区修改
```

```
git commit #暂存区到版本库
git restore --staged 文件名 #撤销暂存区状态，修改返回工作区
```

每次 `git commit` 会生成一个带唯一哈希的版本,也可以用标签来表示每个在版本库中的版本

```
git tag v1.0
git tag -a v1.0 -m "message" #标签添加注释
git tag -d v1.0 #撕掉标签
```

`status`可以观察当前修改所处的状态
```
git status
```

以下命令可以查看历次提交记录，在后面添加`--pretty=oneline`可以让显示更加简洁。
```
git log
```

调取之前的档案，则采用`reset`命令，有三种工作方式包括`--hard``--soft``--mixed`，也可以用哈希值或者标签指定。

```
git reset --hard HEAD^ #调取前一份档案
git reset --hard HEAD^^ #调取两次之前的档案
git reset --hard HEAD~20 #调取20次之前的档案
```

`reflog`记录了所有的调动记录：

```
git reflog
```
