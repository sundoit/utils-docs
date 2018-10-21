

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

