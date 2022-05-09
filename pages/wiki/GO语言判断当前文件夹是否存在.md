#### 代码：
    func isDirExist(path string) bool {
    	_, err := os.Stat(path)
    	if err != nil {
    		return os.IsExist(err)
    	} else {
    		// return file.IsDir()
    		return true
    	}
    }
