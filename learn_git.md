# Git学习笔记

工作区->暂存区->版本库

## 本地修改的接受和丢弃

```bash
# 丢弃工作区的修改，即让该文件回退到最近一次git commit或git add时的状态
git checkout -- file_name      

# 撤销暂存区的修改，将其重新放回到工作区
git reset HEAD file_name    

# 以上两条命令联用，就可以实现撤销暂存区的修改，回退到版本库的版本。

# 处理工作区非delete的修改
git add file_name   

# 处理工作区delete的修改
git rm file_name   
# 文件误删后可以使用 git checkout -- file_name回退到最近一次暂存区或版本库的内容，进行恢复
```

## gitignore

```bash
git rm --cached readme.txt   # 删除readme.txt的跟踪，并保留在本地
git rm -f readme.txt         # 删除readme.txt的跟踪，并删除本地文件
```

如果在建立gitignore之前已经push项目，则新建的gitignore不会起作用。此时解决办法是将
本地缓存删除（改变为untrack状态），然后再提交。

```bash
git rm -r --cached .        # 最后的.是删除当前目录下所有文件的track状态
git add .
git commit -m "update .gitignore"

```

## 分支的创建与合并

```bash
# 创建新的分支，并切换。
git checkout -b branch_name 

# 相当于以下两条命令：
git branch branch_name
git checkout branch_name

# 在本地创建远程dev分支的本地dev分支
git checkout -b dev origin/dev    

# 查看当前分支
git branch     

# 将other_branch上的工作合并到当前分支上
git merge other_branch   

# fast-forward：快进模式合并，即直接把当前分支指向other_branch上的当前提交。
# 这种模式下，删除分支后，在log上会损失分支合并信息

# 不以fast-forward模式合并。这种方式会保留分支合并信息。
git merge --no-ff -m "merge with no-ff" dev    

# 合并分支后可以删除对应的分支：
git branch -d other_branch

# 以直观形式查看git log
git log --graph --pretty=oneline --abbrev-commit 
```

## 远程分支合并

```bash
# 如果git pull冲突，则先fix冲突，然后add commit即可；如果没有冲突，则可以fast-forward.
# git pull = git fetch + git merge

git fetch origin master:tmp # 取回远程主分支，并在本地建立名为tmp的本地分支
git diff tmp    # 查看二者不同
git merge tmp   # 将tmp分支合并到当前分支
git branch -d tmp  # 删除tmp分支

# 直接方法
git push # 首先用git push看有没有冲突 如果本地进行了修改，远程也进行了修改，则会产生冲突
git pull # 拉取远程仓库
# 这一步需要注意：如果远程仓库的修改与本地的内容冲突，则会显示远程仓库与本地仓库冲突的部分。如果远程仓库比本地添加了一些文件，则会直接加入。如果本地仓库的内容比远程仓库的内容多了某一部分，则不会显示。总结：只会显示由于远程仓库与本地仓库的交集中，与本地仓库冲突的部分；至于交集以外的文件变动，则会直接合并，并等待stage。
# 若git pull之后存在冲突，则在修改完冲突后，需要git add之后commit提交；而如果不存在冲突，直接合并，则系统会自动产生一个merge的commit信息，之后只需要直接git push即可。
git add
git push
```

## 版本回退

```bash
# 回退到上一版本:
git reset --hard HEAD^     
# 此时git log，则之前的版本号已经没有了。如果在同一窗口可以找到，可以使用下面语句，这样可以回到之前的版本
git reset --hard 版本号      

# 若不记得之前的版本号，可以使用下面语句，查看每一次操作时的版本号
git reflog 
```

## git查看远程仓库

```bash
git remote -v
```
