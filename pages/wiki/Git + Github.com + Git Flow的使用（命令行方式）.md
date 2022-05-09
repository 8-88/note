Title: Git + Github.com + Git Flow的使用（命令行方式）
###MSYSGit的配置：
####下载地址（Portable版本即可）：
* <http://code.google.com/p/msysgit/>
####配置：
* 下载并解压缩到任意路径，如：F:\kenshin\DevTools\git-1.8.1.2
* 在环境变量里面增加如下内容：
> GIT_HOME = F:\kenshin\DevTools\git-1.8.1.2
> Path += %GIT_HOME%\bin
* 重启系统，并在CMD中键入：__git --version__
###util-linux-ng for Windows的配置：
####下载地址：
* <http://gnuwin32.sourceforge.net/packages/util-linux-ng.htm>
> 分别下载：Binaries和Dependencies（不用下载exe安装版）
####配置：
* 解压缩下载后的内容（两个Zip文件）
* 将解压缩后的两个文件（getopt.exe 和 libintl3.dll）复制到MSYSGit\bin文件夹中。
* 在CMD中使用：$ git clone --recursive git://github.com/nvie/gitflow.git 如：F:\kenshin\DevTools\gitflow
* 进入 F:\kenshin\DevTools\gitflow\contrib，并在CMD中键入：msysgit-install.cmd
* 在CMD中键入：git flow ，如出现如下内容则说明Git Flow配置成功。
<pre>
usage: git flow &lt;subcommand&gt;
Available subcommands are:
   init      Initialize a new git repo with support for the branching model.
   feature   Manage your feature branches.
   release   Manage your release branches.
   hotfix    Manage your hotfix branches.
   support   Manage your support branches.
   version   Shows version information.
</pre>
###命令行方式连接GitHub：
####生成SSH：
* 在CMD定位到 F:\kenshin\DevTools\git-1.8.1.2
* 在CMD中键入：__ssh-keygen -t rsa -C "xxx@gmail.com"__
> 系统会提示一些信息，直接回车三次即可。
* 生成的PUB文件一般建立在当前用户的根目录（如：windows用户可以在Exporer下面直接键入当前用户名称，如：kenshin）就会发现.ssh文件夹生成：__id_rsa 和 id_rsa.pub__。
####设置GitHub：
* 用文本编辑工具打开id_rsa.pub，复制其中的内容。
* 进入Github.com你的账户中心，新建一个Publick SSH，并将刚才的内容粘贴到其中并保存。
> __注意：__去掉前后的空格和回车
* 在Github.com中随便建立一个新的资源库，名叫较：test-flow，并复制其中的SSH地址，如：__git@github.com:Kenshin/test-flow.git__
####测试：
* 在CMD中随便定位到一个文件夹，如：F:\kenshin\Sync\Repository\Github，并键入：__git clone git@github.com:Kenshin/test-flow.git__
* 如上述军配置成功的话，test-flow会出现在 F:\kenshin\Sync\Repository\Github中。
* 简单描述一下命令行Git的用法：
<pre>
git clone git@github.com:Kenshin/test-flow.git
进行一些修改。
git add .
git commit -m "xxxx"
git push origin
上述步骤为一个比较典型的Git用法。
下面介绍一些较常用功能：
git remote show origin #显示当前的origin名字，如果是从GitHub.com下载，则origin就指向它，如上例中的：git@github.com:Kenshin/test-flow.git
git config --global user.name kenshin #设定全局用户名（跟Github.com一致）
git config --global user.email fxblog@gmail.com#设定全局邮件（跟Github.com一致）
git checkout xxx #切换当前branch。
git branch #查看当前branch
//查看远程分支的参考文档：<http://zengrong.net/post/1746.htm>
git branch -a #查看远程branch
git push origin --delete "远程分支名" #删除远程分支（方式1）
git push origin :"远程分支名" #删除远程分支（方式2）
git fetch -p #删除不存在对应远程分支的本地分支
//取得分支
git fetch origin xxxx #取得某个具体分支
git merge FETCH_HEAD #合并之前取得的某个具体分支到当前branch
git fetch origin #取得全部分支
git merge origin/xxxx #合并某个具体分支到当前branch
//多个分支进行merge的常用方式
git fetch origin xxxx #取得remote xxxx分支到本地
git checkout xxxx #切换到xxxx分支
git checkout -b yyyy #在xxxx分支基础上增加yyyy分支
//注意：这里并没有使用以下的方式
git fetch origin xxxx #取得remote xxxx分支到本地
git flow feature start xxxx
因为：git flow xxxx start是在develop的基础上增加一个新的分支，因此不适合上述情况。一般情况下，git flow xxxx start更适合从release阶段的开发
//增加一个.gitignore
touch .gitignore
//标记Tag
git tag v0.0.1
//上传tag到remote
git push origin xxxx --tag
//撤销全部修改（未提交）
git stash
//撤销某个文件的修改
git checkout file-name
//还原已经提交的修改
git revert HEAD      //还原最近一次提交的修改
git revert commit-id //还原指定版本的修改
//各种Git操作
<http://wangcongming.info/2010/07/git-%E7%B3%BB%E5%88%97%E4%B9%8B%E5%9B%9B%EF%BC%9Agit-%E8%BF%9B%E9%98%B6%E5%8A%9F%E8%83%BD/>
</pre>
###使用Git Flow：
####参考文档：
* <http://selfcontroller.iteye.com/blog/996494>
* <http://www.xwuxin.com/?p=1022>
#### 命令描述：

##### git flow 使用方法：（单一分支方式）
<pre>
git clone git@github.com:Kenshin/test-flow.git
cd test-flow
git flow init
显示需要录入的信息全部都是回车（即：默认配置）
git flow feature start test01
git add .
git commit -m "xxxx"
git flow feature finish test01
git checkout master
git merge develop
git push origin
</pre>

##### git flow 使用方法：（多个分支方式）
<pre>
git clone git@github.com:Kenshin/test-flow.git
cd test-flow
git flow init
git flow feature test01
修改一些内容
git add .
git commit -m "xxxx"
git flow feature start test02
git checkout feature/test01
git flow feature finish test01
git checkout master
git merge develop
git push origin
git checkout feature/test02
修改一些内容
git add .
git commit -m "xxxx"
git flow feature finish test02
由于同时开了两个分支，所以develop也应该需要提交一下
git add .
git commit -m xxxx
git checkout master
git merge develop
git push origin
</pre>
####通常的流程：
<pre>
User A:
git clone git@github.com:Kenshin/test-flow.git
git flow init
git flow feature start XXXX
修改代码
git flow feature finish XXXX
User B:
git push origin feature/XXXX
git fetch origin
git merge origin/feature/XXXX
</pre>
####Git中文乱码：
* 无法显示中文（如ls命令）：
<pre>
{GIT_HOME}/etc/git-completion.bash增加一行：
alias ls='ls --show-control-chars --color=auto'
</pre>
* git commit不能提交中文注释：
<pre>
{GIT_HOME}/etc/inputrc修改对应的行：
set output-meta on
set convert-meta off
</pre>
* git log无法显示中文注释：
<pre>
{GIT_HOME}/etc/profile增加一行：
export LESSCHARSET=iso8859
</pre>