
#### 图片转换Base64编码：

<pre>
var fs = require("fs");
var imageBuf = fs.readFileSync("D:\\Documents\\Desktop\\baidu_jgylogo3.gif");
console.log(imageBuf.toString("base64"));
</pre>

#### 下载Base64编码的Html5：

<pre>

写法：
data:image/png;base64,<png的base64编码>

例如：
$( '#btn-confirm' ).attr {
    'href'      : "data://text/plain; " + file_content,
    'download'  : MC.canvas_data.name + '.json',
}

$( '#btn-confirm' ).attr {
    'href'      : "data:image/png;base64, " + base64_image,
    'download'  : MC.canvas_data.name + '.png',
}
</pre>

#### node.js 字符串 → base64
<pre>
转换为Base64：
var a = new Buffer( 'key1=value1&key2=value2' ).toString( 'base64' );
'a2V5MT12YWx1ZTEma2V5Mj12YWx1ZTI='

解析为字符串：
var b = new Buffer( a, 'base64' ).toString()
'key1=value1&key2=value2'
</pre>