[TOC]

## Git操作

git可以分为工作区、暂存区、本地仓库、远程仓库

+ 工作区
+ 暂存区
+ 版本库
+ 远程仓库：建立在远程服务器上的版本库。



基本使用

```powershell
#初始化仓库
git init
#查看仓库状态
git status
#查看提交日志
git log
#查看git配置
git config --list
```

在当前目录初始化一个版本库

```powershell
git init
```

提交工作区变化到暂存区

```powershell
git add .
#提交工作区所有变化到暂存区
git add -u
#提交工作区更改过的文件到暂存区
```

执行提交（将暂存区的文件提交到版本库），就是存到本地仓库的版本库

```powershell
git commit -m "提交说明"
```

执行推送（将本地仓库推送到远程仓库）

```powershell
git push git@github.com:Yu-Fool/hello-world.git
```

执行拉取（将远程仓库拉取到本地仓库）

```powershell
git pull [shortname] [分支]
```

> origin 是 git clone 的默认 shortname



#### 删除历史提交记录

##### git语法解决一（不更改记录造成的代码更改）

新建分支，复制数据至新分支，删除原有分支

```powershell
#尝试运行
git checkout --orphan latest_branch
#添加所有文件
git add -A
#提交更改
git commit -m "..."
#删除分支
git branch -D master
#将当前分支重命名
git branch -m master
#最后，强制更新存储库
git push -f origin master
```



##### git语法解决二（返回记录之前的代码）

转载的网址 --> [Git 删除具体某个提交commit的方法 | CSDN](<https://blog.csdn.net/Nathan1987_/article/details/81605531>)

下面是流程：

```powershell
#zai
git log
#
git rebase -i (commit-id)
```



1. git log
   
    >在本地获取相关Repository的commit记录，按向下键就可以查看更多了
2. git rebase -i (commit-id)
    >commit-id 就是提交的hash值,</br>
    >像这样的一串 **8b994d86d8d7f1d0caf547cc0ff964ccea80ae1e**</br>
    >这里的commit-id是要删除的commit的之前的一个commit号,</br>
    >就是说，你点回车之后显示的可以让你操作的历史记录，它是从你这个commit-id开始到最新的记录，但是不包含你输入的这个commit-id对应的记录
3. 编辑文件，将要删除的commit前面的pick单词改为drop，然后按照提示保存退出
   
    >此处是Linux的vi操作
4. git log 查看一下是否删除
5. git push origin HEAD --force
   
   >推送到远程仓库，就OK了