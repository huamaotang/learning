# git学习笔记
## 基础命令
把指定目录变成Git可以管理的仓库

```
git init
```
克隆远程仓库

```
git clone git@github.com:huamaotang/techspace.git
```
掌握仓库当前的状态

```
git status
```
能看看具体修改了什么内容

```
git diff
```
把文件修改添加到暂存区

```
git add
```
把暂存区的所有内容提交到当前分支

```
git commit -m  
```
显示从最近到最远的提交日志

```
日志简要
git log --pretty=oneline
可以看到分支合并图
git log --graph     
可以看到分支的合并情况
git log --graph --pretty=oneline --abbrev-commit
```
HEAD表示当前版本上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100

```
git reset --hard HEAD^
```
可以指定回到未来的某个版本

```
git reset --hard 3628164
```
用来记录你的每一次命令

```
git reflog
```
可以丢弃工作区的修改

```
git checkout -- readme.txt
```
查看远程分支

```
git remote -v
```
查看本地分支

```
git branch -a
```
提交到远程分支

```
git push -u origin_github master     （第一次提交）
git push origin_github master
git push origin test:master         // 提交本地test分支作为远程的master分支
git push origin test:test              // 提交本地test分支作为远程的test分支
git push origin :test              // 刚提交到远程的test将被删除，但是本地还会保存的，不用担心
```
创建dev分支，然后切换到dev分支

```
git checkout -b dev
git branch dev
git checkout dev
```
把dev分支的工作成果合并到master分支上

```
git merge dev
git merge --no-ff master //no fast-forward
```
删除dev分支

```
git branch -d dev
```
## 配置
查看配置信息

```
git config --list
```
别名配置

```
git config --global alias.df diff
git config --global alias.st status
git config --global alias.ci commit
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
git config --global alias.cf config
```
区分文件名大小写

```
git config --global core.ignorecase false //区分
```
设置pull默认为rebase

```
git config --global pull.rebase=true
```
设置用户名和邮箱

```
git config --global user.name Tom
git config --global user.email tanghuamao@noahwm.com
```
## 合并代码，解决冲突

```
git pull
```

```
git merge --no-ff master
```

```
git rebase master
```

因pull=fetch+rebase或者pull=fetch+merge
假设为rebase，若存在文件冲突，当你解决完冲突之后，切记使用:

```
git add -u
```
继续合并

```
git rebase --continue
```
忽略合并的分支，使用当前指向分支的内容

```
git rebase --skip
```
忽略本次合并，回到合并之前的分支

```
git rebase --abort
```
注意：

```
rebase和merge的区别：
	* rebase 不产生新的提交记录，保证整个分支上是一条完整的直线
	* merge 会产生新的一次提交，除非fast-forward，否则都将产生一次新的提交
	* 建议pull代码的时候使用rebase，合并master或者其他分支时使用merge

```
## 学习地址
[http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
