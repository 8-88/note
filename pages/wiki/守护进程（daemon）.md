



### Node.js下的守护进程

#### forever

##### 安装：
`npm install -g forever`

##### 使用：

<pre>
启动
forever start -a -l forever.log -o out.log -e err.log xxx.js

停止
forever stop xxx.js
</pre>

##### 参考：
* <http://wenxin2009.iteye.com/blog/1751546>
* <https://github.com/nodejitsu/forever>

##### 注意：
`在win下不太好用，但能正常使用`

#### Supervisord
##### 简介：
与forever相比，多了监控文件改变而重启node.js的功能。（daemon方面应该没有forever强大，但对win的支持比较好）

##### 安装：
npm install -g supervisor

##### 使用：
supervisor index.js

##### 参考：
* <https://github.com/isaacs/node-supervisor>
* <http://blog.iwege.com/posts/nodejs-live-reload.html>
* <http://www.cnblogs.com/pigtail/archive/2013/01/08/2851056.html>
* <https://github.com/remy/nodemon>
* <http://www.jb51.net/article/29332.htm>
* <http://strongloop.com/strongblog/comparison-tools-to-automate-restarting-node-js-server-after-code-changes-forever-nodemon-nodesupervisor-nodedev/>

#### daemon结合require( 'domain' )效果最好

##### 安装：
`npm install domain-middleware`

##### 使用：
<pre>
domain     = require 'domain'

app.use ( req, res, next ) ->
	d = domain.create()
	d.on 'error', ( error ) ->
		console.log error
		res.statusCode = 500
		res.json { 'status' : 'error', 'error_msg' : 'server faild' }
		d.displose()
	d.add req
	d.add res
	d.run next
</pre>
	
##### 参考：
* <http://cnodejs.org/topic/516b64596d38277306407936>
* <https://github.com/fengmk2/domain-middleware>

#### 比较著名的进程管理：Supervisord（python）
##### 参考：
* <http://feilong.me/2011/03/monitor-processes-with-supervisord>
* <http://chenxiaoyu.org/2011/05/31/python-supervisor.html>