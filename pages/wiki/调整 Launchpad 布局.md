#### 调整 Launchpad 布局
Launchpad 默认布局是 5 * 7，在终端中输入如下代码：
```
defaults write com.apple.dock springboard-columns -int 8; 
defaults write com.apple.dock springboard-rows -int 5; 
defaults write com.apple.dock ResetLaunchPad -bool TRUE; 
killall Dock
```
调整 其中的 `columns` 与 `rows` 对应的值即可。
#### 参考：
<http://mp.weixin.qq.com/s?__biz=MzA4NTMxOTgxNg==&mid=2649882683&idx=1&sn=a611eb5e9ff29760fa997661e7bbf4f2&scene=1&srcid=0525WSJSTGVKqy7R4zhCmf5L#rd>