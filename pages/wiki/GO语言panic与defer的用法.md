


#### 综述：
GO语言没有`try...catch`语法，但是可以使用`panic`配合`defer`进行异常的捕获。

#### panic
当程序执行到`panic`时，跳出当前的执行，直接抛出错误，如：

    package main

    import (
    	"errors"
    )
    
    func main() {
    
    	// new error
    	err := errors.New("This is a error message!")
    	// throw error
    	panic(err)
    }
    
    //输出
    panic: This is a error message!
    
    goroutine 16 [running]:
    runtime.panic(0x52c40, 0x1020e008)
    	/tmp/sandbox/go/src/pkg/runtime/panic.c:279 +0x120
    main.main()
    	/tmpfs/gosandbox-cbde2089_a189c41e_83fa48f6_7b16215a_fa87f3c6/prog.go:12 +0x120
    
    goroutine 17 [runnable]:
    runtime.MHeap_Scavenger()
    	/tmp/sandbox/go/src/pkg/runtime/mheap.c:507
    runtime.goexit()
    	/tmp/sandbox/go/src/pkg/runtime/proc.c:1445
    
    goroutine 18 [runnable]:
    bgsweep()
    	/tmp/sandbox/go/src/pkg/runtime/mgc0.c:1976
    runtime.goexit()
    	/tmp/sandbox/go/src/pkg/runtime/proc.c:1445
     [process exited with non-zero status]
    
#### defer
捕获任何引发panic的错误（defer最好建立在method的最开始位置），如：

    // manual
    package main
    
    import (
    	"errors"
    	"fmt"
    )
    
    func main() {
    	// try catch
    	defer func() {
    		if err := recover(); err != nil {
    			fmt.Print(err)
    		}
    	}()
    	// new error
    	err := errors.New("This is a error message!")
    	// throw error
    	panic(err)
    }
    
    // output
    This is a error message!
    
    // automatic
    package main
    
    import (
    	"fmt"
    )
    
    func main() {
    	// try catch
    	defer func() {
    		if err := recover(); err != nil {
    			fmt.Print(err)
    		}
    	}()
    	// new error
    	i := 1
    	arr := [1]int{0}
    	fmt.Print(arr[i])
    }
    
    // output
    runtime error: index out of range

