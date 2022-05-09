#### 优势
`babun`集成了`cygwin`与`oh-my-zsh`，尤其是后者，意味着如果你同时拥有Win + MAC双系统的话，可以使用`babun`统一不同的系统间的开发环境。

#### 下载
 <http://babun.github.io/>

#### 安装
* 解压缩到任意文件夹后，运行`install.bat`（需管理员权限）
* 也可以使用`/t "D:\target_folder"`的模式制定安装目录。
* 安装时如系统有安全防护等APP最好关闭。

#### 配置
* 安装完毕后，一般需要以下两个命令：
    * `babun check`（用于判断环境是否正确）
    * `babun update`(用于判断是否有新的更新包)

#### 默认根目录
`%userprofile%\.babun\cygwin\home\Kenshin`

#### 包管理
`babun`自带了叫做`pact`的包管理，但貌似比较弱...

#### babun常用配置

##### 常用插件
`autojump colored-man zsh_reload zsh-syntax-highlighting git git-flow ruby gem python pip node npm bower`

##### zsh-syntax-highlighting
```
cd ~/.oh-my-zsh/custom/plugins
git clone git://github.com/zsh-users/zsh-syntax-highlighting.git
plugins=( [plugins...] zsh-syntax-highlighting)
source ~/.zshrc or src
```

##### autojump
```
git clone git://github.com/joelthelion/autojump.git
cd autojump
./install.py
add
[[ -s ~/.autojump/etc/profile.d/autojump.sh ]] && . ~/.autojump/etc/profile.d/autojump.sh
to ~/.zshrc
```

##### Powerline-Shell
* 下载：
```
git clone https://github.com/milkbikis/powerline-shell
cd powerline-shell
./install.py
ln -s <path/to/powerline-shell.py> ~/powerline-shell.py
```
* 配置
```
# Add the following to your .zshrc:
 function powerline_precmd() {
     export PS1="$(~/powerline-shell.py  --cwd-max-depth 1 --cwd-only $? --shell zsh 2> /dev/null )"
}

function install_powerline_precmd() {
  for s in "${precmd_functions[@]}"; do
	if [ "$s" = "powerline_precmd" ]; then
	  return
	fi
  done
  precmd_functions+=(powerline_precmd)
}
install_powerline_precmd
```

* Powerline-Shell参数：(需要添加）
    * --cwd-only（只显示当前目录）
    * --cwd-max-depth 1（目录深度）
* powerline-shell/config参数：
> 去掉 'username', 'hostname',（为了节省显示的路径，改动config.py后，需要重新执行install.py）

* 参考：
	* <http://cenalulu.github.io/linux/mac-powerline/>
	* <https://github.com/milkbikis/powerline-shell>

#### cygwin常用开发环境配置

##### pip
cygwin自带的python没有pip，所以需要手动下载：`wget https://bootstrap.pypa.io/get-pip.py -O - | python`

##### ruby
> 由于使用`pact install rubygems`会出现错误，所以改用`rvm`方式。

* 参考
    * <http://lists.gnupg.org/pipermail/gnupg-users/2004-October/023592.html>
    * <https://github.com/babun/babun/issues/93>
    * <http://sourceforge.net/projects/gettext/>
    * <http://prdownloads.sourceforge.net/gettext/libiconv-1.9.1.bin.woe32.zip?download>
    * <http://xjlin0.github.io/tech/2015/04/14/babun-the-new-cygwin-for-ruby-rails-sinatra-and-nodejs/>

* Rvm
    * 依赖
        * gnupg
            *  `pact install gnupg`
            *  `curl http://prdownloads.sourceforge.net/gettext/libiconv-1.9.1.bin.woe32.zip?download`
            *  `unzip libiconv-1.9.1.bin.woe32.zip`
            *  copy `iconv.dll` to `%USERPROFILE%\AppData\Roaming\gnupg`
        * `pact install patch libyaml-devel libtool bison mingw64-i686-gcc-g++ mingw64-x86_64-gcc-g++ patch sqlite3`
    * 安装

    ```
    gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
    curl -sSL https://get.rvm.io | bash -s stable
    ```
    * 使用
        * `rvm install 1.9.3`（自带rubygems）
    * 注意：
        > rvm install 2.x.x 会出现类似`/psych.so (LoadError)`这样的错误。暂时不清楚如何解决，所有只能安装`1.x.x`。

#### gem
> 由于`rubygems.org`被墙，所以无法使用在线安装方式`gem install xxx`，可以先将*.gem下载，而后使用离线安装方式`gem install --local <path/to/xxx.gem>`

##### github
* 自带版本2.1.4
* 与github的使用与其他系统类似，使用`ssh-keygen -t rsa -C "xxx@gmail.com"`生成密匙。
* 使用`ssh -T git@github.com`测试连接。
* **注意有可能出现如下错误：**
    `Permissions 0644 for '/x/xx/xxx/.ssh/id_rsa' are too open`
    * 解决办法：`chmod 0600 ~/.ssh/id_rsa`
    * 参考：
        * <https://github.com/babun/babun/issues/208>
        * <http://www.cnblogs.com/rubytim/p/3393035.html>
        * <http://blog.sina.com.cn/s/blog_6db040920100thy0.html>
        * <http://blog.csdn.net/johnnywww/article/details/8667168>

##### git-flow
```
curl -OL https://raw.github.com/nvie/gitflow/develop/contrib/gitflow-installer.sh
$ chmod +x gitflow-installer.sh
$ sudo ./gitflow-installer.sh
```

##### git-extras
```
git clone --depth 1 https://github.com/tj/git-extras.git
cd git-extras
sudo make install
```

##### cloc
```
curl -O http://softlayer-dal.dl.sourceforge.net/project/cloc/cloc/v1.62/cloc-1.62.tar.gz
tar -zxvf cloc-1.62.tar.gz 
cd cloc
sudo make install
```

##### httpie
* Site <https://github.com/jakubroztocil/httpie>
* Install `pip install --upgrade httpie`
* Usage 
```
http http://cn.bing.com/HPImageArchive.aspx\?format\=js\&idx\=13\&n\=1
```

##### cheat
* Site <https://github.com/chrisallenlane/cheat>
* Install `pip install cheat`
* Usage `cheat xxx`

##### icdiff
* Site <http://www.jefftk.com/icdiff>
* Install
```
git clone git@github.com:jeffkaufman/icdiff.git "icdiff-source"
n -s <path/icdiff/icdiff> ~/icdiff
sudo <path/icdiff/git-icdiff> /usr/local/bin
```
* Usage
```
git difftool --extcmd icdiff
git icdiff xxx yyy
```

#### 将Babun加入到ConEmu
* Update to the latest ConEmu
* In ConEmu
    * Go to Settings>Startup>Tasks
    * Create a new task
        * Task parameters `/icon "%userprofile%\.babun\cygwin\bin\mintty.exe" /dir "%userprofile%"`
        * `Commands %userprofile%\.babun\cygwin\bin\mintty.exe -`
* .minttyrc
```
CursorType=block
Term=xterm-256color
Font=Droid Sans Mono
FontHeight=10
```

#### 常见错误
##### compdef: unknown command or service: git（同样，我的环境不好使）
```
$ compinit
$ cp .zcompdump .zcompdump-$HOSTNAME-5.0.2
```