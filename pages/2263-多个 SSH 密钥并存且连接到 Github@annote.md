title::  多个 SSH 密钥并存且连接到 Github

# MetaDate
	- Origin
		- [kangzhiheng.top](https://kangzhiheng.top/post/11-more-ssh-in-one-laptop/)
	- Date
		- 2022年01月25日 19:25:15
	- Desc
		- 在这篇文章中，使用 Git 服务器 Github，来进行多 SSH 密钥的配置，介绍多个 SSH 密钥同时存在于同一台设备中的方法。
	- Tags
		- [[开发技巧/GIt]]
	- Backlinks
		-
	- Reference
		-
# Annoations

collapsed:: false
	- #+BEGIN_QUOTE
	    ```
	  vim ~/.ssh/config
	  ``` 
	    #+END_QUOTE
	    collapsed:: true
		- Note
			-
		- Tags
			-
		- External reference
			-
		- Association
			- #+BEGIN_QUOTE
			  
			  #+END_QUOTE
			- [内部链接](<http://localhost:7026/reading/2263?title=多个 SSH 密钥并存且连接到 Github#id=1643267473446>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2263?title=多个 SSH 密钥并存且连接到 Github#id=1643267473446>)
			  collapsed:: false
	- #+BEGIN_QUOTE
	    ```
	  Host github.com
	      HostName github.com
	      User git
	      PreferredAuthentications publickey
	      IdentityFile ~/.ssh/id_rsa_normal_github
	  
	  Host adoredee.github.com
	      HostName github.com
	      User git
	      PreferredAuthentications publickey
	      IdentityFile ~/.ssh/id_rsa_hugo_github
	  ``` 
	    #+END_QUOTE
	    collapsed:: true
		- Note
			-
		- Tags
			-
		- External reference
			-
		- Association
			- #+BEGIN_QUOTE
			    > ```
			     Host git@github2.com   #此处可以随意指定
			     HostName github.com
			     User git
			     Port 22
			     IdentityFile ~/.ssh/id_rsa2   #你新生成的SSH名字```
			     > 
			     > [[在 GitHub 多个账号上使用不同的 SSH 的配置方法]]
			  
			  #+END_QUOTE
			- [内部链接](<http://localhost:7026/reading/2263?title=多个 SSH 密钥并存且连接到 Github#id=1643267475431>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2263?title=多个 SSH 密钥并存且连接到 Github#id=1643267475431>)