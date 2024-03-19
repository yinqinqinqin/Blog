---
title: git
---







参考pro git简体中文版

http://iissnan.com/progit/ 

# 1.git的基本使用方式

## 1.1git 安装

linux

yum -y install git

输入 git --version查看Git是否安装完成以及查看其版本号

windows 

https://git-scm.com/

进入git官网，选择windows版本进行下载

下载完后，点击exe文件执行，根据提示进行安装，

安装完成之后在桌面点击右键出现git bash 即成功



### 1.2 本地建立git标识

git config --global user.name "YOUR NAME"

git config --global user.email "YOUR EMAIL"

该两行命令表示一个标识，

### 1.3初始化git仓库

git init

在哪个目录下执行的，那这个目录就变成git可以管理的目录

### 1.4 添加文件到暂存区

git add [文件名] 

#将文件添加到暂存区

### 1.5  用命令 git commit告诉Git，把文件提交到仓库

git commit -m "注释"   ##给本次提交提供注释

### 1.6 **连接远程仓库**

在github(或其他接受git命令的仓库)

点开github页面，在设置里找到ssh连接，将本地的公钥内容复制到ssh框中，重新输入密码，提示成功即可。

```
git remote add origin https://github.com/xuyujie2020/Hello-World.git
```

使用该命令连接到远程仓库

### 1.7上传代码

git push -u origin master

第一次提交代码需要加上-u

### 1.8克隆代码

使用git clone + [url]   ##url : 路径

github支持git和http两种克隆模式

### 1.9 查看当前分支

git status

可以查看clone下来的代码所属的分支

使用git checkout 可以切换分支

git branch 也可以查看分支

### 1.10 创建分支

git branch + [名字] 创建一个新的分支，不切换分支

git checkout -b 创建一个分支并切换过去

### 1.11 查看代码的修改

每次代码修改会在该目录下形成一个.git文件，修改的内容保存在这

git status 可以查看被修改过的文件

git diff 查看修改的内容

### 1.12 删除分支

git branch -d + [名字]

### 1.13 删除仓库

在github网页中，进入仓库，在设置中的最下面选择delete，输入要删除的仓库的路径即可



问题解决

visual studio 上传代码出现错误

使用git add .时出现

error: open("贪吃蛇/.vs/贪吃蛇/v17/Browse.VC.opendb"): Permission denied
error: unable to index file '贪吃蛇/.vs/贪吃蛇/v17/Browse.VC.opendb'
fatal: adding files failed

解决方法

touch .gitignore    

在文件中添加 .vs/保存即可

##忽略.vs/文件





##### git 基本命令

```
git init                                                  # 初始化本地git仓库（创建新仓库）
git config --global user.name "xxx"                       # 配置用户名
git config --global user.email "xxx@xxx.com"              # 配置邮件
git config --global color.ui true                         # git status等命令自动着色
git config --global color.status auto
git config --global color.diff auto
git config --global color.branch auto
git config --global color.interactive auto
git config --global --unset http.proxy                    # remove  proxy configuration on git
git clone git+ssh://git@192.168.53.168/VT.git             # clone远程仓库
git status                                                # 查看当前版本状态（是否修改）
git add xyz                                               # 添加xyz文件至index
git add .                                                 # 增加当前子目录下所有更改过的文件至index
git commit -m 'xxx'                                       # 提交
git commit --amend -m 'xxx'                               # 合并上一次提交（用于反复修改）
git commit -am 'xxx'                                      # 将add和commit合为一步
git rm xxx                                                # 删除index中的文件
git rm -r *                                               # 递归删除
git log                                                   # 显示提交日志
git log -1                                                # 显示1行日志 -n为n行
git log -5
git log --stat                                            # 显示提交日志及相关变动文件
git log -p -m
git show dfb02e6e4f2f7b573337763e5c0013802e392818         # 显示某个提交的详细内容
git show dfb02                                            # 可只用commitid的前几位
git show HEAD                                             # 显示HEAD提交日志
git show HEAD^                                            # 显示HEAD的父（上一个版本）的提交日志 ^^为上两个版本 ^5为上5个版本
git tag                                                   # 显示已存在的tag
git tag -a v2.0 -m 'xxx'                                  # 增加v2.0的tag
git show v2.0                                             # 显示v2.0的日志及详细内容
git log v2.0                                              # 显示v2.0的日志
git diff                                                  # 显示所有未添加至index的变更
git diff --cached                                         # 显示所有已添加index但还未commit的变更
git diff HEAD^                                            # 比较与上一个版本的差异
git diff HEAD -- ./lib                                    # 比较与HEAD版本lib目录的差异
git diff origin/master..master                            # 比较远程分支master上有本地分支master上没有的
git diff origin/master..master --stat                     # 只显示差异的文件，不显示具体内容
git remote add origin git+ssh://git@192.168.53.168/VT.git # 增加远程定义（用于push/pull/fetch）
git branch                                                # 显示本地分支
git branch --contains 50089                               # 显示包含提交50089的分支
git branch -a                                             # 显示所有分支
git branch -r                                             # 显示所有原创分支
git branch --merged                                       # 显示所有已合并到当前分支的分支
git branch --no-merged                                    # 显示所有未合并到当前分支的分支
git branch -m master master_copy                          # 本地分支改名
git checkout -b master_copy                               # 从当前分支创建新分支master_copy并检出
git checkout -b master master_copy                        # 上面的完整版
git checkout features/performance                         # 检出已存在的features/performance分支
git checkout --track hotfixes/BJVEP933                    # 检出远程分支hotfixes/BJVEP933并创建本地跟踪分支
git checkout v2.0                                         # 检出版本v2.0
git checkout -b devel origin/develop                      # 从远程分支develop创建新本地分支devel并检出
git checkout -- README                                    # 检出head版本的README文件（可用于修改错误回退）
git merge origin/master                                   # 合并远程master分支至当前分支
git cherry-pick ff44785404a8e                             # 合并提交ff44785404a8e的修改
git push origin master                                    # 将当前分支push到远程master分支
git push origin :hotfixes/BJVEP933                        # 删除远程仓库的hotfixes/BJVEP933分支
git push --tags                                           # 把所有tag推送到远程仓库
git fetch                                                 # 获取所有远程分支（不更新本地分支，另需merge）
git fetch --prune                                         # 获取所有原创分支并清除服务器上已删掉的分支
git pull origin master                                    # 获取远程分支master并merge到当前分支
git mv README README2                                     # 重命名文件README为README2
git reset --hard HEAD                                     # 将当前版本重置为HEAD（通常用于merge失败回退）
git rebase
git branch -d hotfixes/BJVEP933                           # 删除分支hotfixes/BJVEP933（本分支修改已合并到其他分支）
git branch -D hotfixes/BJVEP933                           # 强制删除分支hotfixes/BJVEP933
git ls-files                                              # 列出git index包含的文件
git show-branch                                           # 图示当前分支历史
git show-branch --all                                     # 图示所有分支历史
git whatchanged                                           # 显示提交历史对应的文件修改
git revert dfb02e6e4f2f7b573337763e5c0013802e392818       # 撤销提交dfb02e6e4f2f7b573337763e5c0013802e392818
git ls-tree HEAD                                          # 内部命令：显示某个git对象
git rev-parse v2.0                                        # 内部命令：显示某个ref对于的SHA1 HASH
git reflog                                                # 显示所有提交，包括孤立节点
git show HEAD@{5}
git show master@{yesterday}                               # 显示master分支昨天的状态
git log --pretty=format:'%h %s' --graph                   # 图示提交日志
git show HEAD~3
git show -s --pretty=raw 2be7fcb476
git stash                                                 # 暂存当前修改，将所有至为HEAD状态
git stash list                                            # 查看所有暂存
git stash show -p stash@{0}                               # 参考第一次暂存
git stash apply stash@{0}                                 # 应用第一次暂存
git grep "delete from"                                    # 文件中搜索文本“delete from”
git grep -e '#define' --and -e SORT_DIRENT
git gc
git fsck
```



##### 冲突合并

```
git branch 分支 # 创建分支
git branch -v # 查看分支版本
git bachch hot-fix # 创建hot-fix分支
git checkout hot-fix # 切换分支

git merge hot-fix # 将hot-fix分支合并到当前分支上 

冲突合并

两个分支在同一个文件的同一个位置 有两套完全不一样的内容 git无法决定

此时我们在不同的分支上都提交了本地库 然后切换到Master分支 开始进行合并

git merge hot-fix

然后我们会得到如下报错信息

Auto-merging hello.c

CONFICT(content): Merge conflict in hello.c

Automatic merge failed; fix conflicts and then commit the result.

同时右边的分支状态会显示为 master | MERGING

再执行

git status

就会告诉我们

both modified: hello.c

在这个文件里面

会使用 

<<<<<<HEAD

======

#

>>>>>> hot-fix 进行分隔

git status
git add hello.c

当我们执行这条语句后

git commit -m "merge test" hello.c

fatal: cannot do a partial commit during a merge

在合并过程中不能只进行部分的修改

git commit -m "merge test"

底层都是看得指针 主要是HEAD指针

head(指针) 指向分支指针 

master(指针) 指向具体版本
```













