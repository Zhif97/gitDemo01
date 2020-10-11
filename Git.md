## 全局配置：

- 用户名：git config --global user.name "用户名"
- 用户邮箱：git config --global user.email "邮箱"
- 查看全局配置：git config --global --list

## 初始化以及操作

- 初始化 git 仓库：git init
- 查看仓库当前的状态：git status
- 添加进入暂存区：git add 文件名
- 添加进入归档区：git commit -m "版本说明"
- 查看工作区和版本库里面最新版本的区别：git diff HEAD -- 文件名
- 撤销修改内容：git checkout -- 文件名/ git restore -- 文件名
- 撤销暂存区内容：git reset HEAD 文件名

## 版本穿梭

- 回退到上一个版本：git reset --hard HEAD^
- 回滚到指定版本(将归档区-暂存区-工作区进行回滚)：git reset --hard commitId
- 回滚到指定版本(将归档区-暂存区进行回滚)：git reset --mixed commitId
- 回滚到指定版本(将归档区进行回滚)：git reset --soft commitId
- 将某个版本删除：git revert commitId

## 版本信息

- 查看当前每个版本：git log 或者 git log --pretty=oneline（只查看每个版本 id 以及说明）
- 查看历史版本：git reflog

## 项目分支

- 查看当前分支：git branch -v
- 创建并切换到该分支：git checkout -b a1
- 切换已存在分支：git switch master
- 将某分支合并到 master 分支：git merge a1

`遇到多分支开发：先合并 a1 到 master 后再合并 a2 到 master,如果遇到冲突，先回滚到前一个版本，再切换 a2 分支。 然后将 master 合并到 a2 进行修正`

## 上传到 GitHub/gitee

- 删除远程关联库名：git remote rm origin
- 指定 GitHub 仓库：git remote add origin 仓库地址
- 初次关联远程仓库：git push -u origin master
- 更新远程仓库：git push origin master

## 同步更新到 GitHub/gitee

- 关联 GitHub 的远程库：git remote add github 仓库地址
- 关联码云的远程库：git remote add gitee 仓库地址

### 配置方式同步

- 修改.git 文件夹内的 config 文件：
<!-- [remote "github"]
url = git@github.com:chloneda/demo.git
	fetch = +refs/heads/*:refs/remotes/github/*
[remote "gitee"]
url = git@gitee.com:chloneda/demo.git
	fetch = +refs/heads/*:refs/remotes/gitee/* -->

## 远程库信息

- 查看远程库信息：git remote -v

## 提交到 GitHub/gitee

-- GitHub：git push github master
-- Gitee：git push gitee master

## 更新代码

- 从 github 拉取更新：git pull github
- 从 gitee 拉取更新：git pull gitee
