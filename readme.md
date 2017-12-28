Git入门指南
===========

## 创建仓库 create repository
创建一个空文件夹，shell或cmd进入该文件夹，输入`git init`，以初始化仓库

## 添加文件
将文件保存到仓库文件夹中，<br>
`git status`查看状态，<br>
通过`git add {文件名}`添加文件，例如`git add readme.txt`，<br>
此时，再查看`git status`，状态发生变化。<br>
add操作是将`工作区`中的文件添加到`暂存区`中，<br>
可以add多次，存在`暂存区`中，然后一并`commit`到仓库中


## 提交操作
`git commit -m "{description}"`，例如`git commit -m "add readme.md"`

## 修改文件
文档编辑器修改文件（不建议windows自带的文本编辑器），<br>
修改后，`git diff`查看变化，<br>
`git add readme.md`添加文件，<br>
`git commit -m "add readme.md"`

## 查看版本信息
git每次`commit`创建一个快照，这也就是为什么可以回退到以前版本的原因。<br>
可通过`git log`查看版本信息，<br>
亦可通过`git log --pretty=oneline`来显示简要信息

## 版本回退：
每次commit会生成快照，并且每个快照有唯一的id（最前面一串很长的数字）<br>
通过`git reset --hard HEAD^`回退到上一个版本，<br>
`git reset --hard HEAD^^`回退到前2个版本，或者`git reset --hard HEAD~2`，数字表示更清晰

若想从旧版本再回退到新版本，可通过id实现。<br>
首先，通过`git reflog`查看每次操作的命令的记录，找到id号，<br>
然后通过`git reset --hard {id}`，用具体的id号代替`{id}`

## 撤销更改
### 1)撤销工作区的更改
`git checkout -- readme.md`
### 2)撤销暂存区的更改(需要2步)
第一步：撤销更改到工作区`git reset HEAD readme.md`;<br>
第二步：撤销工作区中的更改 `git checkout -- readme.md`;<br>

如果已经commit，则通过版本回退。但如果提交到远程仓库，就麻烦了。

## 删除文件
首先，选中文件删除，或者命令行`rm test.txt`删除文件<br>
删除之后，可通过`git status`查看到变化，<br>
若确定提交删除，`git commit -m "remove test.txt"`，<br>
若删错了，可通过`git checkout -- test.txt`回退（注意：此时恢复的版本库中的版本，没有提交的更改会丢失）

## 添加远程仓库
1、首先在github网站new一个新repository，名字与本地建的仓库名一致<br>
2、添加远程仓库：git remote add origin https://github.com/wuchunxu/learngit.git ，此时本地仓库与远程仓库关联起来<br>
3、推送内容到远程仓库<br>
首次推送内容：`git push -u origin master`，<br>
以后再推送用：`git push origin master`即可。

