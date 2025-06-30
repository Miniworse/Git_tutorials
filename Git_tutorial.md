# Git 版本控制教程

_30/JUN/2025_  
_ref: [知乎](https://zhuanlan.zhihu.com/p/685785542) _

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

3. 在本地项目创建仓库

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

1. 将项目中的所有文件添加到Git的暂存区：

```
git add .
```

2. 提交代码并添加提交信息

   
```
git commit -m "提交信息"
```

3. 将将本地仓库的代码推送到GitHub上的远程仓库

```
git push -u origin master
```