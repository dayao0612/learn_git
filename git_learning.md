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



