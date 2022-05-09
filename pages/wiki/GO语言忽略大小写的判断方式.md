用`strings.EqualFold`判断是忽略大小写的，如判断"all"与"ALL"返回为`true`。如果要返回为`false`的话，使用下面的方式：

#### 代码：
    func EqualAbs(key, value string) bool {
    	if !strings.EqualFold(value, key) {
    		return false
    	} else if strings.EqualFold(value, key) && value != key {
    		return false
    	}
    	return true
    }
    
    // use
    fmt.Print(EqualAbs("ALL", "all"))
