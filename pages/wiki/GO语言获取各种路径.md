#### 获取某个执行文件的路径，如node.exe
`file, err := exec.LookPath("node.exe")`

#### 获取CLI当前所处的路径
`path, err := os.Getwd()`