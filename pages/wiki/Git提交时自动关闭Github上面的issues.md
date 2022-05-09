在github上面建立一个issues，会得到一个编号`#xxx`，如`#1`
<pre>
git commit -m "xxxx fixes #1"`(对应github上面的编号)
git push origin <branch_name>
</pre>

自动关闭编号为#1的issues。


#### commit格式如下：
<pre>
fix #xxx
fixes #xxx
fixed #xxx
close #xxx
closes #xxx
closed #xxx
resolve #xxx
resolves #xxx
resolved #xxx
</pre>