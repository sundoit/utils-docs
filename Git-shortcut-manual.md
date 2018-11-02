

Git 不同于GitHub，Git是一个版本控制系统，它可以帮助我们追踪我们机器上的程序和文件的变化，还可以让我们用它跟其他同事合作开发，编码和编辑文件。
GitHub以及跟其类似的服务包括GitLab，BitBucket等，都是站点，它们部署了Git服务器来帮我们保存代码，提供追踪服务。

1、我们要使用GitHub，首先需要在其上面注册账户，然后创建新的代码库repo，比如Demo

然后在我们自己的电脑上打开Termial终端，创建一个本地项目目录，跟我们的GitHub上项目库同名。

$ mkdir Demo

$ cd Demo

在该目录下创建一个README.md 文件

$ echo "#Demo" >> README.md

$ cat README.md

然后将该目录注册给本机Git 

$ git init

然后将README.md文件添加到本地Git库

git add README.md

接下来就是提交README.md的内容，每次提交就相当于创建了一个README.md文件的milestone，我们可以回到该点时的文件。

$ git commit -m "first commit" 

下一次，当我们对README.md 进行修改后，再次执行commit命令，会创建另外一个milestone

这些提交commit记录我们可以通过如下命令来查看

$ git log 


最后，我们连接本地Git库到GitHub上

$ git remote add <origin> https://github.com/<your_username>/<your_repo_name>.git

该命令是为我们的Git添加一个远程库，其名字为origin（可以是任意名，以后我们可以使用改名字来替代完整的URL来跟远程的库交互），比如我们可以起名为github_demo 

连上远程的GitHub库后，我们就可以使用git push命令将本地的README.md 推送到GitHub的库里。

$ git push -u origin master

输入登录密码，即可上传了。

--------------------------

2、上传完成后，日后如果要修改，我们可以通过 

$ git clone https://github.com/<your_username>/<your_repo_name>.git 

下载到本地，然后进行修改README.md

修改完成后，通过git status命令查看文件状态，会发现有提示

Changes not staged for commit;

是告诉我们下面的文件没有标记“staged”需要被提交,接下来我们执行：

$ git add filename 

Git会将该文件标记为准备好提交状态:

Changes staged for commit.

在我们执行 git add 命令前，我们可以通过执行

$ git diff 

它会显示文件的变化内容

diff --git a/README.md b/README.md 指定Git正在比较的内容，这里是比较README.md

--- a/README.md 移除的内容

+++ b/README.md 新增加的内容

Changes to be committed 指定文件名列表

如果你已经执行了git add命令，再去执行 git diff命令查看比较就不能显示变化了,此时需要执行 

$  git diff --cached

当我们修改完成后，将修改后的内容上传到github库

首先向Git库提交并添加提交说明：

$ git commit -m "Updated Readme comments"

然后执行推送

$ git push -u origin master 

---------------------------------------------------------

3、添加新文件：

大题的步骤是在本地创建新文件，add到Git，push到GitHub这样一个过程。

$ echo "This is a new file" >> newFile.txt

$ cat newFile.txt

$ git status # 需要添加到Git的内容

$ git add newFile.txt

$ git status # 需要提交的内容

$ git commit -m "Adding a new file" newFile.txt

$ git push -u origin master 

4、从Git删除一个文件

大题流程是，首先在本地通过rm 删除目标文件

$ rm delFile.txt

执行 

$ git status 

会看到 该文件not staged for commit,并且它已经被从本地删除了,接下来，我们执行

$ git add delFile.txt

$ git status

这里执行git add是为了告诉Git我们对delFile.txt的变化操作

git add命令会在添加新文件，修改已有文件，以及删除文件后都执行，它会将目标文件的所有变化记录到Git

此后执行的git status会显示有个文件已被删除需要提交，那么接下来我们就可以commit这次删除，并push它到远程github上。

$ git commit -m "Delete fdelFile.txt"

$ git push -u origin master


====================================================================

远程仓库相关操作

查看远程仓库：

$ git remote -v 显示需要读写远程仓库信息

下载远程仓库：

$ git clone https://github.com/sundoit/utils-docs.git

添加远程仓库：

$ git remote add <shortName> https://github.com/sundoit/new-repo

从远程仓库拉取内容：

$ git fetch <shortName>

想远程仓库推送内容：

$ git push <shortName> <branchName>

比如： $ git push origin master

查看指定远程仓库：

$ git remote show <shortName>

比如： $ git remote show origin

远程仓库重命名： A-->B

$ git remote rename A B

查看结果： $ git remote 

删除远程仓库：

$ git remote rm <shortName>


