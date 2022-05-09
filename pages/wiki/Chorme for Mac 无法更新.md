由于 `GoogleSoftwareUpdate` 造成，解决办法如下：

* 更新失败（错误：11）
  
  > if the `install.py` file is not found, you can try running `ksinstall` the following command instead:
  
  * `sudo /Library/Google/GoogleSoftwareUpdate/GoogleSoftwareUpdate.bundle/Contents/Resources/GoogleSoftwareUpdateAgent.app/Contents/Resources/install.py --uninstall`
  * `sudo /Library/Google/GoogleSoftwareUpdate/GoogleSoftwareUpdate.bundle/Contents/Resources/GoogleSoftwareUpdateAgent.app/Contents/Resources/ksinstall --uninstall`
  * `rm -f /Library/Google/GoogleSoftwareUpdate`
  * reboot Mac.


* 更新失败（错误：12）
  * `sudo cd /Library/Caches`
* 参考：
  * <http://applehelpwriter.com/2014/07/13/how-to-remove-googles-secret-update-software-from-your-mac/>
  * <https://raam.org/2008/howto-remove-google-software-update-on-mac-os-x/>
  * <http://blog.sina.com.cn/s/blog_6f76f8450100ofct.html>
  * <http://zh.wikihow.com/%E6%9B%B4%E6%96%B0%E8%B0%B7%E6%AD%8CChrome%E6%B5%8F%E8%A7%88%E5%99%A8>
  * <https://productforums.google.com/forum/#!topic/chrome/8eY9TuO0ogw>
  * <https://www.google.com/chrome/cleanup-tool/index.html>

