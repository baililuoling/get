[git下载](http://git-scm.com/downloads)

```
安装完成后，需要配置个人用户信息和电子邮箱地址，在命令行输入：
$ git config --global user.name "guan"

$ git config --global user.email "guan@163.com"

git config --list					可以查看配置.

git init						初始化一个仓库

git add 文件路径					添加一个文件

git add .						添加全部文件

git rm 文件路径 --cache					从暂存区删除文件

git commit -m "本次提交的简要说明信息"			提交一个文件

git commit -a -m "提交的信息"				上面两行的合并操作(不推荐)

git diff						对比与add.文件变化

git reset --hard Head					回退到最近的一次提交的代码

git reset --hard Head^					回退到上一次提交的代码(每多一个"^"表示多一个上)

git reset --hard HEAD~100				回退到上一百次提交的代码

git reset --hard 提交的版本号				回退到指定的版本(根据每次提交的版本的号)

git reflog						查看每一次的提交的版本号

git log							命令显示从最近到最远的提交日志

git commit -m "本次提交的简要说明信息" --amend		撤销上一次提交，并讲暂存区文件重新提交

git checkout -- 文件路径				拉取暂存区文件 并将其替换成工作区文件

git reset HEAD  -- 文件路径				拉取最近一次提交到版本库的文件到暂存区，改操作不影响工作区

git status						查看仓库状态

git branch 分支名					创建分支

git branch						列出所有分支，在列出所以分支中，当前分支前会有个*号

git checkout 分支名					切换分支

git checkout -b 分支名					创建和切换分支合并写法

git checkout master					切换到主分支

git merge 分支名					把指定分支名的分支合并到当前分支(后面可以贴标签)

git branch -d 分支名					清除之前临时使用的分支

git remote add origin(别名) 远程仓库地址		给远程仓库地址取一个别名

git push -u origin master				把本地代码提交到远程仓库

git clone origin master					将整个工程复制下来，不需要本地是仓库

git pull origin master					把工程更新到本地库

git branch -a						查看所有分支路径

git clone：从远程服务器克隆一个一模一样的版本库到本地,复制的是整个版本库.（clone是将一个库复制到你的本地，是一个本地从无到有的过程）

git pull：从远程服务器获取到一个branch分支的更新到本地，并更新本地库.（pull是指同步一个在你本地有版本的库内容更新的部分到你的本地库）
```

忽略文件
* 新建 .gitignore文件
* 在这个文件里写一些想要被git忽略的文件或者文件夹
* 可以通过命令git status查看仓库状态

冲突解决方法：
* 当两个人同时修改一个文件，并提交后，合并这两个分支回发生冲突
* Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容
* 我们可以手动修改冲突文件，再次提交，即可解决冲突
* $ git add .
* $ git commit -m "conflict fixed"
* [master cf810e4] conflict fixed