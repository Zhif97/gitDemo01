## git 本地仓库命令

### 全局配置：

- 用户名：git config --global user.name "用户名"
- 用户邮箱：git config --global user.email "邮箱"
- 查看全局配置：git config --global --list

### 获取 SSH 公钥

- 执行生成公钥和私钥的命令：ssh-keygen -t rsa

```
参数 -t rsa 表示使用rsa算法进行加密，执行后，
会在/home/当前用户/.ssh目录下找到id_rsa(私钥)和id_rsa.pub(公钥)
并按回车3下（为什么按三下，是因为有提示你是否需要设置密码，
如果设置了每次使用Git都会用到密码，一般都是直接不写为空，直接回车就好了）。
会在一个文件夹里面生成一个私钥 id_rsa和一个公钥id_rsa.pub。
（可执行start ~ 命令，生成的公私钥在 .ssh的文件夹里面）
```

- 执行查看公钥的命令：cat ~/.ssh/id_rsa.pub

### 初始化以及操作

- 初始化 git 仓库：git init
- 查看仓库当前的状态：git status
- 添加进入暂存区：git add 文件名
- 添加进入归档区：git commit -m "版本说明"
- 撤销修改内容：git checkout -- 文件名/ git restore -- 文件名
- 撤销暂存区内容：git reset HEAD 文件名

### 比较版本差异

- 查看工作区和版本库里面最新版本的区别：git diff HEAD -- 文件名
- 比较的是暂存区和工作区的差异 : git diff
- 比较的是暂存区和历史区的差异 : git diff --cached
- 比较的是历史区和工作区的差异（修改）: git diff master

### 版本穿梭

- 回退到上一个版本：git reset --hard HEAD^
- 回滚到指定版本(将归档区-暂存区-工作区进行回滚)：git reset --hard commitId
- 回滚到指定版本(将归档区-暂存区进行回滚)：git reset --mixed commitId
- 回滚到指定版本(将归档区进行回滚)：git reset --soft commitId
- 将某个版本删除：git revert commitId

### 版本信息

- 查看当前每个版本：git log 或者 git log --pretty=oneline（只查看每个版本 id 以及说明）
- 查看历史版本：git reflog

### 分支管理

- 创建分支 : git branch 分支名
- 切换分支 : git switch/checkout 分支名
- 创建分支并切换分支 : git checkout -b 分支名
- 删除分支 : git branch -d 分支名
- 合并分支 : git merge 分支名(将该分支合并到当前分支)
- 分支的合并后显示 : log:git log --oneline --graph --decorate
- 查看当前分支：git branch -v

```
遇到多分支开发：先合并 a1 到 master 后再合并 a2 到 master;
如果遇到冲突，先回滚到前一个版本，再切换 a2 分支。
然后将 master 合并到 a2 进行修正
```

## 同步到 GitHub/gitee 远程仓库

- 删除远程关联库名：git remote rm 远程仓库名
- 指定 GitHub 仓库：git remote add origin 仓库地址
- 初次关联远程仓库：git push -u origin master
- 更新远程仓库：git push origin master

```
拒绝合并无关的历史:
首先将远程仓库和本地仓库关联起来:git branch --set-upstream-to=origin/远程分支名  你的分支名
整合远程仓库和本地仓库:git pull --allow-unrelated-histories    (忽略版本不同造成的影响)
重新更新、提交即可。
```

### 远程库信息

- 查看远程库信息：git remote -v

### 向 GitHub/gitee 拉取

- 拉取更新：git pull origin master
- 更新远程代码到本地仓库：git fetch origin master

## 同时推送项目至 GitHub/gitee

### 删除远程关联库名

- git remote rm 远程仓库名

### 关联远程库

- 关联 GitHub 的远程库：git remote add github 仓库地址
- 关联码云的远程库：git remote add gitee 仓库地址

### 提交到 GitHub/gitee

-- GitHub：git push github master
-- Gitee：git push gitee master

### 向 GitHub/gitee 拉取

- 从 github 拉取更新：git pull github master
- 从 gitee 拉取更新：git pull gitee master
