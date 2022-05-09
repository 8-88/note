### GO 配置：

#### 下载：
* <https://golang.org/dl/>

#### 环境变量：
```
# create go work folder
> mkdir GO
> mkdir src & pkg & bin

# set GOROOT
set GOROOT=F:\kenshin\DevTools\go
set path=%path%;%GOROOT%\bin

# set GOPATH
set GOPATH=F:\kenshin\Work\28-GO\01-work\src
set path=%path%;%GOPATH%

# set GOBIN
set GOBIN=%GOPATH%\bin
set path=%path%;%GOBIN%
```

#### 查看当前 go 环境变量：
* `go env`

#### 比较重要的几个环境变量：
* `GOROOT` - go的目录
* `GOPATH` - 当前项目对应的目录（包括：`src` `pkg` `bin` 的根目录）
* `GOBIN`  - go.exe 执行目录

### 工具：

- `gocode` - `go get -u github.com/nsf/gocode ` - 提供代码补全
- `godef` - `go get -u github.com/rogpeppe/godef` - 代码跳转
- `gofmt` - `go get -u golang.org/x/tools/cmd/goimports` - 代码自动整理
- `golint`- `go get -u github.com/golang/lint/golint` - 语法检查
- `goimport` - `go get -u golang.org/x/tools/cmd/goimports` - 自动整理 imports
- **注意：** 由于某些已知原因，无法使用  `go get golang.org/x/...`  时，可以使用以下两种方式：
  - `http://golangtc.com/download/package`
  - `http://gopm.io/`
  - 将下载的包，放到 `%GOPATH%\src\` 并解压缩，执行 `go install` ，如： `go install golang.org/x/tools/cmd/goimports` 即可。

### 开发环境：（ Sublime Text 3 ）
* 配置 <http://wiki.k-zone.cn/post/wiki/sublime-text-3-chang-yong-pei-zhi>
* `GoSublime`
  * 配置 `Preferences -> Package Settings -> GoSublime ->　Settings - User`

    ```
    {
     "env": {
         "GOROOT": "D:\\DevTools\\go\\go-1.5.3",
         "GOBIN":  "%GOROOT%\\bin",
         "GOPATH": "D:\\Work\\GO",
         "PATH": "%PATH%;%GOROOT%;%GOBIN%;%GOPATH%\\bin"
     }
    }
    ```

  >  如果是 Linux 系统，将`\\`替换为`/`

  * 使用
    > 连续两次输入`Ctrl + dot(.)`, 可以查看 `GoSublime` 的功能和快捷键。

* `Godef`
  *  `Preferences -> Package Settings -> GoDef ->　Settings - User`

     ```
     {
     "goroot": "D:\\DevTools\\go\\go-1.5.3",
     "gopath": "D:\\Work\\GO\\src",
     }
     ```

  > 如果是 Linux 系统，将`\\`替换为`/`

  * 跳转快捷键 `gd`

#### 验证：
* 用 `ST3` 新建 `hello.go`，如果可以看到语法高亮，并有智能提示。

#### 使用：
* 选中 `Tools -> Build System -> GoSublime`
* `ctrl + b` - 打开控制台。
* `go run hello.go`

### 开发环境：（ Atom ）

* `go-plus` - <https://atom.io/packages/go-plus>
  *  `apm install go-plus` or `Preferences > Install > go-plus`
* `Preferences`
  * `Packages > Go Plus > Settings`
    * GOPATH - `required`
    * Go Installation Path - `required`

### 开发环境：（LiteIDE）

#### 下载：
* <https://github.com/visualfc/liteide>

#### 安装：
* 解压到任意文件夹。
* 运行 `{LiteIDE}\bin\liteide.exe`

### 参考：

* <http://blog.wiseturtles.com/posts/go-ide.html>
* <https://godoc.org/golang.org/x/tools>
* <https://github.com/golang/tools>
* <http://golanghome.com/post/126>
* <http://www.jianshu.com/p/843c3b99e8fa>
* <http://studygolang.com/articles/2731>
* <https://golang.org/doc/gdb>
* <http://www.philo.top/2015/02/06/golang-%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE%E5%BB%BA%E8%AE%AE/>