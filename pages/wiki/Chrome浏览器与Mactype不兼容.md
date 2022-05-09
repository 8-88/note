#### 原因：
* 由于Chrome在41和之后的版本中强制启用了对标签栏和菜单的DirectWrite渲染。
* Mactype渲染和Chrome浏览器的DirectWrite是互斥的，如果要使用Mactype就需要停用后者。

#### 解决：
```
chrome://flags/#disable-direct-write
选择停用，然后重启Chrome即可。
```

#### 参考：
* <http://bbs.kafan.cn/thread-1840015-1-1.html>