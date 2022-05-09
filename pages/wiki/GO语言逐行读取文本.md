#### 代码：
    package main
    
    import (
    	"bufio"
    	"fmt"
    	"net/http"
    	"io"
    )
    
    func main() {
    
    	// get
    	res, err := http.Get("http://www.k-zone.cn/gnvm/version.txt")
    	if err != nil {
    		return
    	}
    	// close
    	defer res.Body.Close()
    
    	// set buff
    	buff := bufio.NewReader(res.Body)
    
    	for {
    		// set line
    		line, err := buff.ReadString('\n')
    
    		// when EOF or err break
    		if err != nil || err == io.EOF {
    			break
    		}
    
    		fmt.Println(line)
    	}
    }
