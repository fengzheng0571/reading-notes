

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

### 初始化一个Git仓库
```
$ git init
```
### 添加文件到Git仓库
```
$ git add readme.txt
$ git commit -m "wrote a readme file"
```

### 查看哪些文件有修改
```
$ git status
```

### 查看某个文件的修改内容
```
$ git diff
```

### 显示提交日志
``git log``
```
RajdeMacBook-Pro:learngit raj$ git log
commit 3bfd4fcce36ae7fe1dd851fbf59f701c71a6ea70
Author: feng <fengzheng0571@163.com>
Date:   Sun May 7 12:39:43 2017 +0800

    add "Hello Git"

commit 531036db6fb61335d7c8d971aec048cfc83a8a49
Author: feng <fengzheng0571@163.com>
Date:   Sun May 7 12:31:37 2017 +0800

    add 2 files

commit a358dfd7bfe25193422eb421697072ff459e8a71
Author: feng <fengzheng0571@163.com>
Date:   Sun May 7 12:24:28 2017 +0800

    wrote a readme file

```

``git log --pretty=oneline``
```
RajdeMacBook-Pro:learngit raj$ git log --pretty=oneline
3bfd4fcce36ae7fe1dd851fbf59f701c71a6ea70 add "Hello Git"
531036db6fb61335d7c8d971aec048cfc83a8a49 add 2 files
a358dfd7bfe25193422eb421697072ff459e8a71 wrote a readme file
```

### 回到上个版本
```
$ git reset --hard HEAD^
$ git reset --hard 3bfd4
```

### 查看命令历史
```
$ git reflog
```

### 撤销修改  
撤销工作区的修改
```
$ git checkout -- readme.txt
```

撤销工作区和暂存区的修改
```
$ git reset HEAD readme.txt
```

### 删除文件
```
$ git rm readme.txt
$ git commit -m "delete readme.txt"
```

### 关联远程仓库
```
$ git remote add origin git@server-name:path/repo-name.git
```

### 向远程仓库推送内容
第一次向远程仓库推送内容，加``-u``参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
```
$ git push -u origin master
```

```
$ git push origin master
```

### 克隆远程仓库
```
$git clone git@github.com:fengzheng0571/reading-notes.git
```

### 保存工作区内容
```
$git stash
```

### 恢复工作区内容
```
$git stash pop
````
或者
```
$ git stash list
$ git stash apply stash@{0}
```

### 要查看远程库的信息
```
$ git remote
```
查看仓库详细信息
```
$ git remote -v
```

### 标签
git tag <name>用于新建一个标签，默认为HEAD，也可以指定一个commit id；
git tag -a <tagname> -m "blablabla..."可以指定标签信息；
git tag -s <tagname> -m "blablabla..."可以用PGP签名标签；
命令git tag可以查看所有标签。
命令git show <tagname> 查看标签详细信息
命令git push origin <tagname>可以推送一个本地标签；
命令git push origin --tags可以推送全部未推送过的本地标签；
命令git tag -d <tagname>可以删除一个本地标签；
命令git push origin :refs/tags/<tagname>可以删除一个远程标签。
