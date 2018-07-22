### git stash

```
git stash 

git stash list

git stash apply stash@{1}      不带参数则是最近的保存
```



###git log

git reflog 带reset的log

git log -p 详细版log





### 在别的分支上复制某一次提交

```markdown
git cherry-pick  hash 从某一分支上复制一份到现在的一个分支上
若遇冲突，解决后 add  **不要 commit** 直接 git cherry-pick --continue 

```



### 版本回退

```
git reset —hard head^
[远程库版本回退方法](http://blog.csdn.net/fuchaosz/article/details/52170105)
git reflog 
git reset --hard xxxxxxxxx
git push -f 回退并且强制push 

其他人协调问题
git checkout tony_branch        //先回到自己的分支  
git reflog                      //接着看看当前的commit id,例如:0bbbbb    
git reset --hard B1             //回到被覆盖的那次提交B1
git checkout -b tony_backup     //拉个分支，用于保存之前因为回退版本被覆盖掉的提交B1
git checkout tony_branch        //拉完分支，迅速回到自己分支
git reset --hard 0bbbbbb        //马上回到自己分支的最前端
接着Tony要把自己的本地master分支和远程master分支保持一致：
git reset --hard origin/master

接着Tony要再次合并那个被丢掉的B1提交：
git checkout master             //切换到master
git merge tony_backup           //再合并一次带有B1的分支到master

同理对于所有队友也要这样做，但是如果该队友没有提交被你丢掉，那么他拉完代码git pull之后，只需要强制用远程master覆盖掉本地master就可以了：
git reset --hard origin/master


最简单粗暴的回退方法 直接把代码复制一份 然后全删了，再重新粘回来，再提交一次。

```



### git diff

```
add之后又修改 查看 add 之后未 add 的更改
$ git diff <filename>
工作目录 vs Git仓库
git diff <commit> <filename>
暂存区 vs Git仓库
git diff --cached <filename>
```



####查看代码是谁写的

git blame



### git pull 远程分支

>  ```
>  git pull <远程主机名> <远程分支名>:<本地分支名>
>  ```



###git克隆新的远程分支

git branch -r|-a 

Git chekout orgin/xx/xxx

较差的解决方案

```
git branch daily/1.4.1
git checkout daily/1.4.1
git branch --set-upstream-to=origin/daily/1.4.1 daily/1.4.1
git pull
```



Git fetch -p



Git merge —fast-ward





### Git 子模块

```


https://segmentfault.com/a/1190000003076028

git submodule init

git submodule update


```


git的head分离

git checkout hash  or  master~100 head^ 等分离head

git checkout master^2  第二个父提交， merge时有俩个父提交，此时用 ^n 来区分

`git branch -f master HEAD~3`前面的命令会将 master 分支强制指向 HEAD 的第 3 级父提交。

git rebase xxx 将当前分支 移动到xxx分支上

git rebase bugFix side 将 side 移动到bugFix上 

Git rebase -i  从本次提交到哪一次提交的中间所有节点 甚至可以合并。  超级变态的方式

Git cherry-pick xxx,xxx,xxx 复制三个提交信息到当前分支。

git reset xxx 撤销本地修改  git revert 撤销远程更改。会修改



git commit —amend 修改提交信息。



git tag v1 C1 在c1 上打 v1 标签



`git describe xxxxx` 锚点  输出 tag值\_相差几个提交\_xxxxx



`git pull --rebase` = git fetch + git rebase

git pull = git fetch+git merge 



关联远程分支：

`git checkout -b totallyNotMaster o/master`    可以创建一个名为 `totallyNotMaster` 的分支，它跟踪远程分支 `o/master`。

`git branch -u o/master foo`

这样 `foo` 就会跟踪 `o/master` 了。如果当前就在 foo 分支上, 还可以省略 foo：

`git branch -u o/master`



git push origin 本地^：远程分支名  本地上一个 远程名不存在会自动新建的。

git fetch origin foo~1:bar 将远程分支foo的父节点下载到bar中，没有会新建



git push origin :foo 删除远程和本地的 foo 分支

git fetch origin :foo	在本地新建一个分支 foo



###[git 比较同一文件的不同的两个版本之间的差异](https://segmentfault.com/q/1010000005974787)

git diff commit_id1 commit_id2 -- index.html


### git 暂时不跟踪某一个文件
`git update-index --assume-unchanged filename.py`
取消不跟踪
`git update-index --no-assume-unchanged filename.py`


​        