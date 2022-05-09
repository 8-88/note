GO语言中没有直接的copy命令，但可以利用`exec`与`io pakcage`来实现。

#### go api
    func copy(src, dest string) error {
    	srcFile, errSrc := os.Open(src)
    	if errSrc != nil {
    		return errSrc
    	}
    	defer srcFile.Close()
    
    	dstFile, errDst := os.OpenFile(dest+DIVIDE+NODE, os.O_WRONLY|os.O_CREATE, 0644)
    	if errDst != nil {
    		return errDst
    	}
    	defer dstFile.Close()
    
    	_, err := io.Copy(dstFile, srcFile)
    
    	return err
    }
    
#### exec（调用系统的copy命令）
`_, err := exec.Command("cmd", "/C", "copy", "/y", src, dest).Output()`

#### 注意：
利用`go api`时，偶尔会出现被覆盖文件进程占用的情况。