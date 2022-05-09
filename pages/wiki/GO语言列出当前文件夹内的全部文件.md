#### 代码：
	err := filepath.Walk(rootPath, func(dir string, f os.FileInfo, err error) error {

		// check nil
		if f == nil {
			return err
		}

		// check dir
		if f.IsDir() == false {
			return nil
		}

        // print file name
		fmt.Println(f.Name())

		// return
		return nil
	})