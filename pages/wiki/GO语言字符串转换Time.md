#### 注意：
GO语言的时间节点/模板以`Mon Jan 2 15:04:05 MST 2006  (MST is GMT-0700)`为初始节点。

#### 代码：
    package main
    
    import (
    	"fmt"
    	"time"
    )
    
    func main() {
        // example 1
    	const TIMEFORMART = "02-Jan-2006 15:04"
    	sTime := "23-Aug-2013 21:14"
    	t, _ := time.Parse(TIMEFORMART, sTime)
    	fmt.Println(t)
    
        // example 2
    	value := "Thu, 05/19/11, 10:47PM"
    	layout := "Mon, 01/02/06, 03:04PM"
    	t2, _ := time.Parse(layout, value)
    	fmt.Println(t2)
    }
    
    // output
    2013-08-23 21:14:00 +0000 UTC
    2011-05-19 22:47:00 +0000 UTC

