<pre>

更新不同分支的同一个文件

// 先修改某个分支的文件，并且提交
git checkout develop
// modify something.txt
git commit -am "something comment."
git push origin develop

// 再切换到另外的分支，同步更新这个文件之后，再提交。
git checkout master
git checkout develop -- someting.txt
git commit  -am "something comment."
git push origin master

查看当前refs
git branch -r

删除当前分支
git branch -d xxxxxx

强制删除当前分支
git branch -D xxxxxx

删除本地分支（working dir）
git br -D <br_name> <br_name>

删除远程分支的本地跟踪分支
git br -D -r origin/<br_name>

删除远程服务器的分支（同时删除本地和远程）
git push origin :<br_name>
git push origin --delete <br_name> <br_name>

比较不同commit之间变化的文件
git diff HEAD..origin/feature/merge-canvas-module-ks --stat

git diff commit_id1..commit_id2 --stat
是以commit_id1为base

git diff commit_id2..commit_id1 --stat
是以commit_id2为base

比较两个版本中某个具体文件的差异
git diff HEAD:src/js/ide/canvas_layout.js a868932:src/js/ide/canvas_layout.js
git difftool HEAD:src/module/design/resource/template_data.html a868932:src/module/design/resource/template_data.html

比较任意两个分支的差别
git diff <branch1>...<branch2>
git diff feature/phantom-v3...release/v0.2-201309

查看任意分支的log
git lg <分支名>

可视化工具
gitk develop 
gitk feature/module-canvas-v2
git gui

还原到某个分支的某个版本
git checkout <分支名> <文件名>
git checkout feature/module-property-panel-ks src/module/design/template.html

进入某个分支后，逐行查看某个文件的修改情况
git blame <文件名>

撤销当前文件的修改
git checkout -- <文件名>
git checkout -- src/ui/common/UI.scrollbar.js

# checkout 8713572 到 <new_branch_name>
git co 8713572 -b <new_branch_name>

# 强制提交到远程
git push origin develop -f

# 强制恢复到某一版本
git reset -- hard xxxxx 某一版本

git add -A 处理所有：添加、修改、删除
git add . 处理添加和修改，不处理删除
git add -u 处理修改和删除，不处理新添加文件

git reset       # 撤销add
git reset 目录  # 撤销add目录
git reset 文件  # 撤销add文件
以上撤销只是针对add，不会撤销修改。

# 撤销所有变更，包括修改
git reset --hard HEAD

# git add 操作
git add -A 处理所有：添加、修改、删除
git add . 处理添加和修改，不处理删除
git add -u 处理修改和删除，不处理新添加文件
git status //查看当前状态（是否有未提交等等）
git show-ref //查看当前与远程分支是否一致

# 撤销到未push到origin的xxx次提交
git reflog                  #得到需要rollback的SHA1代码，如7b9fb7e
git reset --hard 7b9fb7e    #删除截至到7b9fb7e（包括它）之后的全部内容

#删除远程分支对应的本地无效分支
git fetch -p

#git pull --rebase
#使用rebase，能让合并点变成一条直线
http://blog.csdn.net/largetalk/article/details/7423015

http://segmentfault.com/q/1010000000184974
http://jianshu.io/p/fbc9eca95e26
# 用来应付需要马上切换分支的情况
# 将文件给push到一个临时空间中
git stash
# 将文件从临时空间pop下来
git stash pop

# 删除某个文件从git库
git rm 文件名(包括路径)

# 可以显示出所有变更的文件列表
git checkout xxxxx_rev_1
git format-patch xxxxx_rev_2

# 获取两个版本之间的差异
git diff --name-status v1..v2

# 只合并特定的分支特定文件（未测试）
用命令 git cherry-pick #commitid
checkout方法 git checkout branch -- filename

# 只显示有对比的文件
git diff 608e120 4abe32e --name-only

# 只显示有对比的文件（压缩成一个文件）
git diff 608e120 4abe32e --name-only | xargs zip update.zip

# 查看今天的更改
git log --since=1.days

# 查看缓存区和本地仓库里的差异
git diff --cached

# 查看已缓存和当前的区别
git diff HEAD 

# 将file从文件缓存区、本地目录中移除
git rm file

# 只从缓存区移除，保存本地目录中的
git rm file --cached 
</pre>