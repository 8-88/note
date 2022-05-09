* 具体配置方式：
<pre>
    npm install jshare
    jshare = require 'jshare'
    app.use jshare 'server' 注意：放在app.use app.router前面
    res.server.person = {firstName : "Alex"};
    <%- JShare() %> 注意：这是HTML，并且放在&lt;title&gt;后面（EJS模板）
    在需要使用的地方使用，方式如：alert(jshare.server.firstName);
</pre>
* 代码地址：[https://github.com/brooklynDev/JShare](https://github.com/brooklynDev/JShare)

* 另可以参考：
> http://stackoverflow.com/questions/11151632/passing-an-object-to-client-in-node-express-ejs  
> https://github.com/tanema/express-helpers  
> http://stackoverflow.com/questions/6064282/node-js-ejs-using-javascript-inside-tags  
> http://stackoverflow.com/questions/13221760/nodejs-ejs-helper-functions
* 更好的方式：
<pre>
//node.js
member = JSON.parse( member )  
//html 
//memeber是JSON对象，需要转换成字符串，但是转换完毕后，貌似还是一个JSON对象...
&lt;script&gt; var aaa = <%- JSON.stringify( member ) %>; alert( aaa.role )&lt;/script&gt;
&lt;script&gt; var aaa = <%- member.role %>; alert( aaa )&lt;/script&gt;
</pre>