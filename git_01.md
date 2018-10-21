## GIT

### 1.什么是GIT
    Git是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目.
    个人理解就是可以管理个时间段文件的版本管理工具(原来提交过的内容,虽然修改了但是通过git这个工具可以将之前的内容重现而且管理).

### 2.GIT工作流程
    1.克隆 Git 资源作为工作目录.
    2.在克隆的资源上添加或修改文件.
    3.如果其他人修改了，你可以更新资源.
    4.在提交前查看修改.
    5.提交修改.
    6.在修改完成后，如果发现错误，可以撤回提交并再次修改并提交.

##### git工作流程
![Alt text](/images/git-Workflow.png "GIT工作流程")

### 3.GIT工作区、暂存区和版本库.
    1.工作区:类似电脑目录.
    2.暂存区:index/stage,一般存放在".git目录"下的index文件(.git/index)中,所以把暂存区有时候也叫作索引(index).
    3.版本库:工作区有一个隐藏目录.git,这个不算工作区,而是git的版本库.

##### 它们之间的关系
![Alt text](/images/git-relationship.png "工作区，暂存区，版本库三者的关系")

### 4.Git基本操作
    1.git init:在目录中创建新的仓库
    2.git clone:拷贝一个仓库在本地-->get clone[url]
    3.git add:可将文件添加到缓存/命令添加当前项目的所有文件.
    4.git status:以查在上次提交之后是否有修改/查看项目当前状态.
    5.git diff:来查看执行git status的结果的详细信息。
        git diff命令显示写入缓存与以修改但未写入缓存的改动的区别.git diff 有俩个主要的场景.
        1>尚未缓存的改动:git diff.
        2>查看已缓存的改动:git diff --cached.
        3>查看已缓存的与未缓存的所有改动:git diff HEAD.
        4>显示摘要而非整个:git diff --stat.
    6.git commit:将缓存区内容添加到仓库中.
    7.git reset HEAD:用于取消已缓存的内容.
    8.git rm:删除文件.
        要从git中移除某一个文件:git rm <file>.
        删除之前修改过并且放到暂存区的话,必须使用强制删除:git rm -f<file>.
        想把文件从暂存区删除,但又想保存在工作目录,也就是从跟踪清单中删除:git rm --cached<file>.
        递归删除:git rm -r *    (如果后面跟的是一个目录作为参数，则会递归删除整个目录中的所有子目录和文件).
    9.git mv:用于移动或重命名一个文件、目录、软连接（符号链接）.
    10.git log:查看提交历史.
    
**"AM":表示这个文件在添加缓存后又有改动.改动后再执行git add命令将其添加到缓存中.**


### 5.Git分支管理:
    1.创建分支命令:git branch(branchname).
    2.切换分支命令:git checkout(branchname).
    3.合并分支命令:git merge.
    4.列出分支命令:git branch.
    5.创建新分支并立即执行切换到该分支下:git checkout -b(branchname).
    6.删除分支命令:git branch -d(branchname).
    7.合并分支命令:git merge.
**当你切换分支的时候,git会用该分支的最后的快照替换你的工作目录的内容，所以多个分支不需要多个目录.**

### 6.Git标签：
    命令:git tag -a.
    个人感觉这是一个类似于项目版本的标签，比如iPhone2、iPhone2S.
    命令可以不使用-a也照样实行,不过不会记录这个标签的时间,也不会让你添加个标签的注解.
    执行命令git log --decorate就可以看到我们的标签.
    标签可追加在发布提交的后面跟一个园括号(tag:版本号).
    指定标签信息命令:git tag -a <tagname> -m "标签".
    PGP签名标签命令:git tag -s <tagname> -m "标签".

### 7.Git 远程仓库(Github)
    1.添加远程仓库:git remote add [shortname][url].
    2.查看当前远程仓库:git remote.
    3.从远程仓库下载新分支与数据:git fetch.
        该命令执行完成之后需要git merge远程分支到你所在的分支.
    4.从远端仓库提取数据并尝试合并到当前分支:git merge.
        该命令就是执行git fach之后紧接着执行git merge远程分支到你所在的任意分支.
    5.提取更新的数据:
        1.首先执行git fetch[alias]告诉git去获取它有你没有的数据.
        2.然后执行git merge[alias]/[branch]以将服务器上的任何更新合并到你的当前分支.
    6.推送到远程仓库:git push [alias][[branch].
    7.删除远程仓库:git remote rm [别名].
    
