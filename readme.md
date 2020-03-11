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

# fafdsfafdsadfsfsdf
