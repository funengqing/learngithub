# Readme

```shell
git init
git add README.md
git commit -m "first commit"
git branch -M main
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
