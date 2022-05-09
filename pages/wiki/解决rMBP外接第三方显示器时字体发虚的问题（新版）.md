

#### 现象

> 当 Mac OS 升级到 10.13.x 时，在 10.9 下已经解决的问题，又重复性出现。



#### 解决方案

1. 更换 HDML 为 DP 线；( **重要** )

2. 下载 [RMD 2.3.1](https://github.com/usr-sse2/RDM)

3. 关闭 System Integrity Protection( 又称为 rootless )

4. 重启 macOS，按住`CMD＋R`进入恢复模式

5. 选择 Utilities 菜单，打开终端 Terminal

6. 输入 `csrutil disable` 成功的话会提示 `Successfully disabled System Integrity Protection` 的字样

7. 重启

> 之后主要操作是让外接显示器支持 HiDPI

8. 管理员权限运行下方的命令开启本机的 HiDPI 选项
   `sudo defaults write /Library/Preferences/com.apple.windowserver.plist DisplayResolutionEnabled -bool true`

9. 备份 `/System/Library/Displays/Contents/Resources/Overrides` 

10. 有 **三种方式** _不同的方式均有人测试成功，但我只在 **第一种方式** 下成功_

  1. https://github.com/syscl/Enable-HiDPI-OSX 方案：
     - donwload `curl -o ~/enable-HiDPI.sh https://raw.githubusercontent.com/syscl/Enable-HiDPI-OSX/master/enable-HiDPI.sh`
     - chmod `chmod +x ~/enable-HiDPI.sh`
     - run `~/enable-HiDPI.sh`
     - 重新拔插 HDMI / DP 线（此时 rMBP 仍为合上状态）
  2. patch-edid.rb 方案
     - `cd downloads`
     - `curl -L https://gist.githubusercontent.com/adaugherity/7435890/raw/5af7e8f7ebef354037b9be39de90b2149b84fec1/patch-edid.rb -o patch patch-edid.rb`
     - `ruby patch-edid.rb`
     - 将会在`downloads`文件夹下生成一个类似`DisplayVendorID-XXXX`的文件夹。
     - 拷贝此文件夹到`/System/Library/Displays/Overrides`，需要使用`sudo权限`。（如果有覆盖，请先备份）
     - 重新拔插 HDMI / DP 线
  3. [SCALED RESOLUTIONS FOR YOUR MACBOOKS EXTERNAL MONITOR](https://comsysto.github.io/Display-Override-PropertyList-File-Parser-and-Generator-with-HiDPI-Support-For-Scaled-Resolutions/) 方案：
     - 打开上述网页，根据步骤操作，已描述很详细了，从略
     - 下载  `DisplayProductID-*.plist`
     - 生成对应文件夹并复制到 `/System/Library/Displays/Overrides` 下
     - 重新拔插 HDMI / DP 线
11. 外接显示器字体发虚改善后，进入恢复模式，启用 `csrutil enable` 后重启



#### 重要

> 无论上述哪种步骤，都需要留意以下几点：

- 需要强制打开 `csrutil disable`

- 其原理都是生成 `DisplayVendorID-xxx` 文件夹，并复制到 `/System/Library/Displays/Overrides` 到下面

- 利用 RDM 2.3.1 让外接显示器强制使用 HiDPI 分辨率

- 如果设置成功后，会在 系统偏好设置 → 显示器中看到类似如外接显示器的色彩方案名称，如下图：

  ![Jietu20181003-143535.jpg](https://i.loli.net/2018/10/03/5bb463417434b.jpg)

#### 参考

- [Mac High Sierra外接显示器设置（解决字体模糊问题，开启high dpi）](https://yanke.info/?id=74)
- [Mac系统HiDPI问题](https://www.jianshu.com/p/30e6f84ffce8)
- [可能是目前解决 Mac 外接显示器字体发虚的最好方法](https://www.jianshu.com/p/6274253b78d8)
- [macOS 外接显示器字体画面模糊虚化已解决](https://www.jianshu.com/p/8fe41f43c4c2)
- [解决rMBP外接第三方显示器时字体发虚的问题](http://wiki.k-zone.cn/post/wiki/jie-jue-rmbpwai-jie-di-san-fang-xian-shi-qi-shi-zi-ti-fa-xu-de-wen-ti)
- RDM 2.3.1 下载地址 → [RDM](https://github.com/usr-sse2/RDM)
- SwitchResX 的参考出处 → <https://blog.xingoxu.com/2016/12/config-switchresx-and-2khidpi/>