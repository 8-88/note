#### 代码：
    package main
    
    import "fmt"
    
    func main() {
    	timer := time.NewTicker(2 * time.Second)
    	for {
    		select {
    		case <-timer.C:
    			go func() {
    				log.Println(time.Now())
    			}()
    		}
    	}
    }
