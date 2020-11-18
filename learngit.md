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

# 如果git pull冲突，则先fix冲突，然后add commit即可；如果没有冲突，则可以fast-forward.
# git pull = git fetch + git merge

git fetch origin master:tmp # 取回远程主分支，并在本地建立名为tmp的本地分支
git diff tmp    # 查看二者不同
git merge tmp   # 将tmp分支合并到当前分支
git branch -d tmp  # 删除tmp分支
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
