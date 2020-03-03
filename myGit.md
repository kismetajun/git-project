## react笔记

## 分布式

- svn(集中式)需要一台中央服务器
- git的区别
- 速度比svn快
- svn中每个文件夹都有一个文件.svn文件，git有一个单独的文件.git文件夹

## git安装

- windows <https://git-scm.com>
- mac 如果安装过xcode自带git， homebrew是mac的包管理器
- mac 效果难看可以安装
- <http://ohmyz.sh/>
- <http://www.iterm2.com/>

注意：安装成功的时候，右键会出现git gui here 和 git bash here

打开git bash here里面出现一行代码，其中，~/Desktop

- ~ 是指当前用户,desktop桌面

## git步骤

（提交）    git add .                     git commit -m "消息"

- 工作区 ----------------> 暂存区/过渡区  --------------------> 历史区/版本库 ------------> 版本id号

（区别）    git diff                      git diff --cached

                 git diff master

## 配置用户（不配置用户不能提交代码）

- git config --list (查看配置项)
- git config --global user.name "XXXXXXX"
- git config --global user.email "XXXXXXXXXXX"

## 初始化git

- 一个项目初始化一次，不能嵌套
- git init 告诉git哪个文件夹被git所管理
  - $ rm -rf .git 如果文件夹一不小心初始化多次了使用
  - $ rm 2.txt (文件名) 删除某个文件

## 删除暂存区

- git rm --cached 文件名

## 添加到暂存区

- git add .或者-A       提交暂存区
  > 如果报错，就初始化一下 git init

## 添加到历史区

- git commit -m "消息"  提交历史区/版本库
- git status 查看git状态
  > 红色是工作区， 绿色是暂存区， 无颜色历史区/版本库
  > 注意：也可以分主干和分支分别的目录
- git log 查看提交日志

- git commit -a -m "消息"  
  > 可以直接把文件从工作区提到历史区
  > 前提条件是，已经按照以前的步骤提交过一次

## 撤销

- git checkout 文件名    从暂存区中将工作区内容覆盖掉
- git reset HEAD 文件名  暂存区返回撤销上一次

## 撤销 - 回滚历史版本

- 返回历史区
  - git reset --hard 版本号  返回上一步或者几步    ！！！！！！！！
  - git reflog 可以打印全部的日志，全部版本
    > 这一步如果返回上一步错了，又想回没有撤销的部分，打印全部日志，然后，git reset --hard 版本号 即可
  - git reset --hard HEAD^

## git的对比（工作区，暂存区/过渡区，历史区/版本库的比较不同）

- git diff           工作区 和 暂存区/过渡区
- git diff --cached  暂存区/过渡区 和 历史区/版本库
- git diff master    工作区 和 历史区/版本库

## 解决冲突

- 遇到冲突时只能手动得解决冲突，留下想要的结果，再次提交即可

## linux 命令

- $ pwd （print working directory）打印当前工作目录
- $ clear 清除当前屏幕内容

- $ rm -rf 文件夹名 删除文件
- $ rm 文件夹名 删除文件
- $ mkdir 文件夹名 创建目录

- ls -al  显示目录下所有的文件
- touch 文件夹名 创建文件
- cat 文件夹名 查看文件
- vi 文件夹名
  - i:插入模式
  - esc  退出编辑模式
  - :q！ 强制退出
  - :wq  保存并退出

- $ cd    文件夹名 更换目录
- $ cd d: 更换d盘
- $ cd ~/Desktop/文件夹名 切换到某个盘
- $ echo 输入文件内容
  > 1. touch 创建一个空文件， echo创建一个有内容得文件
  > 2. echo 一个 > 表示输入 ； 两个表示追加到
    > 例子： $ echo hello >> 1.txt

- $ git log --graph 显示分支的过程
- $ git log --graph --oneline 显示分支过程一行

## 分支

- git branch 查看分支
  > 其中，* 表示当前在哪一条分支上面
- git branch 分支名字           创建分支
  > $ touch 文件夹名            创建文件
  > 注意：即使在当前的分支上面建立文件，依旧不能说明这个文件就是当前分支上的文件
     > 做法：$ git add . + git commit -m "" 再次提交才可以
- git checkout 分支名字         切换分支
  > 可以查看分支里面的所具有的文件

- git branch -D 分支名字        删除分支
  > 注意：删除分支时当前用户不能在当前要删除的分支上
- git checkout -b  分支名字     创建并切换分支
- git status 才是可以分主干和分支分别的目录
- git stash      文件修改时切换分支
  > 注意：分支有更改不能直接切换，可以提交更改或者暂存更改
- git stash pop  把最后一个历史删掉/还原暂存的内容
- git merge  分支名字  合并分支
  > 注意：需要在主支线上合并分支

步骤：

1. 先创建主干(先主文件提交 gitadd,gitcommit)
2. 在主干的基础上添加一个分支
3. 在分支上进行提交
4. 切换到主干合并分支

> 注意： 先建立分支 确保只有当前分支有这个文件 ,主的上面没有

## 本地 --> gitHub

- 先有github账号

## 本地提交

- README.md
- 创建一个 .gitignore 文件
  > .idea
  > node_modules
  > . DS_Store
  > .................
- git不会上传空文件夹添加，因为它认为这样没有意义
- 添加.gitkeep（git的保留文件）在空文件夹内  

步骤：

1. $ touch README.md(参照上面本地提交的方法)
2. git init
3. git status
4. git add . + git commit -m "" (提交)

## 关联远程仓库

- git remote add origin 地址
- git remote -v   查看远程的信息

## 删除关联(远程信息地址)

- git remote rm 名字

## 推送代码

- git push origin master
