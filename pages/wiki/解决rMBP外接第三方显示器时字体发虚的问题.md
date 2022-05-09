#### 问题现象：
当rMBP外接第三方显示器，并使用HDMI方式连接时会出现字体发虚的现象。（如使用mini DP则无此问题）

#### 问题原因：
* OS X会识别HMDI为电视模式，所以字体清晰度很差。
* 可以通过 关于本机 → 更多信息 → 系统报告 → 图形卡/显示器 → 电视选项（此时为【是】）

#### 解决：
* 需要合上rMBP。（非常重要的步骤，使其系统使用外接显示器模式）
* `cd downloads`
* `curl -L https://gist.githubusercontent.com/adaugherity/7435890/raw/5af7e8f7ebef354037b9be39de90b2149b84fec1/patch-edid.rb -o patch patch-edid.rb`
* `ruby patch-edid.rb`
* 将会在`downloads`文件夹下生成一个类似`DisplayVendorID-XXXX`的文件夹。
* 拷贝此文件夹到`/System/Library/Displays/Overrides `，需要使用`sudo权限`。（如果有覆盖，请先备份）
* 重新拔插HDMI（此时rMBP仍为合上状态），外接显示器的字体问题即可解决。
* 如上步无效，则需要重启系统。

#### 独立使用外接显示器的方法：
* 电源适配器。
* 外置键盘、鼠标或触控板。
* 外置显示器。

#### 参考：
* http://support.apple.com/zh-cn/HT3131
* http://www.ireckon.net/2013/03/force-rgb-mode-in-mac-os-x-to-fix-the-picture-quality-of-an-external-monitor
* http://bbs.crsky.com/read.php?tid=2787662