git 常用指令
=====
安装git
----
- git config --global user.name 'your name'
- git config --global user.email 'email@example.com'

创建git仓库
----
- mkdir XX 创建空目录
- cd XX 切换目录
- pwd 显示当前目录
- git init 初始化仓库

文件添加版本
---
- git add XX 添加XXX到暂存区
- git commit -m 'XXX' 暂存区提交到仓库，版本为XXX
- git status 查看仓库状态
- git diff 查看修改的具体内容
- git log 查看版本日志
- git log --pretty=oneline 日志简介显示一行
 
版本回退
---
- git reset --hard commit_id（版本号） 回退到哪个版本
- HEAD 表示当前版本
- HEAD^ 表示上一个版本
- HEAD^^ 上上个版本
- HEAD~100 上100个版本
- git reflog 查看命令历史，确定要回到未来哪个版本
- git checkout --file 丢弃工作修改
- 如果改了工作区，又添加到暂存区，先丢弃修改（两步） <br>
        1、git reset HEAD file <br>
        2、git checkout --file
        
删除文件
----
- rm file 删除文件
- git rm 删除文件

远程仓库
----
- git remote add origin [url]
- git push -u origin master 关联后第一次推送master分支所有内容

如何修改远程仓库地址：（三种方法）
---
(1)修改命令<br>
     git remote set-url origin [url]  <br>
(2)先删后加<br>
git remote rm origin <br>
git remote add origin [url]  <br>
(3)直接修改config文件

#####PS：Git支持多种协议，默认git：//使用ssh。使用https速度慢，最大的麻烦是每次推送必须输入口令，只开放http端口公司，无法使用ssh只能使用https

分支管理
----
- git branch 查看分支
- git branch name 创建分支
- git checkout name 切换分支
- git checkout -b name 创建并切换分支
- git merge name 合并某分支到当前分支
- git branch -d name 删除分支
- git log --graph 查看分支合并图
- git merge --no-ff -m 'XXX' 普通模式合并，合并后的历史有分支，能看出曾做过的合并，而fast forward合并看不出做过合并

修复bug
---
- git stash 暂存工作区
- git stash list 暂存工作区列表
- git stash apply 回复工作区 ，但是stash内容不删，需要用git stash drop删除
- git stash pop 回复工作区的同时 stash内容删除
- git branch -D name 丢掉一个未被合并的分支

多人协作
----
- git push origin branch-name
- git pull 提示no tracking information 说明本地分支和远程分支的链接没有创建<br>
   使用git branch --set -upstream branch-name origin/branch-name
   
标签
-----
- git tag name 创建一个标签，默认HEAD可以指定commit_id
- git tag -a name -m 'XXX' 指定标签信息
- git tag -s name -m 'XXX' 用PGP签名标签
- git tag 查看所有标签
- git push origin tagname 推送本地标签
- git push origin --tags 推送全部未推送标签
- git tag -d tagname 删除本地标签
- git push origin :ref/tags/tagnanme 删除远程标签

#####ps：忽略某些文件时，需要编写.gitignore

