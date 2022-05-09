#### 语法：
`string(out[:])`

	out, err := exec.Command("node", "--version").Output()
	if err == nil {
		fmt.Println(string(out[:]))
	}
