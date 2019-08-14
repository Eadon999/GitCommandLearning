# GitCommandLearning
learning the command of Git
##创建分支并切换的原理
之前提到的 HEAD 严格来说不是指向提交，而是指向master，master才是指向提交的，所以，HEAD指向的就是当前分支。

一开始的时候，master分支是一条线，Git用master指向最新的提交，再用HEAD指向master，就能确定当前分支，以及当前分支的提交点，每次提交，master分支都会向前移动一步，这样，随着你不断提交，master分支的线也越来越长。

当我们创建新的分支，例如dev时，Git新建了一个指针叫dev，指向master相同的提交，再把HEAD指向dev，就表示当前分支在dev上。

不过，当切换到dev分支后，对工作区的修改和提交就是针对dev分支了，比如新提交一次后，dev指针往前移动一步，而master指针保持不变

假如我们在dev上的工作完成了，就可以把dev合并到master上。Git怎么合并呢？最简单的方法，就是直接把master指向dev的当前提交，就完成了合并。

合并完分支后，甚至可以删除dev分支。删除dev分支就是把dev指针给删掉，删掉后，我们就剩下了一条master分支，HEAD又指向了master

摘自 廖雪峰的官方网站，图文并茂，非常清楚

## 基础知识
### 创建与切换分支：
#### 1、创建 develop 分支并切换：

git checkout -b develop
##### 这里 checkout -b 是复合命令，一个是创建，一个是切换：<br>
创建分支的命令是 git branch develop <br>
切换分支的命令是 git checkout develop <br>
#### 2、创建完成后执行 git branch 可以查看所有本地分支：

$ git branch
* develop # 前面带星号的表示当前所在分支
  master

1. 切换到被copy的分支（master），并且从远端拉取最新版本

$git checkout master

$git pull



## 从当前分支拉copy开发分支
### Step1:创建分支
git checkout -b dev
Switched to a new branch 'dev'



### Step2:把新建的分支push到远端 <br>
git push origin dev



### Step3:拉取远端分支 <br>
git pull

There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

git branch --set-upstream-to=origin/<branch> dev

经过验证，当前的分支并没有和本地分支关联，根据提示进行下一步：


### Step4:关联

git branch --set-upstream-to=origin/dev

注意：这里branch之后都是没有空格的，如果有空格则是错误命令

### Step5:再次拉取 验证

git pull

## 合并分支
### Step1：切换到开发分支并git pull更新本地
git checkout dev20190813

git pull

### Step2：切换到master并git pull更新本地
git checkout master <br>
git pull

### Step3：合并dev到master
git merge dev20190813

git push origin master




## 删除远程分支
### Step1：查看远程分支
git branch -r
### Step2：删除远程
 git branch -r -d  origin/dev20190813
### Step3：删除指令push到远端
 git push origin :dev20190813   #冒号一定要有

