#Git学习笔记
##添加最小配置命令  
###设置用户名
    git config [--local|--global|--system] user.name 'Your name'
###清除用户
    git config --unset --[local|global|system] user.name 
###设置Email
    git config [--local|--global|--system] user.email 'Your email'
###清除Email 同上
###查看配置
      git config --list [--local|--global|--system]
      区别  
      git config --list --local :区域为本地仓库  只能在仓库里面起作用，普通路径git不管理. 在 .git/config 文件里面。
      git config --list --global:为当前用户的所有仓库。在个人home目录下的 .gitconfig文件里面。
      git config --list --system:本系统的所有用户。在git安装目录下。    
##创建Git仓库
###1.把已有的项目代码纳入git仓库
      cd 项目代码所在的文件夹
      git init 
###2.新建的项目直接用Git管理
      cd 某个文件夹
      git init you_project 会在当前路径下创建和项目名称同名的文件夹
      cd you_project
##往仓库里面添加文件
###区分 工作目录 暂存区 版本历史
####git add 命令将在工作目录的文件添加到暂存区,被git跟踪，有如下几种
       1. git add . ： 将文件的修改，文件的新建，添加到暂存区。
       2. git add -u ：将文件的修改，文件的删除，添加到暂存区域。
       3. git add -A 相当于 git add -all 到了2.21.0.win.1 版本  git add . 和 git add -A 一样：
                   将文件的修改，文件的删除，文件的新增，添加到暂存区。
####git commit 命令将在暂存区文件添加到版本历史中。
       git commit -m'message'
##给文件重命名的简单命令
       git mv filename othername
       (git reset --hard 清除暂存区，此命令比较危险，注意使用)
##git log 命令看版本历史
       1.git log --all 查看所有分支的历史
       2.git log --all --graph 查看图形化的log地址
       3.git log --oneline 查看单行的简洁历史
       4.git log --oneline -n4 查看最近4条简洁历史
       5.git log --oneline -n4 --graph 查看所有分支最近4条单行的图形化历史
       6.git help --web log 跳转到git log的帮助文档网页
       7.gitk 跳转 图形化面板工具
##探索 .git 目录
       cat命令主要用来查看文件内容 创建文件，文件合并，追加文件内容等功能。
       cat HEAD 查看HEAD 文件内容
       git cat-file 显示版本库对象的内容  类型 大小信息
       git cat-file -t xxxxxxxxx 显示版本库对象类型
       git cat-file -p xxxxxxxxx 显示版本库对象内容
       git cat-file -s xxxxxxxxx 显示版本库对象大小
       
       HEAD：指向当前的工作分支路径
       config：存放本地库（local）相关的配置信息
       refs/heads:存在分支
       refs/tags:存放tag，又叫里程碑（当这次commit是具有里程碑意义的 比如项目1.0的时候 就可以打tag）
       objects：存放对象 .git/object/文件夹中的子文件夹都是以哈希值前两位字符命名，每个object由40位字符组成，前两位给文件夹当名称，后38位做文件名。
##认识 commit tree blob  以及它们之间的关系
       1.commit对象，每次执行commit命令 都会生成一个commit对象，commit对象是当前时间所有文件夹和文件的快照。
       commit 包含 tree 、parent、author、committer
       2.tree对象 可以理解问一个文件夹
       3.blob对象可以理解为文件夹中的文件

       当commit过多时候 objects 会无限扩大
       但是 git会对内容相同的文件只会存一个blob，blob和文件名一点关系没有，多数为变更的blob都是相同的，所以只会存一个blob，这样可以节省很多空间。




