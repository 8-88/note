#### 下载：

* Windows：
  * <https://sourceforge.net/projects/mingw-w64/files/External%20binary%20packages%20(Win64%20hosted)/gdb/>
* MAC：
  * `brew install gdb`

#### 使用：

* 编译：
  *  `go build -gcflags "-N -l"` - 编译，关闭内联优化。


* 运行：
  * `gdb`

#### 常用命令：

* `run` - 运行。 
* `b` - 设置断点，例如：关联文件的行号中、**GOPATH**里的文件的行号或一个包里的函数等。
  * `b github.com/bfosberry/gdb_sandbox/main.go:20`  - 设置 github.com/xxx/main.go 第20行 为断点。
  * `b 'main.main'`  - 设置 man.go 中的 main() 为断点。
  * b `nodehandle.go:20` - 设置 nodehandler.go 第20行 为断点。
  * `b 20` - 设置  第20行，为断点。
* `l` - 默认显示10行的源码，后面可以加 num，例如： l 15 ( 显示第15行，包括前后10行的内容 ) 
* `d` - 删除断点， 序号可以通过 `info breakpoints` 获取，后面没有参数的话，删除全部断点。
* `info` - 显示信息。
  * `locals` - 显示当前执行的程序中的变量值。
  * `breakpoints` - 显示当前设置的断点列表。
  * `goroutines` - 显示当前执行的goroutine列表。
* `p` - 用来打印变量或者其他信息，后面跟上需要打印的变量名。 
* `whatis` - 显示当前变量的类型，例如： `whatis xxx`
* `n` - 用来单步调试，跳到下一步，当有断点之后，可以输入`n`跳转到下一步继续执行。
* `c` - 用来跳出当前断点处，后面可以跟参数N，跳过多少次断点。
* `set variable` - 该命令用来改变运行过程中的变量值，格式如：`set variable xxx=yyy`

#### 其它工具：

* `hopwatch` - <https://github.com/emicklei/hopwatch>
* `beewatch` - <https://github.com/beego/beewatch>

#### 参考：

* <http://www.gnu.org/software/gdb/>
* <https://github.com/astaxie/build-web-application-with-golang/blob/master/zh/11.2.md>
* <http://www.open-open.com/lib/view/open1439650114379.html>
* <http://www.cnblogs.com/ztiandan/archive/2013/01/11/2856145.html>
* <http://blog.studygolang.com/2012/12/gdb%E8%B0%83%E8%AF%95go%E7%A8%8B%E5%BA%8F/>