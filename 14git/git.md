### git 查看查看所有分支列表：
也就是本地的和远程的都能查看，
git branch -a

### 查看远程分支列表：

```
git branch -r
```

### 查看本地分支：
git branch

### 切换本地分支
git checkout 本地分支名

### 创建本地分支并切换本地分支
git checkout -b 新的本地分支名
### 创建远程分支
先创建本地分支，然后push到远程并且创建一个和本地分支一样的名字
1.git checkout -b 新的本地分支名

```
git checkout -b develop2
```

2.git push --set-upstream origin 本地分支名  :  远程分支会创建一个和本地分支一样的名字

```
git push --set-upstream origin develop2
```



### 新建本地分支并且切换到本地分支 ，并且新建的本地分支和远程分支关联
git checkout -b 本地分支名 origin/远程分支名

```
git checkout -b develop remotes/origin/develop
```

## 查看本地分支和远程分支的跟踪关系

```
 git branch -vv
```

```
$ git branch -vv
* develop 3903dba [origin/develop] Initial commit
  master  616628b [origin/master] master
```



### 新建一个本地分支develop 并且和远程分支origin/develop关联

```
git branch --track develop origin/develop
```
### 删除本地分支
git branch -d 本地分支名

### 删除远程分支

删除远程分支branchname

 `git push origin --delete [branchname]`  