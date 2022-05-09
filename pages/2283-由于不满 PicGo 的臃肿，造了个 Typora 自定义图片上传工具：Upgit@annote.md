title::  由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit

# MetaDate
	- Origin
		- [www.appinn.com](https://www.appinn.com/upgit/)
	- Date
		- 2022年01月31日 10:47:48
	- Desc
		- Upgit 是一款可以将任意文件上传至 GitHub 并能与 Typora 整合使用的命令行小工具，支持 macOS、Linux 与 Windows，可以把它当作 Typora 自定义图片上传工具，也可以用来保存文件到 GitHub。@Appinn
	- Tags
		- [[生产力工具/Typora]]  [[使用技巧/Github]]  [[图床]]
	- Backlinks
		-
	- Reference
		-
# Annoations

collapsed:: false
	- #+BEGIN_QUOTE
	    ### 特点：
	  
	  *   支持 Typora
	  *   支持上传任意文件
	  *   支持剪贴板上传
	  *   支持链接以 Markdown 形式保存到剪贴板
	  *   配合 AHK 食用效果更佳~
	  *   支持 Windows/Linux/macOS
	  *   体积小，5 MiB 左右无运行时
	  *   仅支持 Github
	  *   自定义重命名规则
	  *   支持 CDN 替换
	  *   完全开源 
	    #+END_QUOTE
	    collapsed:: true
		- Note
			- #+BEGIN_QUOTE
			   
			  #+END_QUOTE
		- Tags
			-
		- External reference
			-
		- Association
			- #+BEGIN_QUOTE
			  
			  #+END_QUOTE
			- [内部链接](<http://localhost:7026/reading/2283?title=由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit#id=1643865960989>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2283?title=由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit#id=1643865960989>)
			  collapsed:: false
	- #+BEGIN_QUOTE
	    程序所在文件夹内 
	    #+END_QUOTE
	    collapsed:: true
		- Note
			- #+BEGIN_QUOTE
			  1. 从 https://github.com/pluveto/upgit/releases 下载对应的文件
			  2. 下载完毕后，复制到任意文件夹，并改名为 `upgit`
			  3. 通过命令行进入此文件夹，并赋予 `chmod +x  ./upgit` 权限。 
			  #+END_QUOTE
		- Tags
			-
		- External reference
			-
		- Association
			- #+BEGIN_QUOTE
			  
			  #+END_QUOTE
			- [内部链接](<http://localhost:7026/reading/2283?title=由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit#id=1643866272765>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2283?title=由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit#id=1643866272765>)
			  collapsed:: false
	- #+BEGIN_QUOTE
	    ```
	  # branch = "master"
	  # Get token from https://github.com/settings/tokens
	  pat = "ghp_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
	  rename = "{year}/{month}/upgit_{year}{month}{day}_{unix_ts}{ext}"
	  repo = "repo-name"
	  username = "username"
	  
	  # [replacements]
	  # "raw.githubusercontent.com" = "cdn.jsdelivr.net/gh"
	  # "/master" = "@master"
	  ``` 
	    #+END_QUOTE
	    collapsed:: true
		- Note
			- #+BEGIN_QUOTE
			   
			  #+END_QUOTE
		- Tags
			-
		- External reference
			-
		- Association
			- #+BEGIN_QUOTE
			  
			  #+END_QUOTE
			- [内部链接](<http://localhost:7026/reading/2283?title=由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit#id=1643865907387>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2283?title=由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit#id=1643865907387>)
			  collapsed:: false
	- #+BEGIN_QUOTE
	    ![](https://img3.appinn.net/static/wp-content/uploads/2022/01/Screen-Appinn2022-01-30_17_22_43.jpg) 
	    #+END_QUOTE
	    collapsed:: true
		- Note
			- #+BEGIN_QUOTE
			   
			  #+END_QUOTE
		- Tags
			-
		- External reference
			-
		- Association
			- #+BEGIN_QUOTE
			  
			  #+END_QUOTE
			- [内部链接](<http://localhost:7026/reading/2283?title=由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit#id=1643865915038>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2283?title=由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit#id=1643865915038>)
			  collapsed:: false
	- #+BEGIN_QUOTE
	    直接在**命令**处输入 upgit 所在路径，比如 Windows 下输入 “c:\upgit\upgit.exe”，macOS 下输入 “/upgit_macos_amd64″，请根据实际情况修改。 
	    #+END_QUOTE
	    collapsed:: true
		- Note
			- #+BEGIN_QUOTE
			   
			  #+END_QUOTE
		- Tags
			-
		- External reference
			-
		- Association
			- #+BEGIN_QUOTE
			  
			  #+END_QUOTE
			- [内部链接](<http://localhost:7026/reading/2283?title=由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit#id=1643866376155>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2283?title=由于不满 PicGo 的臃肿，造了个 Typora 自定义图片上传工具：Upgit#id=1643866376155>)