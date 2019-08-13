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

## 实战
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
