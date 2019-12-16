# hello-world

一个例子

## markdownLint的规则

记录一下markdown的规则 [简书上的一篇博客markdown黄线警告中文版|简书](<https://www.jianshu.com/p/51523a1c6fe1>)

## Git提交记录

+ `git init`
  
>初始化

+ `git add .`

>添加所有的文件（后面是一个英文的句号）
>也可以不用句号，用具体的文件名

+ `git commit "这里写下你自己的记录本次提交内容的信息"`

>执行提交(后面加双引号内是备注)

+ `git push git@github.com:自己的名称/仓库名.git`

我自己的自然就是
git push git@github.com:Yu-Fool/hello-world.git

>执行推送

***每次增加了新文件就先 add，然后 commit，如果只是改了文件的内容，只执行commit就行了，最后一步都是要执行 push 。***

## 删除commit记录

因为有的时候刚上传代码，里面会包含一些个人的、服务器之类的信息，
这些在后期更改后在commit历史记录上任然可见，所以想要删除这些记录。

__如果仅仅想删除历史记录，不对当前代码造成更改。用下面这个：__

好像原理就是创建新分支后删除原来的分支，然后把新的分支改个名字，新的分支就没有commit的记录了

1. git checkout --orphan latest_branch
    >尝试运行
2. git add -A
    >添加所有文件
3. git commit -am "commit message"
    >提交更改
4. git branch -D master
    >删除分支
5. git branch -m master
    >将当前分支重命名
6. git push -f origin master
    >最后，强制更新存储库。

__如果是想删除commit提交记录并且将对应commit造成的更改也删除，即变回了未执行对应的commit之前的状态。__

转载的网址 --> [Git 删除具体某个提交commit的方法 | CSDN](<https://blog.csdn.net/Nathan1987_/article/details/81605531>)

下面是流程：

1. git log
    >在本地获取相关Repository的commit记录，按向下键就可以查看更多了
2. git rebase -i (commit-id)
    >commit-id 就是提交的hash值,</br>
    像这样的一串 **8b994d86d8d7f1d0caf547cc0ff964ccea80ae1e**</br>
    这里的commit-id是要删除的commit的之前的一个commit号,</br>
    就是说，你点回车之后显示的可以让你操作的历史记录，它是从你这个commit-id开始到最新的记录，但是不包含你输入的这个commit-id对应的记录
3. 编辑文件，将要删除的commit前面的pick单词改为drop，然后按照提示保存退出
    >此处是Linux的vi操作
4. git log 查看一下是否删除
5. git push origin HEAD --force
   >推送到远程仓库，就OK了
