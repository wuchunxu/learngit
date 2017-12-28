Git is a distributed version control system.
Git is free software distributed under the GPL.
This is wuchunxu's first repository created by git.

## 创建仓库
创建一个空文件夹，并进入，输入`git init`，初始化仓库

## 添加文件
将文件保存到仓库文件夹内，`git status`可以查看状态，通过命令`git add {文件名}`添加文件，例如`git add readme.txt`，此时，再查看`git status`，状态发生变化。
添加文件可以进行多次操作。
不再添加时，可以提交

## 提交操作
`git commit -m "{description}"`

## 修改文件
文档编辑修改文件后，可以`git diff`查看变化，`git add readme.txt`添加文件，`git commit -m "new description"`

## 查看版本信息
git每次commit都会创建一个快照，可以通过如下命令查看提交的信息：
`git log`
或者
`git log --pretty=oneline`来显示简要信息

## 版本回退：
### 原理：每次commit都会生成新的id，通过id可以实现版本的切换。
### 命令：`git reset --hard HEAD^`回退到上一个版本，`git reset --hard HEAD~2`回退到前2个版本

如果想从旧版本再回退到新版本，只要找到相应的id号即可，通过`git reflog`查看每次操作的命令记录，然后`git reset --hard {id}`
那么，每个id代表什么版本呢？这就要看自己的注释了，也就是git commit -m "modify description"中的modify description，每次提交的时候都会有个备注。

## 撤销更改
### 撤销工作区的更改
`git checkout -- readme.txt`
### 撤销暂存区的更改
第一步：撤销更改到工作区`git reset HEAD readme.txt`;
第二步：撤销工作区中的更改 `git checkout -- readme.txt`;

如果commit更改了，则通过版本回退
但如果提交到远程仓库，就...

