#### 注册/登录：
进入<https://travis-ci.org/>，并使用github.com帐号登录即可。

### 使用：（其他过程略，可以看官网）
进入<https://travis-ci.org/profile/{github.com的用户名}>直接选择打开即可。

![travis-cl](http://i.imgur.com/WIXRyu5.png)

#### 建立.travis.yml
在选中的repo根目录建立此文件，具体语法可以看官网。

### 生效
只要push根目录包含有`.travis.yml`到github后，自动生效。

#### 由于travis直接将github.com上面的内容clone到本地，所以当*.go中出现import本地file的时候，会发生如下错误：
    cannot find package "gnvm/command" in any of:
    /home/travis/.gvm/gos/go1.2.2/src/pkg/gnvm/command (from $GOROOT)
	/home/travis/gopath/gnvm/src/gnvm/command (from $GOPATH)

#### 解决方法：
    # 复制$TRAVIS_BUILD_DIR（$HOME/gopath/src/github.com/Kenshin/gnvm）所有内容到 $HOME/gopath/src根目录
    - cp -r  $TRAVIS_BUILD_DIR $HOME/gopath/src
    # 进入此目录
    - cd $HOME/gopath/src/gnvm
    # 可选（只是用来查看是否成功复制到此目录下）
    - ls -a -l
    # 可选（如果翻译文件有需要直接可执行文件，则直接放到PATH里面。）
    - export PATH=$PATH:/home/travis/gopath/bin

#### 适配GO的.travis.yml
    language: go
    
    go:
      - 1.2.2
    
    before_install:
      - cp -r  $TRAVIS_BUILD_DIR $HOME/gopath/src
      - cd $HOME/gopath/src/gnvm
      - ls -a -l
      - export PATH=$PATH:/home/travis/gopath/bin
    
    install:
      - go get -d -v ./...
      - go run gnvm.go version
    
    notifications:
      email: false


