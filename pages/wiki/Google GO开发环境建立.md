### 运行环境：

#### 下载：
* <https://code.google.com/p/go/downloads/list>

#### 配置环境变量：
<pre>
# set GOROOT
set GOROOT=F:\kenshin\DevTools\go
set path=%path%;%GOROOT%/bin

# create go work folder
> mkdir 28-GO\01-work
> mkdir src & pkg & bin

# set GOPATH
set GOPATH=F:\kenshin\Work\28-GO\01-work\gnode
set path=%path%;%GOPATH%

# set GOBIN，只有设置了GOBIN，才能使用go install
set GOBIN=%GOPATH%\bin
set path=%path%;%GOBIN%
</pre>

#### 查看当前go的各个参数：
`go env`

#### 比较重要的几个环境变量：
* `GOROOT` # go的目录
* `GOPATH` # 当前项目对应的目录
* `GOBIN`  # 当前项目对应的编译目录（当使用go install时，需要设置此目录）

### 开发环境：（Sublime Text 3）
* 配置Package Controll
* 安装`GoSublime` #最新版本以及包含了GO build

#### 验证：
* 用ST3打开*.go，如果可以看到语法高亮，说明配置完毕。

#### 使用：
* `ctrl + b` #打开控制台，然后可以输入GO的任意指令，如`go run xxx`

### 开发环境：（LiteIDE）

#### 下载：
* <https://code.google.com/p/liteide/>

#### 安装：
* 解压到任意文件夹。
* 运行{LiteIDE}\bin\liteide.exe

