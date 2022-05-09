#### 语法：
    // {gopath}/aaa/bbb/bbb.go
    "aaa/bbb"
	
	// 通常写法，调用util.XXX()
	"gnvm/util"

    // 自动执行gnvm/command中的INIT方法，不用特意调用command.XXX()
	_ "gnvm/command"
	
	// 忽略github.com/Kenshin/cprint的前缀，如P(WARING, "xxx")
	. "github.com/Kenshin/cprint"
	
	// 别名，如P.println()
	P "fmt"