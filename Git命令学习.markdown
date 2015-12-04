# Git命令学习

标签（空格分隔）：命令

---
##背景##
git是一种分布式版本控制系统，和其他集中式版本控制系统相比，具有以下特点：

 - 直接处理快照，而非差异比较
 - 近乎所有操作都是在本地执行
 - git保证完整性
 - git一般只添加数据

参考[PRO-GIT中文版][1]
 
----
## 相关概念 ##
git有三种区域
git directory:git存储元数据和对象数据库
working directory:工作区域，存储物理文件
staging area:映像区域，存储需要提交的修改信息


git文件有三种状态
commited:数据被保存在本地git数据库中
modified:修改了本地物理数据
staged:将修改的行为标记为可提交状态

所有的git命令都是针对这三种区域的数据进行操作

基本的git工作流程如下：
![此处输入图片的描述][2]

 1. 用户modified在working directory
 2. 用户将修改的信息提交到staging area中
 3. 用户将staging area的信息以快照(snapshot)的形式存储在git directory中

---
##命令##

###仓库(repository)命令###
仓库初始化
git init
仓库克隆
git clone    

###分支(branch)命令###
显示所有存在的分支
git branch
创建一个新的分支
git branch &lt;branch-name&gt;
切换分支
git checkout &lt;branch-name&gt;
创建并切换分支
git checkout -b &lt;branch-name&gt;
将分支与当前分支合并
git merge &lt;branch-name&gt;
删除一个分支
git branch -d &lt;branch-name&gt;
强制删除一个分支
git branch -D &lt;branch-name&gt;

###提交(commit)命令###
将文件修改提交到暂存区(stage)
git add &lt;file-name&gt;
将文件修改提交到当前分支的提交记录中(commit)
git commit -m message
显示当前分支的提交记录
git log
显示当前git directory和staging area；working directory和staging area的不同
git status
将对应文件在git directory中的内容恢复到staging area中；或者将对应的commit恢复到staging area中或者working directory中；
git reset &lt;file-name&gt;&lt;commit&gt;
将对应的文件或者commit或者branch中的内容恢复到working directory中
git checkout &lt;file-name&gt;&lt;commit&gt;&lt;branch&gt;
将文件从working directory和staging area中删除
git rm &lt;file-name&gt;

###远程(remote)命令###
git remote
git push 
git pull
git fetch


git remote add origin
git push -u origin master


git pull server-name/remote-branch:local-branch
git fetch server-name/remote-branch
git branch --set-upstream local-branch
git push server-name/local-branch:remote-branch


 


  [1]: https://git-scm.com/book/zh/v2/
  [2]: https://git-scm.com/book/en/v2/book/01-introduction/images/areas.png