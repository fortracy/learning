# Git命令


标签（空格分隔）：命令

-----
##背景##
git是一种分布式版本控制系统，和其他集中式版本控制系统相比，具有以下特点：

 - 直接处理快照，而非差异比较
 - 近乎所有操作都是在本地执行
 - git保证完整性
 - git一般只添加数据

参考[PRO-GIT中文版][1]
 
------
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

 1. 仓库初始化
git init
 2. 仓库克隆
git clone    

###分支(branch)命令###

 1. 显示所有存在的分支
git branch
 2. 创建一个新的分支
git branch &lt;branch-name&gt;
 3. 切换分支 
git checkout &lt;branch-name&gt;
    创建并切换分支，可使用该命令在远程分支的基础上创建一个本地新分支，并将两个分支创建关联 如git checkout -b
    &lt;branch-name&gt; &lt;remote branch-name&gt; 
 4. 将分支与当前分支合并 
 git merge &lt;branch-name&gt; 
 5. 删除一个分支
git branch -d &lt;branch-name&gt; 
 6. 强制删除一个分支 
git branch -D &lt;branch-name&gt; 
 7. 将远程分支与本地分支进行**分支跟踪**，那么当在使用remote命令时就不用专门指定远程分支
git branch --set-upstream-to=origin/&lt;branch&gt;
    &lt;local-branch&gt;
> 从远程分支 checkout 出来的本地分支，称为 跟踪分支 (tracking branch)。跟踪分支是一种和某个远程分支有直接联系的本地分支。在跟踪分支里输入 git push，Git 会自行推断应该向哪个服务器的哪个分支推送数据。同样，在这些分支里运行 git pull 会获取所有远程索引，并把它们的数据都合并到本地分支中来。
在克隆仓库时，Git 通常会自动创建一个名为 master 的分支来跟踪 origin/master。这正是 git push 和 git pull 一开始就能正常工作的原因。当然，你可以随心所欲地设定为其它跟踪分支，比如 origin 上除了 master 之外的其它分支。

###提交(commit)命令###

 1. 将文件修改提交到暂存区(stage)
git add &lt;file-name&gt;
 2. 将文件修改提交到当前分支的提交记录中(commit)
git commit -m message
 3. 显示当前分支的提交记录
git log
 4. 显示当前git directory和staging area；working directory和staging area的不同
git status
 5. 将对应文件在git directory中的内容恢复到staging area中；或者将对应的commit恢复到staging area中或者working directory中；
git reset &lt;file-name&gt;&lt;commit&gt;
 6. 将对应的文件或者commit或者branch中的内容恢复到working directory中
git checkout &lt;file-name&gt;&lt;commit&gt;&lt;branch&gt;
 7. 将文件从working directory和staging area中删除
git rm &lt;file-name&gt;

###远程(remote)命令###

 1. git remote 
 2. 将远程分支与当前分支合并
git push &lt;remote&gt;&lt;branch&gt;
 3. 拉下远程分支数据，并将远程分支与当前分支进行合并
git pull &lt;remote&gt;&lt;branch&gt;
 4. 下载远程分支数据，将远程分支数据保存在本地，但是无法进行编辑；如果需要使用远程分支的数据，可以在远程分支的基础上创建一个本地分支，或者将远程分支合并入本地分支
git fetch &lt;remote&gt;&lt;branch&gt;


----

##和CVS的对比##

> 这和大多数版本控制系统形成了鲜明对比，它们管理分支大多采取备份所有项目文件到特定目录的方式，所以根据项目文件数量和大小不同，可能花费的时间也会有相当大的差别，快则几秒，慢则数分钟。而 Git 的实现与项目复杂度无关，它永远可以在几毫秒的时间内完成分支的创建和切换。同时，因为每次提交时都记录了祖先信息（译注：即 parent 对象），将来要合并分支时，寻找恰当的合并基础（译注：即共同祖先）的工作其实已经自然而然地摆在那里了，所以实现起来非常容易。Git 鼓励开发者频繁使用分支，正是因为有着这些特性作保障。 

----

> 值得一提的是 Git 可以自己裁决哪个共同祖先才是最佳合并基础；这和 CVS 或 Subversion（1.5 以后的版本）不同，它们需要开发者手工指定合并基础。所以此特性让 Git 的合并操作比其他系统都要简单不少。




 


  [1]: https://git-scm.com/book/zh/v2/
  [2]: https://git-scm.com/book/en/v2/book/01-introduction/images/areas.png