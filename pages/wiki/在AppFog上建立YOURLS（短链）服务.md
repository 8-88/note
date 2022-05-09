Date: 2013-02-22 12:00:27

###YOURLS的下载地址：
* [http://yourls.org/](http://yourls.org/)

###在AppFog上面连接MySQL数据库（以PHP为例）：
* 参考文档：[https://docs.appfog.com/services/mysql](https://docs.appfog.com/services/mysql)
* 结合YOURLS的特点，修改user/config-sample.php文件，重命名为config.php，并加入如下内容：
<pre>
//AppFog Env Variables
$services_json = json_decode(getenv("VCAP_SERVICES"),true);
$mysql_config  = $services_json["mysql-5.1"][0]["credentials"];
$username      = $mysql_config["username"];
$password      = $mysql_config["password"];
$hostname      = $mysql_config["hostname"];
$port          = $mysql_config["port"];
$db            = $mysql_config["name"];  
//MySQL database username
define( 'YOURLS_DB_USER', $username );
//MySQL database password
define( 'YOURLS_DB_PASS', $password );
//The name of the database for YOURLS
define( 'YOURLS_DB_NAME', $db );
//MySQL hostname
define( 'YOURLS_DB_HOST', $hostname );
//MySQL tables prefix
define( 'YOURLS_DB_PREFIX', 'yourls_' );
</pre>

**注意：**其他过程与AppFog | YOURLS 建立流程一致。