* express与ejs的版本需要对应，截止到2013-02-04它们的版本分别是：
> express → 3.1.0 | ejs → 0.8.3   
* ejs旧版本最主要的变化就是去掉了partial，包括：
<pre>
//node.js端： 
res.partial → res.render  
//html端： 
&lt;%- partial( "footer" ) %&gt; 改为 &lt;% include footer.html %&gt;
</pre>