# Readme

## 创建ssh

```shell
ssh -keygen -t rsa -C "your_email@youremail.com"
//成功的话会在~/下生成.ssh文件夹，进去，打开id_rsa.pub，复制里面的key。
//回到github上，进入 Account Settings（账户配置），左边选择SSH Keys，Add SSH //Key,title随便填，粘贴在你电脑上生成的key。
//为了验证是否成功，在git bash下输入：

ssh -T git@github.com
//如果是第一次的会提示是否continue，输入yes就会看到：You've successfully //authenticated, but GitHub does not provide shell access 。这就表示已成功连上//github。 
```



## 新创建时会提示

```shell
git init
git add README.md
git commit -m "first commit"
git branch -M main
//以下一条命令第一次推送是时用,表明是本地仓库和远程仓库连接起来,以后推送直接运行下一条命令
git remote add origin git@github.com:funengqing/learngithub.git
git push -u origin main

```





```shell
git init 初始化仓库

git add 添加到暂存区

git status 显示目录和暂存区状态,可以看到文件是否被修改

git commit 更改的记录

git log 提交的记录
```



## 时光穿梭机

修改某个文件后会提交到暂存区,此时需要用git add命令提交到暂存区,然后再git commit到本地仓库

当某个文件被git add 后,如果不想追踪些文件,git add 后紧跟着使用git reset HEAT,此时本地仓库就没有这个文件

## 版本回退

使用git log -5 --pretty=oneline来查看commit 的标识符及commit 的信息,数字可以变的

使用git reflog 查看此前的操作,看不到commit的标识符时用(如关闭了窗口或清空了窗口)

git reset --hard HEAT^  回退到此版本的前一个版本

git reset --hard HEAT^^  回退到此版本的前二个版本,依次类推,但不推荐

git reset --hard HEAT~1 回退到此版本的前一个版本,数字表示要回退到此版本的前N个版本

git reset --hard 标识符(一般取标识符的前6位就可以,如果不行就取全部) 跳到指定的版本

所以可以看到所有的版本都是根据commit 来操作的

## 文件删除相关操作

当在工作区删除了一个被git add 和git commit 后的文件后,工作区此时已经没有了这个文件 ,但用git status 查看状态会看相关信息,此时本地仓库还是有此文件的,此时可以用git checkout -- 文件名(全部)来恢复此文件到工作区.(文件名可以根据git status来获取到标识为deledet 的那个文件  )

git rm 文件名,用于删除文件,commit 后的文件也会被删除,也就是说工作区和本地仓库的都会被删除,查看本地仓库的文件可以用get ls-files命令

## 推送到远程仓库

```shell
git add 文件名
git commit -m "推送信息"
git push -u origin main
```

## 本地分支

现实中很多都是在分支上进行开发的,完成后再合并到主分支

```shell
git checkout branchname 切换到指定分支
git checkout -b new_branchname 新建分支并切换到此新建分支
git branch -d branchname 删除指定分支
git brandch 查看所有分支,有*号的表示当前分支
git merge branchname 合并分支,需要先切换到主分支
git branch -m | -M oldbranchname newbranchname 重命名分支,如果名字已存在,则用-M强制,否则用-m进行重命名(先用-m,不行时才用-M,两者用其一)
//主分支上的文件在其他分支也会有,切换到其他分支时,在其他分支下所操作的文件不会出现在主分支中,可以使用 git ls-files 来查看当前分支下本地仓库的所有文件
//对其他分支的操作不会影响到主分支
//在其他分支操作主分支上的相同文件时,需要git add 和 git commit,因为合并分支时会用到,否则无法合并
//在其他分支上新加文件时,不需要上述的两条命令也可以合并
//在其他分支上删除主分区上相同文件?测试
//切换到某一个非主分支时,如果此时在工作区进行文件操作,是不会影响到主分支的
```



## 分支的push与pull

```shell
git branch -a 查看本地与远程分支
git push origin branchname 推送本地分支到远程分支
git push origin :remote branchname 删除远程分支,但本地分支还在
git checkout -b local_branch origin/remote_branch 拉取远程指定分支并在本地创建分支(一般是接手时会接取某个分支来进行开发)
```

