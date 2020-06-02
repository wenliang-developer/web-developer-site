[TOC]

##分支

**Git 的分支，其实本质上仅仅是指向提交对象(commit object)的可变指针**

```
A<---B<---C<----D
     ^          ^
     |          |
  branch      master
```

###基本概念

Git 历史记录中有三种对象：
- `blob `对象 - 保存着文件快照
- `tree` 对象 - 记录着目录结构和 blob 对象索引
- `commit`对象 - 会包含一个指向暂存内容快照的指针（前述树对象的指针和所有提交信息），还包含了作者的姓名和邮箱、提交时输入的信息以及指向它的父对象的指针。首次提交产生的提交对象没有父对象，普通提交操作产生的提交对象有一个父对象， 而由多个分支合并产生的提交对象有多个父对象

####HEAD
它是一个指针，指向当前所在的本地分支

###基本命令

#### 创建分支
```
git branch <branchname>
```

#### 合并分支

```
git merge <branch>
```

#### 删除分支

```
git branch -d <branch>
```

### 查看分支记录

#### 查看分支列表

```
git branch
```

#### 查看分支提交记录

```
git branch -v
```

#### 查看已经合并到当前分支的分支

```
git branch --merged
```

#### 查看已经尚未合并到当前分支的分支

```
git branch --no-merged
```

#### 查看分支分叉情况

```
git log --oneline --decorate --graph --all
```

###远程分支

####查看远程引用的分支列表

```
git ls-remote <remote>
```

####创建远程分支

```
git clone -o <remote> <remoteUrl>

git remote add <remote> <remoteUrl>
git fetch <remote>
```

####远程分支同步数据

```
git fetch <remote>
```

`git fetch` 和 `git pull` 区别：
- 当 `git fetch` 命令从服务器上抓取本地没有的数据时，它并不会修改工作目录中的内容。 它只会获取数据然后让你自己合并。
- `git pull` 在大多数情况下它的含义是一个 `git fetch` 紧接着一个 `git merge` 命令。
- 如果是一个远程分支，`git pull`都会查找当前分支所跟踪的服务器与分支， 从服务器上抓取数据然后尝试合并入那个远程分支。

####

```
git push <remote> <localBranch:originBranch>
```

####创建远程分支对应的本地分支

```
git checkout -b localBranch origin/originBranch
```

####合并到当前分支

```
git merge origin/originBranch
```

####创建跟踪分支

从一个远程跟踪分支检出一个本地分支会自动创建所谓的“跟踪分支”（它跟踪的分支叫做“上游分支”）。 跟踪分支是与远程分支有直接关系的本地分支。 如果在一个跟踪分支上输入 git pull，Git 能自动地识别去哪个服务器上抓取、合并到哪个分支。

```
git checkout -b <branch> <remote>/<branch>
git checkout --track <remote>/<branch>
git checkout <branch> (branch 只存在于远程分支上)
```

####当前本地分支 跟踪远程分支

```
git branch -u <origin>/<branch>
git branch --set-upstream-to <origin>/<branch>
```

####查看跟踪分支

```
git branch -vv
```

####同步所有远程仓库

```
git fetch --all; git branch -vv
```

####删除远程分支

```
git push origin --delete serverfix
```

###变基（rebase）

rebase 命令将提交到某一分支上的所有修改都移至另一分支上，就好像“重新播放”一样。

假设有以下历史记录，当前分支是 `topic`:
```
      A---B---C topic
     /
D---E---F---G master
```

运行以下命令：
```
git rebase master
或者
git rebase master topic
```

将会：
```
              A'--B'--C' topic
             /
D---E---F---G master
```

_ _ _


`--onto` 选项使用部分分支进行rebase，示例：
```
                        H---I---J topicB
                       /
              E---F---G---K  topicA
             /
A---B---C---D  master
```
运行以下命令：
```
git rebase --onto master topicA topicB
```
将会：
```
             H'--I'--J'  topicB
            /
            | E---F---G---K  topicA
            |/
A---B---C---D  master
```
