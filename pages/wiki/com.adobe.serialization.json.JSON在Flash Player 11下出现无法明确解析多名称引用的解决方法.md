#### 现象：
* 在使用版本号高于11的playerglobal.swc（Flash Player也是如此）版本编译的时候会产生“无法明确解析多名称引用”的错误。
<pre>
//import
import com.adobe.serialization.json.JSON
//use
JSON.decode( xxx )
JSON.encode( xxx )
</pre>

#### 原因：
* 当Flash Player（playerglobal.swc）高于11时，FP增加了原生的解析JSON的顶级Class - JSON 
* 当在程序中使用JSON.xxx()的时候，编译器无法判断到底是com.adobe.serialization.json.JSON提供的方法？还是Flash Player提供的方法。

#### 解决：

* 第一种方案：（替换方案）
<pre>
remove import com.adobe.serialization.json.JSON
JSON.decode() → JSON.parse()
JSON.encode() → JSON.stringify()
</pre>

* 第二种方案：（手动指定JSON的包名）
<pre>
//import
import com.adobe.serialization.json.JSON
//use
com.adobe.serialization.json.JSON.decode( xxx )
com.adobe.serialization.json.JSON.encode( xxx )
</pre>