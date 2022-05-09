###Google Go学习笔记

####命名规约：
* GO采用驼峰命名方式。
* GO没有public | private 等关键词，凡是__小写变量（首字母）__均为包内可见。
* GO没有public | private 等关键词，凡是__大写变量（首字母）__均为public类型。

####一些有意思的地方：
* GO语言没有使用;（分号）作为一个语句的结束。
* GO语言语句的结束以“回车”代替。
* GO语言的{}没有类似Java的多变形式，GO语言只允许一种形式，即：
<pre>
//正确并唯一的方式：
func test() {
    //TO DO
}
//错误的方式1：
func test() { }
//错误的方式2：
func test()
{
    //TO DO
}
</pre>
* GO语言默认有两个方法，init() 和 main()，其中main()必须要跟package main放在一起使用，如：
<pre>
package main
import "fmt"
func main() {
    fm.Println("hello world!")
}
</pre>
* 分组声明：
<pre>
import (
    "fmt"
    "os"
)
var (
    i int = 0
    j string = “test”
)
const （
    Pi = 3.1415926
)
</pre>
* GO语言内置了三种预定义变量：true、false、iota

####变量类型：（简单数据类型）
* 布尔类型：bool
* 整型：int8, byte, int16, int, uint, uintptr
* 浮点类型：float16, float32
* 复数类型：complex64, complex128
* 字符串类型：string
* 错误类型：error
* 字符类型：rune

####变量类型：（复合数据类型）
* 指针（pointer）
* 数组（array）
* 切片（slice）
* 字典（map）
* 结构体（struct）
* 接口（interface）
* 通道（chan）

####变量命名：
<pre>
GO语言一般采用如下三种变量命名方式：
//方式1：
var i int
i = 100
//方式2：（无类型，有被赋的值来决定其变量类型）
var i = 100
//方式3：（省略var关键字方式）
i := 100
//简化方式1：
var i, j, k int
//简化方式2：
var i, j, k int = 1, 2, 3
//简化方式1：
i, j, k := 1, 2, 3
//简化方式3：
var (
    i int
    j float32
    k string
}
//匿名变量
func test() (i,j,k int) {
    i, j, k := 1, 2, 3
    return
}
_, a, _ = test()
</pre>

####常量命名：
* const的使用与其他语言并没有明显区别
* const只拥有var的方式1和方式2：
<pre>
//方式1：
const Pi float32 = 3.1415926
//方式2：
const Pi = 3.1415926
//方式3：
const (
    Pi  float32 = 3.1415926
    API string = "http://k-zone.cn"
)
</pre>

####字符串：
* GO语言使用UTF-8的编码方式。
* GO语言使用一对双引号（""）（单行）或反引号（` `）（多行）来定义字符串。
* 字符串的连接使用"+"（与其他语言并没有本质区别）
* 字符串取长度：len(str)
* 字符串取个数：
<pre>
str := "hello"
fm.Println( str[1] ) //print e
</pre>

####枚举类型：
* 使用关键字：iota
* 初始值为0（从0开始计数）
* 每遇到iota即重新初始化（从0开始计数）
<pre>
const (
A = iota //A = 0
B        //B = 1
C        //C = 2
D        //D = 3
)
const E = iota //E = 0，iota从0开始重新计算
</pre>

####数组、切片、字典：

#####数组：
* 声明：
<pre>
//方式1：
var arr [3]int
//方式2：
a := arr [3]int{1, 2, 3}
//方式3：（声明了长度为5的数组，但只赋值了前三个变量）
b := arr [5]int{1, 2, 3}
//方式4：（根据赋值的数量决定数组的长度）
c := arr [...]int{1, 2, 3}
</pre>
* 数组的长度不可变。
* 数组是值类型变量。意味着以array作为参数的时候，每次操作都会产生一个array的副本。
* 数组长度的取得：len(arr)
* 使用for来遍历数组，如：
<pre>
arr := [...]int{1,2,3,4,5}
for i := 0; i < len(arr); i++ {
    fm.Print("Array Element is " + arr[i])
}
</pre>
* 使用rang来遍历数组，如：
<pre>
arr := [...]int{1,2,3,4,5}
for i, v := range arr {
    fm.Println("Arrat Element [", i "]=", v)
}
* make不能用于数组的创建。
</pre>

#####切片类型：
* 声明：
<pre>
var slice []int //注意这里并没有在[]里面声明长度，这是与array在声明上的区别
</pre>
* 切片可以直接创建，也可从已知的数组或者切片中创建，其获取方式：array[i:j] 或者 slice[i:j]
> * i：开始位置（从0开始）
> * j：结束位置（但不包含array[j]，它的长度是j-i）
* 切片是一个引用类型（这是与array又一区别）
<pre>
arr := [5]int{1,2,3,4,5}
var slice = []int
slice = arr[1:3]
//slice = 2,3，即包含arr[1] arr[2]
//几种特殊的[i:j]
slice := arr[:]  //基于arr的全部元素生成切片
slice := arr[:3] //基于arr的前五个元素生成切片
slice := arr[3:] //从arr的第五个元素开始直到最后一个元素生成切片。
</pre>
* 切片的取得：
> * len(slice)   //取得当前slice存在的元素个数。
> * cap（slice） //取得当前slice全部的元素个数。
* 切片的组合，使用append关键字，如：
<pre>
slice1 := []int{1,2,3,4,5}
i,j,k  := 6, 7, 8
slice2 := make([]int,3)
append(slice1, i, j, k )  //slice1 = 1 2 3 4 5 6 7 8
append(slice1, slice2...) //slice1 = 1 2 3 4 5 0 0 0
</pre>
* 当append的长度大于cap，会自动分配长度。
* 切片的复制，使用内置关键字：copy，可以用于长度不一致的两个切片的复制，如：
<pre>
slice1 := []int{1,2,3,4,5}
slice2 := []int{6,7,8}
copy(slice1, slice2) //6 7 8 4 5
copy(slice2, slice1) //1 2 3
</pre>
####字典（map）：
* 声明：
<pre>
var dict = map[int]string //声明一个map类型的变量dict，其中key是int类型，value是string类型
</pre>
* map是一组无序的key = value的对应关系。
* 与slice一样可以使用make关键字创建。即：dict := make(map[int]string , 3)
* map的查找：
<pre>
dict := make(map[int]string)
dict[0] = "world"
dict[1] = "hello"
fmt.Println(dict[0]) //world
value, ok := dict[0]
if ok {
    fmt.Println("search ok, value = ", value )
}
value, ok = dict[2] //注意：由于之前的value与ok已经定义，所以这里不能用:=方式
if ok {
    fmt.Println("search ok, value = ", value )
} else {
    fmt.Println("search error")
}
</pre>
* map的遍历：（与切片的方式一致）
<pre>
dict := make(map[int]string)
dict[0] = "world"
dict[1] = "hello"
for k, v := range dict {
    fmt.Println("dict[", k, "]=", v)
}
</pre>

#####make用法：
* 切片（slice）与字典（map）可以通过关键字make来生成，如：
<pre>
slice := make([]int,3,10) //创建一个初始化为0（因为是int类型），初始元素个数为3，总共有10个元素的切片
</pre>

####条件语句：
#####if：
* 与其他语言相比，少了()，并且强制if else的格式，如：
<pre>
if x {
    //TO DO
} else {
    //TO DO
}
</pre>
* 可以在if中定义变量，此变量只能作用于该if条件块，如：
<pre>
func add(a,b int) int {
    return a + b
}
if x := add(1,2); x > 0 {
    fmt.Println("x is ", x)
}
</pre>

#####switch：
* 与if一样，省略了()
* 与其他语言相比，省略了break。
* case分支可以使用判断条件。
* 内置关键字：fallthrough（强制执行下一个case，类似有break的语言中没有写break的效果），如：
<pre>
i := 1
switch i {
case 0:
fmt.Println("i is", i )
case 1:
fmt.Println("i is", i )
case 2,3,4:
fmt.Println("i is", i )
fallthrough
case i == 0:
fmt.Println("i is", i )
default:
fmt.Println("i is", i )
}
</pre>
* switch后面的变量也可以省略，如：
<pre>
//如这样使用的话，switch后面的变量必须要省略
i := 1
switch {
case i == 1:
    fmt.Println("i is ", i)
default:
	fmt.Println("i is ", i)
}
</pre>

#####for：
* 声明：
<pre>
for expression1; expression2; expression3 {
    //...
}
</pre>
* 使用与其他语言并没有本质区别。
* 与其他条件语句一样，不需要()
* 其中expression1与expression3可以省略，在这种情况下与while作用一样，如：
<pre>
sum := 1
for sum < 10 {
    sum += 1
}
</pre>
* break：跳出当前循环。
* continue：跳出本次循环。


####函数：
* 使用func关键字。
* 函数也是一种（特殊）的变量。
* 允许有多个参数，如：
<pre>
func test()
func test(a int, b string)
func test(a,b int)
</pre>
* 允许有多个返回值，如：
<pre>
func test(a,b int) int {
    return a + b
}
func test(a,b int) (c,d int) {
    c = a + b
    d = a - b
    return
}
func test(a,b int)(int, int) {
    return a + b, a - b
}
</pre>
* 可变参数，使用关键字...<类型>，如：
<pre>
func test(a,b int, args ...int)
//调用
test(1, 2)
test(1, 2, 3)
test(1, 2, 3, 4, 5)
</pre>
* 可变参数，可以传递任意类型的参数，使用关键字...interface{}，如：
<pre>
func test(a, b int, args ...interface{})
//调用
test(1, 2)
test(1, 2, 3)
test(1, 2, 3, 4, 5, "a", "b", true)
test(1, 2, "a", "b", "c", 3, 4, 5, 6, true, 1 < 2)
</pre>
* 可变参数本质上是个切片（slice），所以具有slice的一切特性，如可以用range，append、copy等操作。
* 匿名函数，不加函数名，如：
<pre>
f := func (a,b int) int {
    return a + b
}
//使用：
c := f(1, 2)
</pre>
* 函数作为值类型使用：
<pre>
package main
import "fmt"
//
type testInt func(int) bool // 声明了一个函数类型
//
func isOdd(integer int) bool {
    if integer%2 == 0 {
        return false
    }
    return true
}
//
func isEven(integer int) bool {
    if integer%2 == 0 {
        return true
    }
    return false
}
// 声明的函数类型在这个地方当做了一个参数
func filter(slice []int, f testInt) []int {
    var result []int
    for _, value := range slice {
        if f(value) {
            result = append(result, value)
        }
    }
    return result
}
func main(){
    slice := []int {1, 2, 3, 4, 5, 7}
    fmt.Println("slice = ", slice)
    odd := filter(slice, isOdd)    // 函数当做值来传递了
    fmt.Println("Odd elements of slice are: ", odd)
    even := filter(slice, isEven)  // 函数当做值来传递了
    fmt.Println("Even elements of slice are: ", even)
}
</pre>
* 特殊的两个方法（保留函数）：init()和main()
  * 在定义时不能有参数、不能用返回值
  * init()是可选的
  * main()必须要跟package main在一起使用
  * GO语言会自动调用init()和main()，无需手动调用。
  * init()和main()的调用流程  
> ![](https://raw.github.com/astaxie/build-web-application-with-golang/master/images/2.3.init.png)
* 函数的导入，使用import方式，如：
<pre>
//方式1：
import "fmt"
import "os"
//方式2：
import (
    "fmt"
    "os"
)
//方式3：（相对路径）
import "./xxx" //当前目录下xxx文件夹，不建议采用这方式
//方式4：（绝对路径）
import "xxx/yyy" //加载$GOPATH/src/xxxx/yyyy模块
//方式5：(.操作)
import (
    . "fmt" //省略fmt前缀，如在调用时直接使用 Println()
)
//方式6：（别名操作）
import (
    f "fmt" //直接使用f.Println
)
//方式7：（_操作）
import (
    _ "github.com/ziutek/mymysql/godrv" //调用此包中的init函数
)
</pre>
* defer（延迟），一般多用作出错处理的关闭操作，某些程度上类似与try...catch...finial，如：
<pre>
file, err := os.Open()
if err != nil {
    //TO DO
    return
}
defer file.Close()
</pre>
* 可以多次使用defer，defer采用后进先出模式，即__后面定义的defer要先执行__。

####指针：
* GO语言的函数参数传递是传入参数的副本（copy），如：
<pre>
func add1(a, b int) {
    a = a + b
	fmt.Println("func add1's a = ", a) //func add1's a =  3
}
a, b := 1, 2
add1(a, b)
fmt.Println("a = ", a) //a =  1
</pre>
* 可以使用指针的方式来避免产生副本的方式。
* GO语言的指针定义方式：*<类型>，如a *int b *string
* GO语言的指针使用方式：*a + *b
* a的地址：&a
* *用于操作；&用于传址。
* 取地址（&）再传递指针（*）操作，如：
<pre>
func add2(a, b *int) {
    *a = *a + *b
	fmt.Println("func add1's *a = ", *a) //func add1's *a =  3
}
a, b := 1, 2
add2(&a, &b) //&a =  3
</pre>
* __string、slice、map本质上就是指针类型__，因而在操作的时候不需要转换为指针类型。

####类型系统：
* 基本类型，int, float32, bool等。
* 复合类型，array, slice, map等。
* 可以指向任意对象的类型（Any类型），定义为：interface{}
* 值语义和引用语义。
* 面向对象。
* 接口。

####type：
* 可以为任意类型添加方法（除指针类型外）
* 声明：
<pre>
//声明
type A int
//定义
func (a A) add (b A) A {
    return a + b
}
//使用
var i, j A = 1, 2
c := i.add(j)
fmt.Println("c = ", c)
</pre>

####struct（结构体）：
* GO语言并没有传统的OOP等概念，要实现一个Class，在GO语言中使用struct方式。
* 声明：
<pre>
type Rect struct {
    width float32
    height float32
}
</pre>
* 使用：
<pre>
//方式1：
var rect = new(Rect)
rect.width = 100
rect.height = 100
//方式2：（与方式1一样）
var rect = Rect{}
rect.width = 100
rect.height = 100
//方式3：（初期化时就赋值）
var rect = Rect{100, 100}
//方式4：（使用key : value的方式，所以不需要按照Rect定义的顺序赋值）
var rect = Rect{ height : 100, width : 100 }
</pre>
* “类方法”：
<pre>
//声明
func (r Rect ) Area() float32 {
    return r.width * r.height
}
//使用：
r := Rect{100, 100}
area := r.Area()
fm.Println("area = ", area)
</pre>
* 类继承：（匿名字段）
<pre>
//声明
type Column struct {
    Rect
    length float32
}
//类方法
func (c Column) Volume() float32 {
    //return c.Rect.Area() * c.length
    return c.Rect.width * c.Rect.height * c.length
}
//使用
r := Rect{100, 100}
c := Column{r, 100}
vol := c.Volume()
fmt.Println("volume = ", vol)
</pre>
* 方法的继承：
<pre>
c.Area() //Column继承于Rect，因此也具有Rect的成员方法
fm.Println("area = ", c.Area())
</pre>
* 方法的覆盖：
<pre>
//定义
func (c Column) Area() float32 {
    return c.Rect.width * 200
}
//使用
r := Rect{100,100}
c := Column{r,2}
r.Area() //调用了Rect的类方法Area()
fmt.Println("r.Area()", r.Area()) //10000
c.Area() //调用了Column的类方法Area()
fmt.Println("r.Area()", r.Area()) //20000
</pre>
* 匿名字段不仅能适用于struct，它可以适用与任何类型，如：
<pre>
//声明
type Column struct {
    Rect
    length float32
    int
}
//使用
r := Rect{100, 100}
c := Column{Rect : r, length : 100}
//修改匿名字段(int)
c.int = 9
fmt.Println("c.int = ", c.int)
</pre>
* 当继承（匿名函数）的字段出现重复时，GO语言采用最外层优先，如：
<pre>
package main
import "fmt"
//
type Human struct {
    name string
    age int
    phone string  // Human类型拥有的字段
}
//
type Employee struct {
    Human  // 匿名字段Human
    speciality string
    phone string  // 雇员的phone字段
}
//
func main() {
    Bob := Employee{Human{"Bob", 34, "777-444-XXXX"}, "Designer", "333-222"}
    fmt.Println("Bob's work phone is:", Bob.phone)
    // 如果我们要访问Human的phone字段
    fmt.Println("Bob's personal phone is:", Bob.Human.phone)
}
</pre>

####interface：
* 声明：
<pre>
type IObjc interface {
    Area()
}
</pre>
* 实现：
<pre>
type Rect struct {
	width  float32
	height float32
}
func (r Rect) Area() {
	area := r.width * r.height
	fmt.Println("Rect's Area = ", area)
}
type Column struct {
	Rect
	length float32
}
func (c Column) Area() {
	area := c.Rect.width * c.Rect.height
	fmt.Println("Column's Area = ", area)
}
//使用
r := Rect{100, 100}
c := Column{Rect{100, 200}, 2}
var objc IObjc
objc = r
objc.Area() //Rect's Area = 10000
objc = c
objc.Area() //Column's Area = 20000
</pre>