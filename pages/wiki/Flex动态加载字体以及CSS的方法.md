#### 字体嵌入：

##### 格式：
<pre>
[Embed(source="xxx", fontName="FontName", fontStyle="normal", fontWeight="normal", embedAsCFF="false", advancedAntiAliasing="true", mimeType="application/x-font")]
public var ClassName : Class;
</pre>
##### 参数含义：
* source : 指定嵌入字体的地址（AIR:可以指定操作系统路径;Flex:指定项目相对路径）
* fontName : 字体的别名（也可以使用fontFamily）
* fontStyle : normal | italic
* fontWeight : normal | bold
* embedAsCFF : true(用于Spark组件) | false（用于Halo组件）
* advancedAntiAliasing : 抗锯齿
* mimeType ：application/x-font（唯一的值）
* unicodeRange : 字体的范围（一般用于中文字体，因中文字体比较大，故只包含当前文字的unicode）
* 嵌入字体代码：（方式1）
<pre>
//FontLibrary.as 编译成 FontLibrary.swf
package {
    import flash.display.Sprite;
	import flash.text.Font;
    //
	public class FontLibrary extends Sprite {
		[Embed(source="xxx.ttf", fontName="AFont", fontStyle="normal", fontWeight="normal", embedAsCFF="false", advancedAntiAliasing="true", mimeType="application/x-font")]
		static public var ClassName : Class;
		//
		public function FontLibrary() {
			Font.registerFont( ClassName );
		}
	}
}
//使用（在Flex里）
var fontLoader : Loader = new Loader();
fontLoader.load( new URLRequest( "FontLibrary.swf" ));
fontLoader.contentLoaderInfo.addEventListener( Event.COMPLETE, function() :void {
    xxx.setStyle( "fontFamily",  "AFont" );
});
</pre>

* 嵌入字体代码：（方式2）
> 使用 __[Flash汉字嵌入助手](http://kevincao.com/2010/07/hanfont/)__

#### 动态载入CSS：

##### CSS代码：
<pre>
/* style.css
 * css file 
 */
@namespace s "library://ns.adobe.com/flex/spark";
@namespace mx "library://ns.adobe.com/flex/mx";
//
mx|Label {
    fontSize : 40;
}
//
.NunitoLightMX {
	fontFamily : Nunito-Light-mx;
}
</pre>

##### 编译：
* mxmlc style.css
> 会生成style.swf

##### 使用：
<pre>
//load
styleManager.loadStyleDeclarations2( "style.swf" );
//use
xxx.styleName = "NunitoLightMX";
</pre>

##### 动态载入字体及CSS：
* 动态载入CSS：
<pre>
StyleManager.loadStyleDeclarations( "style.swf" );
</pre>
* 如果动态载入的CSS包含动态载入的字体，那么必须要先载入字体，然后才能载入CSS，代码如下：
<pre>
var fontLoader : Loader = new Loader();
fontLoader.load( new URLRequest( "FontLibrary.swf" ));
fontLoader.contentLoaderInfo.addEventListener( Event.COMPLETE, function() :void {
    event : IEventDispatcher = StyleManager.loadStyleDeclarations( "style.swf" );
    event.addEventListener( StyleEvent.COMPLETE, function() : void {
        xxx.styleName = "NunitoLightMX";
    });
});
</pre>

* 注意：
> 当主程序Load完毕FontLibrary.swf后，Module则可以直接使用FontName，Module不需要再Load一次。