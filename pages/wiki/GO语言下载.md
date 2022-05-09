#### 代码：
    package main
    
    import (
    	"fmt"
    	"net/http"
    	"os"
    )
    
    func main() {
    	// get res
    	res, err := http.Get("http://dist.u.qiniudn.com/latest/x64/node.exe")
    
    	// close
    	defer res.Body.Close()
    
    	// err
    	if err != nil {
    		panic(err)
    	}
    
    	// check state code
    	if res.StatusCode != 200 {
    		fmt.Printf("Downlaod error occurred, please check. See 'gnvm config help'.\n", res.StatusCode)
    	}
    
    	// create file
    	file, createErr := os.Create(os.TempDir() + "\\" + "node.exe")
    	if createErr != nil {
    		fmt.Println("Create file error, Error: " + createErr.Error())
    	}
    	defer file.Close()
    
    	fmt.Printf("Start download node.exe from %v\n", os.TempDir())
    
    	// loop buff to file
    	buf := make([]byte, res.ContentLength)
    
    	for {
    		n, err := res.Body.Read(buf)
    
    		// write complete
    		if n == 0 && err.Error() == "EOF" {
    			fmt.Println("End download.")
    			break
    		}
    
    		//error
    		if err != nil && err.Error() != "EOF" {
    			panic(err)
    		}
    
    		file.WriteString(string(buf[:n]))
    	}
    
    	// valid download exe
    	fi, err := file.Stat()
    	if err == nil {
    		if fi.Size() != res.ContentLength {
    			fmt.Printf("Error: Downlaod node.exe version size error '.\n")
    		}
    	}
    }
