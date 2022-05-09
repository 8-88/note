# Flex 4自定义ScrollBarSkin时自动计算XXXThumbSkin的高度

#### 问题：
* 在使用Flex 4默认皮肤的时候，滚动条的ThumbSkin是可以通过滚动内容的高度/宽度进行自动设置其高度/宽度。
* 在自定义ScrollBarSkin的时候，却无法通过滚动内容来设定其自身的高度/宽度。

#### 现象：
* 当滚动内容过多时，会出现ThumbSkin超出滚动界限的问题，如：![Flex 4 ScrollbarSkin error](http://i.imgur.com/AoYxXdS.png)

#### 解决：
<pre>
//在有使用Scrollbar的地方（例如AdvancedDataGridSkin、List等Skin）加入：
creationComplete="creationCompleteHandler()"
//
private function creationCompleteHandler() : void {
    scroller.verticalScrollBar.setStyle( "fixedThumbSize", true );
}
</pre>