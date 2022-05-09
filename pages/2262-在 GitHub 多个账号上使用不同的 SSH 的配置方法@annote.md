title::  在 GitHub 多个账号上使用不同的 SSH 的配置方法

# MetaDate
	- Origin
		- [cuiqingcai.com](https://cuiqingcai.com/495.html)
	- Date
		- 2022年01月25日 19:25:00
	- Desc
		- 现在遇到这么一个情况，在我电脑上配置了一对 SSH 秘钥，其中公钥已经添加到了我的 GitHub 上面。
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
	  ssh-keygen -t rsa -C '1016903103@qq.com'
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
			- [内部链接](<http://localhost:7026/reading/2262?title=在 GitHub 多个账号上使用不同的 SSH 的配置方法#id=1643267512933>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2262?title=在 GitHub 多个账号上使用不同的 SSH 的配置方法#id=1643267512933>)
			  collapsed:: false
	- #+BEGIN_QUOTE
	    ```
	  Generating public/private rsa key pair.
	  Enter file in which to save the key (~/.ssh/id_rsa): ~/.ssh/id_rsa2 #这里输入一个新的ssh key文件名
	  ``` 
	    #+END_QUOTE
	    collapsed:: true
		- Note
			- -  留意 id_rsa2 需要绝对路径
		- Tags
			-
		- External reference
			-
		- Association
			- #+BEGIN_QUOTE
			  
			  #+END_QUOTE
			- [内部链接](<http://localhost:7026/reading/2262?title=在 GitHub 多个账号上使用不同的 SSH 的配置方法#id=1643267514889>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2262?title=在 GitHub 多个账号上使用不同的 SSH 的配置方法#id=1643267514889>)
			  collapsed:: false
	- #+BEGIN_QUOTE
	    ```
	  Host git@github2.com   #此处可以随意指定
	  HostName github.com
	  User git
	  Port 22
	  IdentityFile ~/.ssh/id_rsa2   #你新生成的SSH名字
	  ``` 
	    #+END_QUOTE
	    collapsed:: true
		- Note
			- -  此处的结构应该改为引用时提到的方式，即下方是正确的。
		- Tags
			-
		- External reference
			-
		- Association
			- #+BEGIN_QUOTE
			    > ```
			     Host github.com
			         HostName github.com
			         User git
			         PreferredAuthentications publickey
			         IdentityFile ~/.ssh/id_rsa_normal_githubHost adoredee.github.com
			         HostName github.com
			         User git
			         PreferredAuthentications publickey
			         IdentityFile ~/.ssh/id_rsa_hugo_github
			     ```
			     > 
			     > [[多个 SSH 密钥并存且连接到 Github]]
			  
			  #+END_QUOTE
			- [内部链接](<http://localhost:7026/reading/2262?title=在 GitHub 多个账号上使用不同的 SSH 的配置方法#id=1643267557067>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2262?title=在 GitHub 多个账号上使用不同的 SSH 的配置方法#id=1643267557067>)
			  collapsed:: false
	- #+BEGIN_QUOTE
	    ```
	  git@github2.com:cqcre/shiyida.git
	  ``` 
	    #+END_QUOTE
	    collapsed:: true
		- Note
			- -  相当于「别名」
		- Tags
			-
		- External reference
			-
		- Association
			- #+BEGIN_QUOTE
			  
			  #+END_QUOTE
			- [内部链接](<http://localhost:7026/reading/2262?title=在 GitHub 多个账号上使用不同的 SSH 的配置方法#id=1643267549215>) |  [外部链接](<https://simpread.pro/@kenshin/reading/2262?title=在 GitHub 多个账号上使用不同的 SSH 的配置方法#id=1643267549215>)