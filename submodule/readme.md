
[参考链接](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97)

# 克隆含有子模块的项目，并更新
git clone --recurse-submodules https://github.com/chaconinc/MainProject

# 在包含子模块的项目上工作

### 从子模块的远端拉取上游修改

在项目中使用子模块的最简模型，就是只使用子项目并不时地获取更新，而并不在你的检出中进行任何更改。

1. 如果想要在子模块中查看新工作，可以进入到目录中运行 git fetch 与 git merge，合并上游分支来更新本地代码。

```
git fetch
git merge 
```

2. 此命令默认会假定你想要更新并检出子模块仓库的 master 分支

```
git submodule update --remote DbConnector
```

### 从项目模块的远端拉取上游修改

```
git pull --recurse-submodules
```

# 在子模块上工作

为了将子模块设置得更容易进入并修改，你需要做两件事。 首先，进入每个子模块并检出其相应的工作分支。 接着，若你做了更改就需要告诉 Git 它该做什么，然后运行 git submodule update --remote 来从上游拉取新工作。 你可以选择将它们合并到你的本地工作中，也可以尝试将你的工作变基到新的更改上。


```
git submodule update --remote --merge
```

# 发布子模块改动

如果我们在主项目中提交并推送但并不推送子模块上的改动，其他尝试检出我们修改的人会遇到麻烦， 因为他们无法得到依赖的子模块改动。那些改动只存在于我们本地的拷贝中。

为了确保这不会发生，你可以让 Git 在推送到主项目前检查所有子模块是否已推送。 git push 命令接受可以设置为 “check” 或 “on-demand” 的 --recurse-submodules 参数。 

> check

```
git push --recurse-submodules=check
```

如果任何提交的子模块改动没有推送那么 “check” 选项会直接使 push 操作失败。如果你想要对所有推送都执行检查，那么可以通过设置 git config push.recurseSubmodules check 让它成为默认行为。

