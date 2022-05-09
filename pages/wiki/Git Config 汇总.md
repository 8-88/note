<pre>
git config --global core.autocrlf false
git config --global core.trustctime false
git config --global core.filemode false

git config --global color.ui true
git config --global color.status auto
git config --global color.diff auto
git config --global color.branch auto
git config --global color.interactive auto

git config --global alias.st 'status'
git config --global alias.ci 'commit'
git config --global alias.co 'checkout'
git config --global alias.br 'branch'
git config --global alias.sr 'show-ref'

git config --global alias.cm '!sh -c "br_name=`git symbolic-ref HEAD|sed s#refs/heads/##`; git commit -em \"[\${br_name}] \""'
git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%x09%C(yellow)%d%Creset %C(bold yellow)<%an>%Creset %x09 %s %Cgreen(%cr)%Creset' --abbrev-commit --date=relative"
git config --global alias.cm=!sh -c "br_name=`git symbolic-ref HEAD|sed s#refs/heads/##`; git commit -em \"[\${br_name}] \""

# 自定义
git config --global alias.tree "diff-tree --no-commit-id --name-only -r"
git config --global alias.pr "pull --rebase"

不比较空行
git config --global apply.whitespace nowarn

比较
git difftool back-develop-2
git config --global diff.tool bc3
git config --global difftool.bc3.path "I:/TOOLS/Beyond Compare 3.3.5.15075/BCompare.exe"

git mergetool
git config --global merge.tool bc3
git config --global mergetool.bc3.path "I:/TOOLS/Beyond Compare 3.3.5.15075/BCompare.exe"

windows 
http://sourceforge.net/projects/kdiff3/files/kdiff3/0.9.97/
kdiff3的路径放到PATH环境变量
git config --global merge.tool kdiff3
git config --global mergetool.kdiff3.path "I:/TOOLS/KDiff3 0.9.97/kdiff3.exe"

列出1次提交中的所有文件？
http://stackoverflow.com/questions/424071/list-all-the-files-for-a-commit-in-git
git diff-tree --no-commit-id --name-only -r xxxxx(git lg)
git show --pretty="format:" --name-only xxxxxx(git lg)
</pre>