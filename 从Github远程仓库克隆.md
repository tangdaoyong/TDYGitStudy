#从Github远程仓库克隆
现在，假设我们从零开发，那么最好的方式是先创建远程库，然后，从远程库克隆。
首先，登陆GitHub，创建一个新的仓库，名字叫gitskills(自己的库可以随意取)：
![Github上创建远程库](/Users/tangdaoyong/TDYGitStudy/0.png)
我们勾选Initialize this repository with a README，这样GitHub会自动为我们创建一个README.md文件。创建完毕后，可以看到README.md文件。
现在，远程库已经准备好了，下一步是用命令git clone克隆一个本地库。
在电脑的终端输入：
>git clone git@github.com:tangdaoyong/远程库的名字.git

点击回车就可以在电脑中克隆了远程库。