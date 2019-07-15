常用GIT命令

## 解决已经add，但是没有commit，直接运行git reset --hard xxxxx的情况
1. 执行 git fsck --lost-found；

2. 在.git/lost-found目录下找找看有没有你丢失的文件；

## 查看status,add之后，不想commit，希望撤回add之前的操作，但要保留修改（包括 新加文件、删除文件、已有文件修改等）
``` git reset -q```

注意不可使用 git reset --hard，本地文件会被替换，后悔莫及

