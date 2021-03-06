常用GIT命令

## 查看status,add之后，不想commit，希望撤回add之前的操作，但要保留修改（包括 新加文件、删除文件、已有文件修改等）
``` git reset -q```

注意不可使用 git reset --hard，本地文件会被替换，后悔莫及

## git commit之后，想撤销commit
```git reset --soft HEAD^```

--soft 不删除工作空间改动代码，撤销commit，不撤销git add .

## git add之后，想撤销add

```
	git reset --mixed HEAD^  
	或 git reset HEAD^
```

意思是：不删除工作空间改动代码，撤销commit，并且撤销git add . 操作
这个为默认参数,git reset --mixed HEAD^ 和 git reset HEAD^ 效果是一样的。

## 删除分支
1. 删除本地分支 git branch -d [branchname] 
2. 删除远程分支 git push origin --delete [branchname] 

## 撤销本地更改
```
	git checkout .
```

## 合并commit
```
git rebase -i HEAD~5 (合并最近五次提交)

//当合并出错时 进行fix
git rebase --edit-todo
//fix完成之后
git rebase --continue
```

## 本地（没有git版本）传到远程仓库
```
git init
git remote add origin https://github.com/wjq1994/react-learn.git
git add .
git commit -m ''
git push -u origin master
```

## git rebase

> 合并commit

1. 本地
    ```
    git rebase -i HEAD~3
    ```
2. 远程
   ```
   git push -f origin develop
   ```

## git stash

```
git stash                         //暂存
git stash save '描述'             //暂存并添加描述
git stash list                   //暂存记录
git stash pop                    //取出暂存第一条并删除
git stash drop  stash@{0}        //删除指定暂存
git stash apply stash@{0}        //取出指定暂存不删除
```

## 远程删除的分支在你本地仓库也将被删除

```
git remote prune origin
```

## 恢复误删远程分支

```
git reflog --date=iso
git checkout -b recovery_branch_name commitid
git push  origin recovery_branch_name 
```

## git reset 和 git revert的区别

```
git reset 原理是移动HEAD指针，HEAD时间线之后的版本都将去掉(git log可以发现)
可以通过git reflog命令查看历史操作记录，进行恢复HEAD时间线之后的版本
提交远程是git push -f
但是其他人从远程仓库拉下来的代码就看不到HEAD时间线之后的版本了, 就算知道HEAD时间线之后的版本id也无法操作
git revert -n 相当于是生成了新的版本
提交远程是git push
```