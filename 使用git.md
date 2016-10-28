#使用git

###修改查看提交
1.git status - 查看修改
2.git diff 文件名 - 查看修改的具体内容(按Q退出)
3.git add 文件名 - 添加
4.git commit -m "提示内容"
###版本回退
版本控制系统肯定有某个命令可以告诉我们历史记录，在Git中，我们用git log命令查看。
>$ git log
>$ git log --pretty=oneline显示的是git的版本号（SVN是1，2，3递增的数字）

首先，Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交3628164...882e1e0（注意我的提交ID和你的肯定不一样），上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
可以使用git reset回到以前的版本
>$ git reset --hard HEAD^

知道版本号，commit id
>$ git reset --hard 3628164

在Git中，总是有后悔药可以吃的。当你用$ git reset --hard HEAD^回退到add distributed版本时，再想恢复到append GPL，就必须找到append GPL的commit id。Git提供了一个命令git reflog用来记录你的每一次命令：
#####小结
现在总结一下：
HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit\_id。
穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

###撤销修改
>$ git checkout -- readme.txt

命令git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：

一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次git commit或git add时的状态。

git checkout -- file命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令，我们在后面的分支管理中会再次遇到git checkout命令。

###删除文件
一般情况下，你通常直接在文件管理器中把没用的文件删了，或者用rm命令删了：
>$ rm test.txt

现在你有两个选择，一是确实要从版本库中删除该文件，那就用命令git rm删掉，并且git commit：
另一种情况是删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本：
>$ git checkout -- test.txt

git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。
