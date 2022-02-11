```
Installation Guide:

Go to golang.org and choose download option. Then at the download page, select appropriate arm based verison for m1 mac.

After installatin, setup can be deleted

Go to /usr/local/go

Execute following command:

export GOROOT=/usr/local/go

export GOPATH=$HOME/Desktop/folders/projects/go-workspace

export PATH=$GOPATH/bin:$GOROOT/bin:$PATH

Go is very useful for multi-threading. It has lot of features that are very simple.

Goroutines

They are light weight threads of execution managed by the go runtime.

They are just functions that can be run concurrently

It's simple to start goroutine . That's it's used widely for backend app that needs concurrency.

package main

import (
	"fmt"
	"time"
)

func spinner(delay time.Duration) {
	for {
		for _, x := range `-|/` {
			fmt.Printf("
%c", x)
			time.Sleep(delay)
		}
	}
}

func waitAndPrint(delay time.Duration) {
	fmt.Println("Working")
	time.Sleep(delay)
	fmt.Println("Fn")
}

func main() {
	go spinner(100 * time.Millisecond)
	waitAndPrint(10 * time.Second)
}
Channels

Imagine we have lot of go routines, Channels are used to communicate between various goroutines. Each channel is a condult for values of a particular type called the channel element type.


package main
import (
  "fmt"
  "time"
)
func other(c chan string) {
  time.Sleep(5 * time.Second)
  c <- " i am a goroutine"
}
func main() {
  done := make(chan string)
  defer close(done)
  go other(done)
  // wait for data to come
  data := <-done
  fmt.Println(data)
}            
            
Mutex

A Mutex is a method used as a locking mechanism to ensure that only one Goroutine is accessing the critical section of code at any point of time. This is done to prevent race conditions from happening. Sync package contains the Mutex

In 2006, Intel released the first dual core processor. In 2007, Google started creating the go programming language. They wanted to advantage of multiple cores. Hence, Go is the first viable language which was wriiten to take advantage of multiple cores. It's statically typed, garbage compiled, to run on distributed environments across multiple machines and easily take advantage of that.It's built time is super fast. Google wanted fast build, fast efficient compilation, efficient execution and easy programming such as python but it has advantage of compiled time, GC ans static type checking. People who helped in creating c, UTF-8 ( world's most popular encoding scheme ) and UNIX OS contributed towards creation of go. Youtube is about all re-written in go. 2009 => open sourced and first version was released at 2012. Go is really popular in China because of its large population.

Server Side : Go > Node.js > Python > Ruby > PHP

People such as Rob Pike ( UTF-8 ), Ken Thompson ( Unix OS, He re-wrote the Unix kernel in C ), and Robert Griesemer ( V8 JS Engine ) led the project.

Go was built to do what google does. Google is rewriting Google with Go. Youtube is about all re-written in go

Commands :

go mod init _____

go build ___.go

go run ___.go

go build github.com/saiashish9/..... ./_____

Variables:

Short Variable Declarator Operator:

x:= 7 fmt.Println(x)

fmt.Printf("%T",x)

Block Level Scope


func main(){
  x := 10
  fmt.Println(x)
}              
              
Package Level Scope


package main

import "fmt"

var x = 10

var y int

func main(){
  fmt.Println(x)
  fmt.Println(y) // 0
}
              
Composite Literal

Slice

It is a datastructure used to hold a list of things.


a := []int{1, 2, 3}
fmt.Println(a, a[:2])
            
Map


m := map[string]int{ "a" : 5, "b" : 7}
            
Struct


type ht int
type person struct {
  fn string
  ln string
}         
func main(){
var t ht
t = 7
}
p := person{"a","b"}
         
Functions

func (receiver) identifier(parameters)


func (p person) speak(){
  fmt.Println(p.fname,`"1235"`)
}            
p := person{"a","b"}
p.speak()
            
Nested Struct


type struct secretAgent {
  person
  license bool
}         
s1:= secretAgent {
  person {
    "a",
    "b"
  },
  true
}
s1.person.speak()
              
Interfaces And Polymorphism


type human innterface {
  speak()
}       

func saySomething(h human){
  h.speak()
}

saySonething(p1)
saySonething(s1)

            
Fundamentals


// i:=42 is not valid here
var i = 42 
// i => local level access
// I => global level access
func main(){
  var i int = 42
  var j float32 = 27.6
  fmt.Printf("%v ,%T", j, j)
  var q string
  q = string(i)
  q = strconv.Itoa(p)
  // variable blocks
  var (
	  i = 32
  )
  var (
    x string = "A"
    y string = "B"
  )
  fmt.Println(x, y)
  var n bool = true
  n = 1==1
  var i int8 = 6
  // 6 == 6 false
  // int(6) == 6 true
  // int8 +128 - 127
  // int16 -32768 - 32767
  // int32 int64
  // var n uint16 = 42
  // uint32 uint64 X
  // uint8 -> byte common
  var i complex64 = 1 + 2i
  i = complex(5, 6)
  fmt.Println(i)
  fmt.Println(real(i), imag(i))
  s := "abcd"
  println("abcd"[2], s[2])
  // s[2] = "j" is not valid
  // & | ^ &^ xnor << >>
  rune '' int32
  r := 'a'
  fmt.Println(r)
  var r rune = 'i'
  fmt.Println(r)
  const myConst int = 42
  const c float32 = math.Sin(1.57) X
  const (
    a = iota
    b = iota
    c = iota
  )
  const (
    a2 = iota
    b2
  )
  var c2 int = a2
  fmt.Println(a2 == c2)
  const (
    _ = 5
    a
    b
    c
  )
  // 5 5 5
  println(a, b, c)
  const (
    _ = iota + 5
    a
    b
    c
  )
  println(a, b, c)
  // 6 7 8
  const (
    _  = iota
    KB = 1 << (10 * iota)
    MB
    GB
    TB
    PB
    EB
    ZB
    YB
  )
  fileSize := 4000000000.00
  fmt.Printf("%.2fGB", fileSize/GB)
  const (
    a = 1 << iota
    b
    c
    e
  )
  1 2 4 16
  var d byte = a | b | c
  println(d)
  fmt.Printf("%b\n", d)
  fmt.Printf("%v\n", a&d == a)
  fmt.Printf("%v\n", a&e == a)
  _ = iota // write only value
  grades := [3]int{97, 85}
  g := [...]int{1, 2}
  var students [3]string
  fmt.Println(students)
  students[0], students[1] = "a", "b"
  fmt.Println(students, len(students))
  fmt.Printf("%v \n%v \n", grades, g)
  var a [3][3]int = [3][3]int{
  	[3]int{1, 0, 1},
  	[3]int{0, 0, 1},
  	[3]int{1, 0, 0}}
  fmt.Println(a)
  a := [...]int{1, 2, 3}
  b := a
  c := &a
  c[1] = 5
  b[1] = 5
  fmt.Println(a, b, c)
  // slice
  a := []int{1, 2, 3}
  fmt.Println(a, a[:2])
  a := make([]int, 3, 1000)
  fmt.Println(len(a), cap(a))
  a = append(a, 1, 2)
  b := []int{}
  b = append(b, []int{2, 3, 4}...)
  fmt.Println(b)
  fmt.Println(a)
  a := []int{1, 2, 3, 4, 5}
  fmt.Println(a)
  b := a[:len(a)]
  fmt.Println(b)
  }            
            
Constructs


for i := 0; i < 10; i++ {
	if i%2 == 0 {
		continue
	}
	fmt.Println(i)
}
s := []int{1, 2, 3}
fmt.Println(s)
for k, v := range s {
	fmt.Println(k, v)
}
x := map[string]int{
	"a": 1,
}
for _, p := range x {
	fmt.Println(p)
}
for j := 7; j <= 9; j++ {
	fmt.Println(j)
}
for {
	fmt.Println("loop")
	break
}           
s := []int{1, 2, 3}
fmt.Println(s)
for k, v := range s {
  fmt.Println(k, v)
}   
for i, j := 0; i < 5; i, j = i+1, j+1 {
  fmt.Println(i, j)
}
for i := 0; i < 10; i++ {
  if i%2 == 0 {
    continue
  }
  fmt.Println(i)
}
s := map[string]int{
  "a": 1,
  "b": 2,
}
if c, d := s["a"]; d {
  fmt.Println(c)
}
myNum := 0.123
if math.Abs(myNum/math.Pow(math.Sqrt(myNum), 2)-1) < 0.001 {
  fmt.Println("same")
} else if 0 == 0 {
  fmt.Println("diff")
}
switch i := 2 + 3; i {
case 1, 2:
  fmt.Println("one")
case 3:
  fmt.Println("two")
default:
  fmt.Println("neither one nor two")
}
i := 2
switch {
case i <= 10:
  fmt.Println("<=0")
  fallthrough
case i >= 20:
  fmt.Println(">=0")
}
var i interface{} = 1
i = 2.2
i = true
switch i.(type) {
case int:
  fmt.Println("i is an int")
case string:
  fmt.Println("string")
case bool:
  fmt.Println("bool")
case float32:
  fmt.Println("float32")
  fmt.Println(i)
}
for i := 0; i < 5; i += 2 {
  fmt.Println(i)
}
// i++ X
// i=0 , j=0 X
for i, j := 0; i < 5; i, j = i+1, j+1 {
  fmt.Println(i, j)
}
for i := 0; i < 10; i++ {
  if i%2 == 0 {
    continue
  }
  fmt.Println(i)
}
            
Functions:


package main
import "fmt"
func main() {
	sayMsg("Go")
	greeting := "Hello"
	name := "Sai"
	sayGreeting(&greeting, &name)
	fmt.Println(name)
	sum(1, 2, 3, 4)
	g := greeter{
		"hi", "Go",
	}
	g.greet()
	fmt.Println(g.name)
}
type greeter struct {
	greeting string
	name     string
}

func (g *greeter) greet() {
	fmt.Println(g)
	g.name = ""
}
func sum(values ...int) {
	fmt.Println(values)
	result := 0
	for _, v := range values {
		result += v
	}
	fmt.Println(result)
}
func sayGreeting(greeting, name *string) {
	fmt.Println(*greeting, *name)
	*name = "Sai9"
	fmt.Println(*name)
}
func sayMsg(msg string) {
	fmt.Println(msg)
}            
            
Interfaces:


package main
import "fmt"
func main() {
	var w Writer = ConsoleWriter{}
	w.Write([]byte("Hello Go!"))
	myInt := IntCounter(0)
	var inc Incrementer = &myInt
	for i := 0; i < 10; i++ {
		fmt.Println(inc.Increment())
	}
}
func (ic *IntCounter) Increment() int {
	*ic++
	return int(*ic)
}
type IntCounter int
type Incrementer interface {
	Increment() int
}
type Writer interface {
	Write([]byte) (int, error)
}
type Closer interface {
	Close() error
}
type WriterCloser interface {
	Writer
	Closer
}
type ConsoleWriter struct{}
func (cw ConsoleWriter) Write(data []byte) (int, error) {
	n, err := fmt.Println(string(data))
	return n, err
}            
            
Tags


package main
import (
	"fmt"
	"reflect"
)
type Animal struct {
	Name   string `required max:"100"`
	Origin string
}
func main() {
	t := reflect.TypeOf(Animal{})
	field, _ := t.FieldByName("Name")
	fmt.Println(field.Tag)
}
            
            
Pointers


package main
import "fmt"
func main() {
	var a int = 42
	b := a
	fmt.Println(a, b)
	a = 27
	fmt.Println(a, b)
	var a int = 42
	var b *int = &a
	fmt.Println(a, b, *b)
	a = 27
	fmt.Println(a, *b)
	a := [3]int{1, 2, 3}
	b := &a[0]
	c := &a[1] - 4
	fmt.Println("%v %p %p\n", a, b, c)
	var ms *myStruct
	ms = new(myStruct)
	ms = myStruct{foo: 42}
	(*ms).foo = 42
	// compiling helping us out
	ms.foo = 42
	fmt.Println(ms, ms.foo, (*ms).foo)
}
type myStruct struct {
	foo int
}
Structs


package main
import "fmt"
type Doctor struct {
	number     int
	actorName  string
	companions []string
}
type A struct {
	name   string
	origin string
}
type B struct {
	A
	Canfly bool
}
func main() {
	s := map[string]int{
		"a": 1,
		"b": 2,
	}
	s["a"] = 3
	delete(s, "a")
	_, b := s["a"]
	// no need to make use of _ again
	fmt.Println(s, b)
	a := Doctor{
		number:    3,
		actorName: "Sai",
		companions: []string{
			"a",
			"b",
		},
	}
	b := Doctor{
		3,
		"Sai",
		[]string{
			"a",
			"b",
		},
	}
	a := struct{ name string }{name: "Sai"}
	b := &a
	b.name = "Ashish"
	fmt.Println(a, b)
	// go doesn't supports traditional oop features
	// go doesn't have inheritance
	// fmt.Println(b.actorName)
	b := B{}
	b.Canfly = true
	b.name = "Sai"
	fmt.Println(b, b.name)
	type A struct {
		name   string
		origin string
	}
	type B struct {
		A
		destination string
	}
	b := B{
		A: A{"sai", "123"},
		destination: "delhi",
	}
	fmt.Println(b)
}            
            
Routines

A goroutine is a lightweight thread of execution used for concurrency.

Example 1


package main
import (
  "fmt"
  "time"
)
func f(from string) {
  for i := 0; i < 3; i++ {
      fmt.Println(from, ":", i)
  }
}
func main() {  
  f("direct")
  go f("goroutine")
  go func(msg string) {
      fmt.Println(msg)
  }("going")  
  time.Sleep(time.Second)
  fmt.Println("done")
}
go run goroutines.go
direct : 0
direct : 1
direct : 2
goroutine : 0
going
goroutine : 1
goroutine : 2
done  
  
Example 2


package main
import (
	"fmt"
	"sync"
)
var wg = sync.WaitGroup{}
var counter = 0
var a = sync.RWMutex{}
func main() {
	// runtime.GOMAXPROCS(100)
	for i := 0; i < 10; i++ {
		wg.Add(2)
		go sayHello()
		go increment()
	}
	wg.Wait()
}
func sayHello() {
	a.RLock()
	fmt.Println(counter)
	a.RUnlock()
	wg.Done()
}
func increment() {
	a.Lock()
	counter++
	a.Unlock()
	wg.Done()
}
go run main.go
1
2
2
2
2
2
2
2
2
3
w/o mutexes
0
2
3
4
4
5
6
7
8
10

package main
import (
	"fmt"
	"sync"
	"time"
)
var wg = sync.WaitGroup{}
func main() {
	var msg = "hello"
	wg.Add(1)
	go func(msg string) {
		fmt.Println(msg)
		wg.Done()
	}(msg)
	msg = "Good Bye"
	wg.Wait()
	// closure's anonymous fns do have access to outer scope
	time.Sleep(100 * time.Millisecond)
}
func sayHello() {
	fmt.Println("hello")
}  
WaitGroups

To wait for multiple goroutines to finish, we can use a wait group.Sleep to simulate an expensive task. This WaitGroup is used to wait for all the goroutines launched here to finish. Note: if a WaitGroup is explicitly passed into functions, it should be done by pointer.
Wrap the worker call in a closure that makes sure to tell the WaitGroup that this worker is done. This way the worker itself does not have to be aware of the concurrency primitives involved in its execution.


package main
import (
	"fmt"
	"sync"
	"time"
)
func worker(id int) {
	fmt.Printf("Worker %d starting\n", id)
	time.Sleep(time.Second)
	fmt.Printf("Worker %d done\n", id)
}
func main() {
	var wg sync.WaitGroup
	for i := 1; i <= 5; i++ {
		wg.Add(1) // increases counter by 1 as we've 1 go routine
		i := i
		go func() {
			defer wg.Done() // decreases counter by 1
			worker(i)
		}()
	}
	// Block until the WaitGroup counter goes back to 0;
	// all the workers notified they're done.
	wg.Wait()
}
o/p
Worker 4 starting
Worker 1 starting
Worker 5 starting
Worker 3 starting
Worker 2 starting
Worker 2 done
Worker 5 done
Worker 4 done
Worker 3 done
Worker 1 done 

// w/o defer
Worker 5 starting
Worker 2 starting
Worker 1 starting
Worker 4 starting
Worker 3 starting
              
Defer

A defer statement defers the execution of a function until the surrounding function returns. The deferred call's arguments are evaluated immediately, but the function call is not executed until the surrounding function returns. Defer is used to delay execution of a statement until function exits and is useful to group "open" and "close" functions together Arguments evaluated at time defer is executed, not at time of called function execution


package main
import "fmt"
func main() {
  fmt.Println("1")
  defer fmt.Println("2")
  fmt.Println("3")
  defer fmt.Println("5")
  // defer takes the value at the time defer is called
  a := "5"
  defer fmt.Println(a)
  a = "6"
}              
// LIFO Stack
// Example 2:

package main
import "fmt"
func main() {
	defer fmt.Println("world")
	fmt.Println("hello")
}
hello
world
Channel

Channels are the pipes that connect concurrent goroutines. You can send values into channels from one goroutine and receive those values into another goroutine.


package main
import "fmt"
func main() {
  // Create a new channel with `make(chan val-type)`.
  messages := make(chan string)
  go func() { messages <- "ping" }()
  msg := <-messages
  fmt.Println(msg, messages)
}
            
Worker Pools

Here’s the worker, of which we’ll run several concurrent instances. These workers will receive work on the jobs channel and send the corresponding results on results. We’ll sleep a second per job to simulate an expensive taskHere’s the worker, of which we’ll run several concurrent instances. These workers will receive work on the jobs channel and send the corresponding results on results. We’ll sleep a second per job to simulate an expensive task.In order to use our pool of workers we need to send them work and collect their results. We make 2 channels for this. Here’s the worker, of which we’ll run several concurrent instances. These workers will receive work on the jobs channel and send the corresponding results on results. We’ll sleep a second per job to simulate an expensive task


package main
import (
	"fmt"
	"time"
)
func worker(id int, jobs <-chan int, results chan<- int) {
	for j := range jobs {
		fmt.Println("worker", id, "started  job", j)
		time.Sleep(time.Second)
		fmt.Println("worker", id, "finished job", j)
		results <- j * 2
	}
}
func main() {
	const numJobs = 5
	jobs := make(chan int, numJobs)
	results := make(chan int, numJobs)
	for w := 1; w <= 3; w++ {
		go worker(w, jobs, results)
	}
	for j := 1; j <= numJobs; j++ {
		jobs <- j
	}
	close(jobs)
	for a := 1; a <= numJobs; a++ {
		<-results
	}
}
O/P:
worker 3 started  job 1
worker 1 started  job 2
worker 2 started  job 3
worker 3 finished job 1
worker 1 finished job 2
worker 1 started  job 5
worker 3 started  job 4
worker 2 finished job 3
worker 3 finished job 4
worker 1 finished job 5            
            
Atomic Counters

The primary mechanism for managing state in Go is communication over channels. We saw this for example with worker pools. There are a few other options for managing state though. Here we’ll look at using the sync/atomic package for atomic counters accessed by multiple goroutines.


package main
import (
	"fmt"
	"sync"
	"sync/atomic"
)
func main() {
	var ops uint64
	var wg sync.WaitGroup
	for i := 0; i < 50; i++ {
		wg.Add(1)
		go func() {
			for c := 0; c < 1000; c++ {
				atomic.AddUint64(&ops, 1)
			}
			wg.Done()
		}()
	}
	wg.Wait()
	fmt.Println("ops:", ops)
}
ops: 50000
Mutexes

In computer science, mutual exclusion is a property of concurrency control, which is instituted for the purpose of preventing race conditions. It is the requirement that one thread of execution never enters a critical section while a concurrent thread of execution is already accessing critical section, which refers to an interval of time during which a thread of execution accesses a shared resource, such as [Shared data objects, shared resources, shared memory].

For more complex state we can use a mutex to safely access data across multiple goroutines. Container holds a map of counters; since we want to update it concurrently from multiple goroutines, we add a Mutex to synchronize access. Note that mutexes must not be copied, so if this struct is passed around, it should be done by pointer.Lock the mutex before accessing counters; unlock it at the end of the function using a defer statement.


package main
import (
	"fmt"
	"sync"
)
type Container struct {
	mu       sync.Mutex
	counters map[string]int
}
func (c *Container) inc(name string) {
	c.mu.Lock()
	defer c.mu.Unlock()
	c.counters[name]++
}
func main() {
	c := Container{
		counters: map[string]int{"a": 0, "b": 0},
	}

	var wg sync.WaitGroup
	doIncrement := func(name string, n int) {
		for i := 0; i < n; i++ {
			c.inc(name)
		}
		wg.Done()
	}
	wg.Add(3)
	go doIncrement("a", 10000)
	go doIncrement("a", 10000)
	go doIncrement("b", 10000)
	wg.Wait()
	fmt.Println(c.counters)
  // O/P:
  // map[a:20000 b:10000]
}
Closure

Go supports anonymous functions, which can form closures. Anonymous functions are useful when you want to define a function inline without having to name it.This function intSeq returns another function, which we define anonymously in the body of intSeq. The returned function closes over the variable i to form a closure.


package main
import "fmt"
func intSeq() func() int {
	i := 0
	return func() int {
		i++
		return i
	}
}
func main() {
	nextInt := intSeq()
	fmt.Println(nextInt())
	fmt.Println(nextInt())
	fmt.Println(nextInt())
	newInts := intSeq()
	fmt.Println(newInts())
}
O/P:
1
2
3
1            
            
Panic

Occurs when program cannot continue at all cannot obtain TCP port for web server if nothing handles panic, program will exit. A panic typically means something went unexpectedly wrong. Mostly we use it to fail fast on errors that shouldn’t occur during normal operation, or that we aren’t prepared to handle gracefully.


// Example 1
err := http.ListenAndServe(":8000",nill)
if err != nill {
panic(err.Error())
}
// Example 2
package main
import "os"
func main() {
    panic("a problem")
    _, err := os.Create("/tmp/file")
    if err != nil {
        panic(err)
    }
}
// O/P
go run panic.go
panic: a problem
goroutine 1 [running]:
main.main()
    /.../panic.go:12 +0x47
...
exit status 2
              
Recover

Used to recover from panics Only useful in deferred functions Current function will not attempt to continue , but higher functions in call stack will

Go makes it possible to recover from a panic, by using the recover built-in function. A recover can stop a panic from aborting the program and let it continue with execution instead. An example of where this can be useful: a server wouldn’t want to crash if one of the client connections exhibits a critical error. Instead, the server would want to close that connection and continue serving other clients. In fact, this is what Go’s net/http does by default for HTTP servers.

package main
import "fmt"
func mayPanic() {
    panic("a problem")
}
func main() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered. Error:\n", r)
        }
    }()
    mayPanic()
    fmt.Println("After mayPanic()")
}
O/P:
Recovered. Error:
 a problem
Templates:

Example 1:


package main
import "fmt"
func main() {
	name := "Sai
	tpl := `
	<!DOCTYPE html>
	<html lang="en">
	<head>
	<meta charset="UTF-8">
	<title>Hello World!</title>
	</head>
	<body>
	<h1>` + name + `</h1>
	</body>
	</html>
	`
	fmt.Println(tpl)
}              
go run main.go > index.html
              
Example 2:


package main
import (
	"fmt"
	"io"
	"log"
	"os"
	"strings"
)
func main() {
	name := os.Args[1]
	fmt.Println(os.Args[0])
	fmt.Println(os.Args[1])
	str := fmt.Sprint(`
	<!DOCTYPE html>
	<html lang="en">
	<head>
	<meta charset="UTF-8" >
	<title>Conatenation</title>
	</head>
	<body>
	<h1>` +
		name +
		`</h1>
	</body>
	</html>
	`)
	nf, err := os.Create("index.html")
	if err != nil {
		log.Fatal("error")
	}
	defer nf.Close()
	io.Copy(nf, strings.NewReader(str))
}              
              
Package Text Template ( text/template )

temp.go
package main
import (
	"log"
	"os"
	"text/template"
)
var tpl *template.Template
type a1 struct {
	A string
	B int
}
type b1 struct {
	C []a1
}
func init() {
	tpl = template.Must(template.ParseGlob("*"))
	// templates/*.txt
	// templates/*
}
func main() {
	// every type implements the empty interface
	err := tpl.Execute(os.Stdout, nil)
	var data interface{}
	data = []string{"a", "b", "c"}
	data = map[string]string{
		"a": "1"}
	data = a1{A: "a", B: 1}
	data = b1{
		C []{data,data}
	}
	_ = data
	var fm = template.FuncMap(
		"us": strings.ToUpper,
		"ft": firstThree
	)
	// err = tpl.ExecuteTemplate(os.Stdout, "a.txt", nil)
	// err = tpl.ExecuteTemplate(os.Stdout, "tpl.gohtml", 42)
	// err = tpl.ExecuteTemplate(os.Stdout, "tpl1.gohtml", `test`)
	err = tpl.ExecuteTemplate(os.Stdout, "tpl1.gohtml", data)
	if err != nil {
		log.Fatalln(err)
	}
}
tp1.gohtml
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Hello World!</title>
</head>
<body>
<h1>The meaning of life: {{.}}</h1>
</body>
</html>
tp2.gohtml
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Hello World!</title>
</head>
<body>
{{ range .C }}
  {{ .A }} - {{ .B }}
{{ end }}
</body>
</html>
{{/* {{$t := .}}
<h1> {{$t}}</h1> */}}
{{/* {{ range . }}
   {{ . }}
{{ end }}*/}}
{{/* {{ range $index , $e := .  }}
    {{ $index }} - {{ $e }}
{{ end }}  */}}
  {{/* {{ $x := .A }}
  {{ $x }}
  {{ .A }} - {{ .B }} */}}
a.txt
########
a
#######
a.gohtml
#########
abcd
########
abc.txt
b
Pipelines in templates

{{ . | fdbl | fsq | fsqrt }}
double , square, square root


package main
import (
  "log"
  "os"
  "text/template"
)
var tpl *template.Template
func init() {
  tpl = template.Must(template.ParseFiles("tpl.gohtml"))
}
func main() {
  xs := []string{"zero", "one", "two", "three", "four", "five"}
  err := tpl.Execute(os.Stdout, xs)
  if err != nil {
    log.Fatalln(err)
  }
}
{{index . 2}}
{{index . 0}}
{{index . 1}}              
              
Nested Template


index.gohtml
<p>{{template "polarbear"}}</p>
file 2:
{{define "polarbear"}}
Here is my polar bear template
{{end}}
              
Html Templates


package main
import (
	"html/template"
	"log"
	"net/http"
)
// html templates escapes un-safe characters avoid cross site scripting
// `<script>alert('hi')</script>`
//  in text templates, fn will be exceuted
//  in html templates , additional characters will be added in b/w
var tpl *template.Template
func init() {
	tpl = template.Must(template.ParseGlob("templates/*.gohtml"))
}
func main() {
	http.HandleFunc("/", index)
	http.Handle("/public/", http.StripPrefix("/public", http.FileServer(http.Dir("public"))))
	http.ListenAndServe(":8080", nil)
}
func index(res http.ResponseWriter, req *http.Request) {
	err := tpl.ExecuteTemplate(res, "index.gohtml", nil)
	if err != nil {
		log.Fatalln("template didn't execute: ", err)
	}
}  

index.gohtml
{{template "btf"}}
{{template "footer"}}
            
Refer to https://github.dev/SaiAshish9/go-templates

TCP Servers

Read from connection


package main
import (
	"fmt"
	"io"
	"log"
	"net"
)
func main() {
	li, err := net.Listen("tcp", ":8080")
	if err != nil {
		log.Fatalln(err)
	}
	defer li.Close()
	for {
		conn, err := li.Accept()
		if err != nil {
			log.Println(err)
			continue
		}
		io.WriteString(conn, "\nHello from TCP server\n")
		fmt.Fprintln(conn, "How is your day?")
		fmt.Fprintf(conn, "%v", "Well, I hope!")
		conn.Close()
	}
}
go run main.go
telnet http 8080
telnet is a program which works on tcp               
              
Write to connection with deadline


package main
import (
	"bufio"
	"fmt"
	"log"
	"net"
)
func main() {
	li, err := net.Listen("tcp", ":8080")
	if err != nil {
		log.Fatalln(err)
	}
	defer li.Close()
	for {
		conn, err := li.Accept()
		if err != nil {
			log.Println(err)
			continue
		}
		go handle(conn)
	}
}
func handle(conn net.Conn) {
  err := conn.SetDeadline(time.Now().Add(10 * time.Second))
	if err != nil {
		log.Fatalln("CONN TIMEOUT")
	}
	scanner := bufio.NewScanner(conn)
	for scanner.Scan() {
		ln := scanner.Text()
		fmt.Println(ln)
    fmt.Fprintf(conn, "I heard you say: %s\n", ln)
	}
	defer conn.Close()
	fmt.Println("Code got here.")
}            
            
Dial


package main
import (
	"fmt"
	"log"
	"net"
)
func main() {
	conn, err := net.Dial("tcp", "localhost:8080")
	if err != nil {
		log.Fatalln(err)
	}
	defer conn.Close()
	fmt.Fprintln(conn, "I dialed you.")
}
            
TCP Server For HTTP


package main
import (
	"bufio"
	"fmt"
	"log"
	"net"
	"strings"
)
func main() {
	li, err := net.Listen("tcp", ":8080")
	if err != nil {
		log.Fatalln(err.Error())
	}
	defer li.Close()
	for {
		conn, err := li.Accept()
		if err != nil {
			log.Println(err.Error())
			continue
		}
		go handle(conn)
	}
}
func handle(conn net.Conn) {
	defer conn.Close()
	request(conn)
}
func request(conn net.Conn) {
	i := 0
	scanner := bufio.NewScanner(conn)
	for scanner.Scan() {
		ln := scanner.Text()
		fmt.Println(ln)
		if i == 0 {
			mux(conn, ln)
		}
		if ln == "" {
			// headers are done
			break
		}
		i++
	}
}
func mux(conn net.Conn, ln string) {
	m := strings.Fields(ln)[0] 
	u := strings.Fields(ln)[1] 
	fmt.Println("***METHOD", m)
  fmt.Println("***URI", u)
	// multiplexer
	if m == "GET" && u == "/" {
		index(conn)
	}
	if m == "GET" && u == "/about" {
		about(conn)
	}
	if m == "GET" && u == "/contact" {
		contact(conn)
	}
	if m == "GET" && u == "/apply" {
		apply(conn)
	}
	if m == "POST" && u == "/apply" {
		applyProcess(conn)
	}
}
func index(conn net.Conn) {
	body := `<!DOCTYPE html><html lang="en"><head><meta charet="UTF-8"><title></title></head><body>
	<strong>INDEX</strong><br>
	<a href="/">index</a><br>
	<a href="/about">about</a><br>
	<a href="/contact">contact</a><br>
	<a href="/apply">apply</a><br>
	</body></html>`
	fmt.Fprint(conn, "HTTP/1.1 200 OK\r\n")
	fmt.Fprintf(conn, "Content-Length: %d\r\n", len(body))
	fmt.Fprint(conn, "Content-Type: text/html\r\n")
	fmt.Fprint(conn, "\r\n")
	fmt.Fprint(conn, body)
}
func about(conn net.Conn) {
	body := `<!DOCTYPE html><html lang="en"><head><meta charet="UTF-8"><title></title></head><body>
	<strong>ABOUT</strong><br>
	<a href="/">index</a><br>
	<a href="/about">about</a><br>
	<a href="/contact">contact</a><br>
	<a href="/apply">apply</a><br>
	</body></html>`
	fmt.Fprint(conn, "HTTP/1.1 200 OK\r\n")
	fmt.Fprintf(conn, "Content-Length: %d\r\n", len(body))
	fmt.Fprint(conn, "Content-Type: text/html\r\n")
	fmt.Fprint(conn, "\r\n")
	fmt.Fprint(conn, body)
}
func contact(conn net.Conn) {
	body := `<!DOCTYPE html><html lang="en"><head><meta charet="UTF-8"><title></title></head><body>
	<strong>CONTACT</strong><br>
	<a href="/">index</a><br>
	<a href="/about">about</a><br>
	<a href="/contact">contact</a><br>
	<a href="/apply">apply</a><br>
	</body></html>`
	fmt.Fprint(conn, "HTTP/1.1 200 OK\r\n")
	fmt.Fprintf(conn, "Content-Length: %d\r\n", len(body))
	fmt.Fprint(conn, "Content-Type: text/html\r\n")
	fmt.Fprint(conn, "\r\n")
	fmt.Fprint(conn, body)
}
func apply(conn net.Conn) {
	body := `<!DOCTYPE html><html lang="en"><head><meta charset="UTF-8"><title></title></head><body>
	<strong>APPLY</strong><br>
	<a href="/">index</a><br>
	<a href="/about">about</a><br>
	<a href="/contact">contact</a><br>
	<a href="/apply">apply</a><br>
	<form method="POST" action="/apply">
	<input type="submit" value="apply">
	</form>
	</body></html>`
	fmt.Fprint(conn, "HTTP/1.1 200 OK\r\n")
	fmt.Fprintf(conn, "Content-Length: %d\r\n", len(body))
	fmt.Fprint(conn, "Content-Type: text/html\r\n")
	fmt.Fprint(conn, "\r\n")
	fmt.Fprint(conn, body)
}
func applyProcess(conn net.Conn) {
	body := `<!DOCTYPE html><html lang="en"><head><meta charet="UTF-8"><title></title></head><body>
	<strong>APPLY PROCESS</strong><br>
	<a href="/">index</a><br>
	<a href="/about">about</a><br>
	<a href="/contact">contact</a><br>
	<a href="/apply">apply</a><br>
	</body></html>`
	fmt.Fprint(conn, "HTTP/1.1 200 OK\r\n")
	fmt.Fprintf(conn, "Content-Length: %d\r\n", len(body))
	fmt.Fprint(conn, "Content-Type: text/html\r\n")
	fmt.Fprint(conn, "\r\n")
	fmt.Fprint(conn, body)
}
            
The Dial function connects to a server:

The Listen function creates servers:

Net Http


package main
import (
	"html/template"
	"log"
	"net/http"
	"net/url"
)
type hotdog int
func (m hotdog) ServeHTTP(w http.ResponseWriter, req *http.Request) {
	err := req.ParseForm()
	if err != nil {
		log.Fatalln(err)
	}
	data := struct {
		Method        string
		URL           *url.URL
		Submissions   map[string][]string
		Header        http.Header
		Host          string
		ContentLength int64
	}{
		req.Method,
		req.URL,
		req.Form,
		req.Header,
		req.Host,
		req.ContentLength,
	}
	tpl.ExecuteTemplate(w, "index.gohtml", data)
}
var tpl *template.Template
func init() {
	tpl = template.Must(template.ParseFiles("index.gohtml"))
}
func main() {
	var d hotdog
	http.ListenAndServe(":8080", d)
}
package main
import (
	"fmt"
	"net/http"
)
type hotdog int
func (m hotdog) ServeHTTP(w http.ResponseWriter, req *http.Request) {
	w.Header().Set("Mcleod-Key", "this is from mcleod")
	w.Header().Set("Content-Type", "text/html; charset=utf-8")
	fmt.Fprintln(w, "<h1>Any code you want in this func</h1>")
}
func main() {
	var d hotdog
	http.ListenAndServe(":8080", d)
}            
            
Net Http ServerMux


package main
import (
  "io"
  "net/http"
)
type hotdog int
func (m hotdog) ServeHTTP(w http.ResponseWriter, req *http.Request) {
  switch req.URL.Path {
  case "/dog":
    io.WriteString(w, "doggy doggy doggy")
  case "/cat":
    io.WriteString(w, "kitty kitty kitty")
  }
}
func main() {
  var d hotdog
  http.ListenAndServe(":8080", d)
}            
// -------------------------
type hotdog int
func (d hotdog) ServeHTTP(res http.ResponseWriter, req *http.Request) {
	io.WriteString(res, "dog dog dog")
}
type hotcat int
func (c hotcat) ServeHTTP(res http.ResponseWriter, req *http.Request) {
	io.WriteString(res, "cat cat cat")
}
func main() {
	var d hotdog
	var c hotcat
	mux := http.NewServeMux()
	mux.Handle("/dog/", d)
	mux.Handle("/cat", c)
	http.ListenAndServe(":8080", mux)
}
// -------------------------
type hotdog int
func (d hotdog) ServeHTTP(res http.ResponseWriter, req *http.Request) {
	io.WriteString(res, "dog dog dog")
}
type hotcat int
func (c hotcat) ServeHTTP(res http.ResponseWriter, req *http.Request) {
	io.WriteString(res, "cat cat cat")
}
func main() {
	var d hotdog
	var c hotcat
	http.Handle("/dog", d)
	http.Handle("/cat", c)
	http.ListenAndServe(":8080", nil)
}
// -------------------------
package main
import (
	"io"
	"net/http"
)
func d(res http.ResponseWriter, req *http.Request) {
	io.WriteString(res, "dog dog dog")
}
func c(res http.ResponseWriter, req *http.Request) {
	io.WriteString(res, "cat cat cat")
}
func main() {
	http.HandleFunc("/dog", d)
	http.HandleFunc("/cat", c)
	// http.Handle("/dog", http.HandlerFunc(d))
	// http.Handle("/cat", http.HandlerFunc(c))
	http.ListenAndServe(":8080", nil)
}
            
Third Party Server Mux:


package main
import (
	"fmt"
	"github.com/julienschmidt/httprouter"
	"html/template"
	"log"
	"net/http"
)
var tpl *template.Template
func init() {
	tpl = template.Must(template.ParseGlob("templates/*"))
}
func main() {
	mux := httprouter.New()
	mux.GET("/", index)
	mux.GET("/about", about)
	mux.GET("/contact", contact)
	mux.GET("/apply", apply)
	mux.POST("/apply", applyProcess)
	mux.GET("/user/:name", user)
	mux.GET("/blog/:category/:article", blogRead)
	mux.POST("/blog/:category/:article", blogWrite)
	http.ListenAndServe(":8080", mux)
}
func user(w http.ResponseWriter, req *http.Request, ps httprouter.Params) {
	fmt.Fprintf(w, "USER, %s!\n", ps.ByName("name"))
}
func blogRead(w http.ResponseWriter, req *http.Request, ps httprouter.Params) {
	fmt.Fprintf(w, "READ CATEGORY, %s!\n", ps.ByName("category"))
	fmt.Fprintf(w, "READ ARTICLE, %s!\n", ps.ByName("article"))
}
func blogWrite(w http.ResponseWriter, req *http.Request, ps httprouter.Params) {
	fmt.Fprintf(w, "WRITE CATEGORY, %s!\n", ps.ByName("category"))
	fmt.Fprintf(w, "WRITE ARTICLE, %s!\n", ps.ByName("article"))
}
func index(w http.ResponseWriter, req *http.Request, _ httprouter.Params) {
	err := tpl.ExecuteTemplate(w, "index.gohtml", nil)
	HandleError(w, err)
}
func about(w http.ResponseWriter, req *http.Request, _ httprouter.Params) {
	err := tpl.ExecuteTemplate(w, "about.gohtml", nil)
	HandleError(w, err)
}
func contact(w http.ResponseWriter, req *http.Request, _ httprouter.Params) {
	err := tpl.ExecuteTemplate(w, "contact.gohtml", nil)
	HandleError(w, err)
}
func apply(w http.ResponseWriter, req *http.Request, _ httprouter.Params) {
	err := tpl.ExecuteTemplate(w, "apply.gohtml", nil)
	HandleError(w, err)
}
func applyProcess(w http.ResponseWriter, req *http.Request, _ httprouter.Params) {
	err := tpl.ExecuteTemplate(w, "applyProcess.gohtml", nil)
	HandleError(w, err)
}
func HandleError(w http.ResponseWriter, err error) {
	if err != nil {
		http.Error(w, err.Error(), http.StatusInternalServerError)
		log.Fatalln(err)
	}
}            
            
Serving Files:


package main
import (
	"io"
	"net/http"
	"os"
)
func main() {
	http.HandleFunc("/", dog)
	http.HandleFunc("/toby.jpg", dogPic)
	http.ListenAndServe(":8080", nil)
}
func dog(w http.ResponseWriter, req *http.Request) {
	w.Header().Set("Content-Type", "text/html; charset=utf-8")
	io.WriteString(w, `
	<img src="/toby.jpg">
	`)
}
func dogPic(w http.ResponseWriter, req *http.Request) {
	f, err := os.Open("toby.jpg")
	if err != nil {
		http.Error(w, "file not found", 404)
		return
	}
	defer f.Close()
	// io.Copy(w, f)
  // fi, err := f.Stat()
	// if err != nil {
	// 	http.Error(w, "file not found", 404)
	// 	return
	// }
	// http.ServeContent(w, req, f.Name(), fi.ModTime(), f)
}
func main() {
	http.HandleFunc("/", dog)
	http.HandleFunc("/toby.jpg", dogPic)
  http.Handle("/assets/", http.StripPrefix("/assets", http.FileServer(http.Dir("./assets"))))
	io.WriteString(w, `<img src="/assets/toby.jpg">`)
	http.ListenAndServe(":8080", nil)
}
func dog(w http.ResponseWriter, req *http.Request) {
	w.Header().Set("Content-Type", "text/html; charset=utf-8")
	io.WriteString(w, `<img src="toby.jpg">`)
}
func dogPic(w http.ResponseWriter, req *http.Request) {
	http.ServeFile(w, req, "toby.jpg")
	log.Fatal(http.ListenAndServe(":8080", http.FileServer(http.Dir("."))))
}
// serveFile serveContent 
            
Not Found Handler:

package main import ( "fmt" "net/http" ) func main() { http.HandleFunc("/", foo) http.Handle("/favicon.ico", http.NotFoundHandler()) http.ListenAndServe(":8080", nil) } func foo(w http.ResponseWriter, req *http.Request) { fmt.Println(req.URL.Path) fmt.Fprintln(w, "go look at your terminal") }

AppEngine Deploy


index.html + .css +.img

app.yaml

runtime: go113

handlers:
- url: /.*
  script: auto
  secure: always

main.go

package main
import "net/http"
func main(){
	http.Handle("/", http.FileServer(http.Dir(".")))
	http.ListenAndServe(":8080", nil)
}

            

package main
import (
	"fmt"
	"net/http"
)
func main() {
	http.HandleFunc("/", foo)
	http.Handle("/favicon.ico", http.NotFoundHandler())
	http.ListenAndServe(":8080", nil)
}
func foo(w http.ResponseWriter, req *http.Request) {
	v := req.FormValue("q")
	fmt.Fprintln(w, "Do my search: "+v)
}              
              


package main import ( "html/template" "log" "net/http" ) var tpl *template.Template func init() { tpl = template.Must(template.ParseGlob("templates/*")) } type person struct { FirstName string LastName string Subscribed bool } func main() { http.HandleFunc("/", foo) http.Handle("/favicon.ico", http.NotFoundHandler()) http.ListenAndServe(":8080", nil) } func foo(w http.ResponseWriter, req *http.Request) { f := req.FormValue("first") l := req.FormValue("last") s := req.FormValue("subscribe") == "on" err := tpl.ExecuteTemplate(w, "index.gohtml", person{f, l, s}) if err != nil { http.Error(w, err.Error(), 500) log.Fatalln(err) } } templates/index.gohtml index.gohtml {{template "header"}} <form method="POST"> <label for="firstName">First Name</label> <input type="text" id="firstName" name="first"> <br> <label for="lastName">Last Name</label> <input type="text" id="lastName" name="last"> <br> <label for="sub">Subscribe</label> <input type="checkbox" id="sub" name="subscribe"> <br> <input type="submit"> </form> <br> <h1>First: {{.FirstName}}</h1> <h1>Last: {{.LastName}}</h1> <h1>Subscribed: {{.Subscribed}}</h1> {{template "footer"}} include-footer.gohtml {{define "header"}} <!doctype html> <html lang="en"> <head> <meta charset="UTF-8"> <title>Document</title> </head> <body> {{end}} include-header.gohtml {{define "footer"}} <h1>copyright McLeod</h1> </body> </html> {{end}}

Form File


package main
import (
	"fmt"
	"html/template"
	"io/ioutil"
	"net/http"
	"os"
	"path/filepath"
)
var tpl *template.Template
func init() {
	tpl = template.Must(template.ParseGlob("templates/*"))
}
func main() {
	http.HandleFunc("/", foo)
	http.Handle("/favicon.ico", http.NotFoundHandler())
	http.ListenAndServe(":8080", nil)
}
func foo(w http.ResponseWriter, req *http.Request) {
	var s string
	if req.Method == http.MethodPost {
		f, h, err := req.FormFile("q")
		if err != nil {
			http.Error(w, err.Error(), http.StatusInternalServerError)
			return
		}
		defer f.Close()
		fmt.Println("\nfile:", f, "\nheader:", h, "\nerr", err)
		bs, err := ioutil.ReadAll(f)
		if err != nil {
			http.Error(w, err.Error(), http.StatusInternalServerError)
			return
		}
		s = string(bs)
		dst, err := os.Create(filepath.Join("./user/", h.Filename))
		if err != nil {
			http.Error(w, err.Error(), http.StatusInternalServerError)
			return
		}
		defer dst.Close()
		_, err = dst.Write(bs)
		if err != nil {
			http.Error(w, err.Error(), http.StatusInternalServerError)
			return
		}
	}
	w.Header().Set("Content-Type", "text/html; charset=utf-8")
	tpl.ExecuteTemplate(w, "index.gohtml", s)
}              
              
Enctype (type="text/plain")


	http.HandleFunc("/", foo)
  func foo(w http.ResponseWriter, req *http.Request) {
    bs := make([]byte, req.ContentLength)
    req.Body.Read(bs)
    body := string(bs)
    err := tpl.ExecuteTemplate(w, "index.gohtml", body)
    if err != nil {
      http.Error(w, err.Error(), 500)
      log.Fatalln(err)
    }
  }            
            
Enctype (type="application/x-www-form-urlencoded")


<form method="POST" enctype="application/x-www-form-urlencoded">
<label for="firstName">First Name</label>
<input type="text" id="firstName" name="first">
<br>
<label for="lastName">Last Name</label>
<input type="text" id="lastName" name="last">
<br>
<label for="sub">Subscribed</label>
<input type="checkbox" id="sub" name="subscribe">
<br>
<input type="submit">
</form>
func main() {
	http.HandleFunc("/", foo)
	http.Handle("/favicon.ico", http.NotFoundHandler())
	http.ListenAndServe(":8080", nil)
}
func foo(w http.ResponseWriter, req *http.Request) {
	bs := make([]byte, req.ContentLength)
	req.Body.Read(bs)
	body := string(bs)
	err := tpl.ExecuteTemplate(w, "index.gohtml", body)
	if err != nil {
		http.Error(w, err.Error(), 500)
		log.Fatalln(err)
	}
}
Enctype (type="multipart/form-data")


<form method="POST" enctype="multipart/form-data">
<label for="firstName">First Name</label>
<input type="text" id="firstName" name="first">
<br>
<label for="lastName">Last Name</label>
<input type="text" id="lastName" name="last">
<br>
<label for="sub">Subscribed</label>
<input type="checkbox" id="sub" name="subscribe">
<br>
<input type="submit">
</form>
func main() {
	http.HandleFunc("/", foo)
	http.Handle("/favicon.ico", http.NotFoundHandler())
	http.ListenAndServe(":8080", nil)
}
func foo(w http.ResponseWriter, req *http.Request) {
	bs := make([]byte, req.ContentLength)
	req.Body.Read(bs)
	body := string(bs)
	err := tpl.ExecuteTemplate(w, "index.gohtml", body)
	if err != nil {
		http.Error(w, err.Error(), 500)
		log.Fatalln(err)
	}
}
Redirect


	http.Redirect(w, req, "/", http.StatusSeeOther)
	http.Redirect(w, req, "/", http.StatusTemporaryRedirect)
	http.Redirect(w, req, "/", http.StatusMovedPermanently)
  // --------
  <form method="POST" action="/bar">
    <input type="text" name="fname" title="fname">
    <input type="submit">
  </form>
	w.Header().Set("Location", "/")
	w.WriteHeader(http.StatusSeeOther)
Cookies


package main
import (
	"fmt"
	"net/http"
)
func main() {
	http.HandleFunc("/", set)
	http.HandleFunc("/read", read)
	http.Handle("/favicon.ico", http.NotFoundHandler())
	http.ListenAndServe(":8080", nil)
}
func set(w http.ResponseWriter, req *http.Request) {
	http.SetCookie(w, &http.Cookie{
		Name:  "my-cookie",
		Value: "some value",
		Path: "/",
	})
	fmt.Fprintln(w, "COOKIE WRITTEN - CHECK YOUR BROWSER")
	fmt.Fprintln(w, "in chrome go to: dev tools / application / cookies")
}
func read(w http.ResponseWriter, req *http.Request) {
	c1, err := req.Cookie("my-cookie")
	if err != nil {
		log.Println(err)
	} else {
		fmt.Fprintln(w, "YOUR COOKIE #1:", c1)
	}
	c2, err := req.Cookie("general")
	if err != nil {
		log.Println(err)
	} else {
		fmt.Fprintln(w, "YOUR COOKIE #2:", c2)
	}
	c3, err := req.Cookie("specific")
	if err != nil {
		log.Println(err)
	} else {
		fmt.Fprintln(w, "YOUR COOKIE #3:", c3)
	}
}
func expire(w http.ResponseWriter, req *http.Request) {
	c, err := req.Cookie("session")
	if err != nil {
		http.Redirect(w, req, "/set", http.StatusSeeOther)
		return
	}
	c.MaxAge = -1 // delete cookie
	http.SetCookie(w, c)
	http.Redirect(w, req, "/", http.StatusSeeOther)
}
            
Sessions, UUID, Middlewares And Bycrypt


main.go

package main

import (
	"github.com/satori/go.uuid"
	"golang.org/x/crypto/bcrypt"
	"html/template"
	"net/http"
	"time"
)

type user struct {
	UserName string
	Password []byte
	First    string
	Last     string
	Role     string
}

type session struct {
	un           string
	lastActivity time.Time
}

var tpl *template.Template
var dbUsers = map[string]user{}      
var dbSessions = map[string]session{} 
var dbSessionsCleaned time.Time

const sessionLength int = 30

func init() {
	tpl = template.Must(template.ParseGlob("templates/*"))
	dbSessionsCleaned = time.Now()
}

func main() {
	http.HandleFunc("/", index)
	http.HandleFunc("/bar", bar)
	http.HandleFunc("/signup", signup)
	http.HandleFunc("/login", login)
	http.HandleFunc("/logout", authorized(logout))
	http.Handle("/favicon.ico", http.NotFoundHandler())
	http.ListenAndServe(":8080", nil)
}

func index(w http.ResponseWriter, req *http.Request) {
	u := getUser(w, req)
	showSessions()
	tpl.ExecuteTemplate(w, "index.gohtml", u)
}

func bar(w http.ResponseWriter, req *http.Request) {
	u := getUser(w, req)
	if !alreadyLoggedIn(w, req) {
		http.Redirect(w, req, "/", http.StatusSeeOther)
		return
	}
	if u.Role != "007" {
		http.Error(w, "You must be 007 to enter the bar", http.StatusForbidden)
		return
	}
	showSessions() // for demonstration purposes
	tpl.ExecuteTemplate(w, "bar.gohtml", u)
}

func signup(w http.ResponseWriter, req *http.Request) {
	if alreadyLoggedIn(w, req) {
		http.Redirect(w, req, "/", http.StatusSeeOther)
		return
	}
	var u user
	if req.Method == http.MethodPost {
		un := req.FormValue("username")
		p := req.FormValue("password")
		f := req.FormValue("firstname")
		l := req.FormValue("lastname")
		r := req.FormValue("role")
		if _, ok := dbUsers[un]; ok {
			http.Error(w, "Username already taken", http.StatusForbidden)
			return
		}
		sID, _ := uuid.NewV4()
		c := &http.Cookie{
			Name:  "session",
			Value: sID.String(),
		}
		c.MaxAge = sessionLength
		http.SetCookie(w, c)
		dbSessions[c.Value] = session{un, time.Now()}
		bs, err := bcrypt.GenerateFromPassword([]byte(p), bcrypt.MinCost)
		if err != nil {
			http.Error(w, "Internal server error", http.StatusInternalServerError)
			return
		}
		u = user{un, bs, f, l, r}
		dbUsers[un] = u
		http.Redirect(w, req, "/", http.StatusSeeOther)
		return
	}
	showSessions() // for demonstration purposes
	tpl.ExecuteTemplate(w, "signup.gohtml", u)
}

func login(w http.ResponseWriter, req *http.Request) {
	if alreadyLoggedIn(w, req) {
		http.Redirect(w, req, "/", http.StatusSeeOther)
		return
	}
	var u user
	if req.Method == http.MethodPost {
		un := req.FormValue("username")
		p := req.FormValue("password")
		u, ok := dbUsers[un]
		if !ok {
			http.Error(w, "Username and/or password do not match", http.StatusForbidden)
			return
		}
		err := bcrypt.CompareHashAndPassword(u.Password, []byte(p))
		if err != nil {
			http.Error(w, "Username and/or password do not match", http.StatusForbidden)
			return
		}
		sID, _ := uuid.NewV4()
		c := &http.Cookie{
			Name:  "session",
			Value: sID.String(),
		}
		c.MaxAge = sessionLength
		http.SetCookie(w, c)
		dbSessions[c.Value] = session{un, time.Now()}
		http.Redirect(w, req, "/", http.StatusSeeOther)
		return
	}
	showSessions() 
	tpl.ExecuteTemplate(w, "login.gohtml", u)
}

func logout(w http.ResponseWriter, req *http.Request) {
	c, _ := req.Cookie("session")
	delete(dbSessions, c.Value)
	// remove the cookie
	c = &http.Cookie{
		Name:   "session",
		Value:  "",
		MaxAge: -1,
	}
	http.SetCookie(w, c)
	if time.Now().Sub(dbSessionsCleaned) > (time.Second * 30) {
		go cleanSessions()
	}
	http.Redirect(w, req, "/login", http.StatusSeeOther)
}

func authorized(h http.HandlerFunc) http.HandlerFunc {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		if !alreadyLoggedIn(w, r) {
			http.Redirect(w, r, "/", http.StatusSeeOther)
			return
		}
		h.ServeHTTP(w, r)
	})
}

session.go

package main

import (
	"fmt"
	"github.com/satori/go.uuid"
	"net/http"
	"time"
)

func getUser(w http.ResponseWriter, req *http.Request) user {
	c, err := req.Cookie("session")
	if err != nil {
		sID, _ := uuid.NewV4()
		c = &http.Cookie{
			Name:  "session",
			Value: sID.String(),
		}

	}
	c.MaxAge = sessionLength
	http.SetCookie(w, c)
	var u user
	if s, ok := dbSessions[c.Value]; ok {
		s.lastActivity = time.Now()
		dbSessions[c.Value] = s
		u = dbUsers[s.un]
	}
	return u
}
func alreadyLoggedIn(w http.ResponseWriter, req *http.Request) bool {
	c, err := req.Cookie("session")
	if err != nil {
		return false
	}
	s, ok := dbSessions[c.Value]
	if ok {
		s.lastActivity = time.Now()
		dbSessions[c.Value] = s
	}
	_, ok = dbUsers[s.un]
	c.MaxAge = sessionLength
	http.SetCookie(w, c)
	return ok
}
func cleanSessions() {
	fmt.Println("BEFORE CLEAN") 
	showSessions()              
	for k, v := range dbSessions {
		if time.Now().Sub(v.lastActivity) > (time.Second * 30) {
			delete(dbSessions, k)
		}
	}
	dbSessionsCleaned = time.Now()
	fmt.Println("AFTER CLEAN") 
	showSessions()            
}
func showSessions() {
	fmt.Println("********")
	for k, v := range dbSessions {
		fmt.Println(k, v.un)
	}
	fmt.Println("")
}
              
Base64


package main
import (
	"encoding/base64"
	"fmt"
	"log"
)
func main() {
	s := "Love is but a song to sing Fear's the way we die You can make the mountains ring Or make the angels cry Though the bird is on the wing And you may not know why Come on people now Smile on your brother Everybody get together Try to love one another Right now"
	s64 := base64.StdEncoding.EncodeToString([]byte(s))
	fmt.Println(s64)
	bs, err := base64.StdEncoding.DecodeString(s64)
	if err != nil {
		log.Fatalln("I'm giving her all she's got Captain!", err)
	}
	fmt.Println(string(bs))
}
              
Context

A Context carries deadlines, cancellation signals, and other request-scoped values across API boundaries and goroutines.

A context.Context is created for each request by the net/http machinery, and is available with the Context() method

Wait for a few seconds before sending a reply to the client. This could simulate some work the server is doing. While working, keep an eye on the context’s Done() channel for a signal that we should cancel the work and return as soon as possible.


package main
import (
	"fmt"
	"net/http"
	"time"
)
func hello(w http.ResponseWriter, req *http.Request) {
	ctx := req.Context()
	fmt.Println("server: hello handler started")
	defer fmt.Println("server: hello handler ended")
	select {
	case <-time.After(10 * time.Second):
		fmt.Fprintf(w, "hello\n")
	case <-ctx.Done():
		err := ctx.Err()
		fmt.Println("server:", err)
		internalError := http.StatusInternalServerError
		http.Error(w, err.Error(), internalError)
	}
}
func main() {
	http.HandleFunc("/hello", hello)
	http.ListenAndServe(":8090", nil)
}
server: hello handler started
server: context canceled
server: hello handler ended              

package main
import (
	"context"
	"fmt"
	"log"
	"net/http"
)
func main() {
	http.HandleFunc("/", foo)
	http.HandleFunc("/bar", bar)
	http.Handle("/favicon.ico", http.NotFoundHandler())
	http.ListenAndServe(":8080", nil)
}
func foo(w http.ResponseWriter, req *http.Request) {
	ctx := req.Context()
	ctx = context.WithValue(ctx, "userID", 777)
	ctx = context.WithValue(ctx, "fname", "Bond")
	results := dbAccess(ctx)
	fmt.Fprintln(w, results)
}
func dbAccess(ctx context.Context) int {
	uid := ctx.Value("userID").(int)
	return uid
}
func bar(w http.ResponseWriter, req *http.Request) {
	ctx := req.Context()
	log.Println(ctx)
	fmt.Fprintln(w, ctx)
}
HTTPS


package main
import (
	"crypto/tls"
	"fmt"
	"log"
	"net/http"
	"rsc.io/letsencrypt"
)
func main() {
	http.HandleFunc("/", foo)
	var m letsencrypt.Manager
	if err := m.CacheFile("letsencrypt.cache"); err != nil {
		log.Fatalln(err)
	}
	go http.ListenAndServe(":8080", http.HandlerFunc(letsencrypt.RedirectHTTP))
	srv := &http.Server{
		Addr: ":10443",
		TLSConfig: &tls.Config{
			GetCertificate: m.GetCertificate,
		},
	}
	log.Fatalln(srv.ListenAndServeTLS("", ""))
}
func foo(res http.ResponseWriter, req *http.Request) {
	fmt.Fprintln(res, "Hello TLS")
}
JSON


import (
	"encoding/json"
	"log"
	"net/http"
)
type person struct {
	Fname string
	Lname string
	Items []string
}
w.Header().Set("Content-Type", "application/json")
p1 := person{
  Fname: "James",
  Lname: "Bond",
  Items: []string{"Suit", "Gun", "Wry sense of humor"},
}
j, err := json.Marshal(p1)
if err != nil {
  log.Println(err)
}
w.Write(j)
w.Header().Set("Content-Type", "application/json")
p1 := person{
  Fname: "James",
  Lname: "Bond",
  Items: []string{"Suit", "Gun", "Wry sense of humor"},
}
err := json.NewEncoder(w).Encode(p1)
if err != nil {
  log.Println(err)
}

package main
import (
	"encoding/json"
	"fmt"
	"log"
)
type thumbnail struct {
	URL           string
	Height, Width int
}
type img struct {
	Width, Height int
	Title         string
	Thumbnail     thumbnail
	Animated      bool
	IDs           []int
}
func main() {
	var data img
	rcvd := `{"Width":800,"Height":600,"Title":"View from 15th Floor","Thumbnail":{"Url":"http://www.example.com/image/481989943","Height":125,"Width":100},"Animated":false,"IDs":[116,943,234,38793]}`
	err := json.Unmarshal([]byte(rcvd), &data)
	if err != nil {
		log.Fatalln("error unmarshalling", err)
	}
	fmt.Println(data)
	for i, v := range data.IDs {
		fmt.Println(i, v)
	}
	fmt.Println(data.Thumbnail.URL)
}

package main
import (
	"encoding/json"
	"fmt"
	"log"
)
type city struct {
	Bali       string  `json:"Postal"`
	Kauai      float64 `json:"Latitude"`
	Maui       float64 `json:"Longitude"`
	Java       string  `json:"Address"`
	NewZealand string  `json:"City"`
	Skye       string  `json:"State"`
	Oahu       string  `json:"Zip"`
	Hawaii     string  `json:"Country"`
}
type cities []city
func main() {
	var data cities
	rcvd := `[{"Postal":"zip","Latitude":37.7668,"Longitude":-122.3959,"Address":"","City":"SAN FRANCISCO","State":"CA","Zip":"94107","Country":"US"},{"Postal":"zip","Latitude":37.371991,"Longitude":-122.02602,"Address":"","City":"SUNNYVALE","State":"CA","Zip":"94085","Country":"US"}]`
	err := json.Unmarshal([]byte(rcvd), &data)
	if err != nil {
		log.Fatalln(err)
	}
	fmt.Println(data)
	fmt.Println(data[1].Kauai)
}
rcvd := `"Todd"`
rcvd := nil
err := json.Unmarshal([]byte(rcvd), &data)
              
MongoDB


main.go
package main
import (
	"github.com/julienschmidt/httprouter"
	"gopkg.in/mgo.v2"
	"net/http"
	"github.com/GoesToEleven/golang-web-dev/042_mongodb/05_mongodb/05_update-user-controllers-delete/controllers"
)
func main() {
	r := httprouter.New()
	uc := controllers.NewUserController(getSession())
	r.GET("/user/:id", uc.GetUser)
	r.POST("/user", uc.CreateUser)
	r.DELETE("/user/:id", uc.DeleteUser)
	http.ListenAndServe("localhost:8080", r)
}
func getSession() *mgo.Session {
	s, err := mgo.Dial("mongodb://localhost")
	if err != nil {
		panic(err)
	}
	return s
}
models/user.go

package models
import "gopkg.in/mgo.v2/bson"
type User struct {
	Id     bson.ObjectId `json:"id" bson:"_id"`
	Name   string        `json:"name" bson:"name"`
	Gender string        `json:"gender" bson:"gender"`
	Age    int           `json:"age" bson:"age"`
}

controllers/user.go

package controllers

import (
	"encoding/json"
	"fmt"
	"github.com/GoesToEleven/golang-web-dev/042_mongodb/05_mongodb/05_update-user-controllers-delete/models"
	"github.com/julienschmidt/httprouter"
	"gopkg.in/mgo.v2"
	"gopkg.in/mgo.v2/bson"
	"net/http"
)
type UserController struct {
	session *mgo.Session
}
func NewUserController(s *mgo.Session) *UserController {
	return &UserController{s}
}
func (uc UserController) GetUser(w http.ResponseWriter, r *http.Request, p httprouter.Params) {
	id := p.ByName("id")
	if !bson.IsObjectIdHex(id) {
		w.WriteHeader(http.StatusNotFound) // 404
		return
	}
	oid := bson.ObjectIdHex(id)
	u := models.User{}
	if err := uc.session.DB("go-web-dev-db").C("users").FindId(oid).One(&u); err != nil {
		w.WriteHeader(404)
		return
	}
	uj, err := json.Marshal(u)
	if err != nil {
		fmt.Println(err)
	}
	w.Header().Set("Content-Type", "application/json")
	w.WriteHeader(http.StatusOK) // 200
	fmt.Fprintf(w, "%s\n", uj)
}
func (uc UserController) CreateUser(w http.ResponseWriter, r *http.Request, _ httprouter.Params) {
	u := models.User{}
	json.NewDecoder(r.Body).Decode(&u)
	u.Id = bson.NewObjectId()
	uc.session.DB("go-web-dev-db").C("users").Insert(u)
	uj, err := json.Marshal(u)
	if err != nil {
		fmt.Println(err)
	}
	w.Header().Set("Content-Type", "application/json")
	w.WriteHeader(http.StatusCreated) // 201
	fmt.Fprintf(w, "%s\n", uj)
}
func (uc UserController) DeleteUser(w http.ResponseWriter, r *http.Request, p httprouter.Params) {
	id := p.ByName("id")
	if !bson.IsObjectIdHex(id) {
		w.WriteHeader(404)
		return
	}
	oid := bson.ObjectIdHex(id)
	if err := uc.session.DB("go-web-dev-db").C("users").RemoveId(oid); err != nil {
		w.WriteHeader(404)
		return
	}
	w.WriteHeader(http.StatusOK) // 200
	fmt.Fprint(w, "Deleted user", oid, "\n")
}
Code Organisation


package main
import (
	"database/sql"
	"fmt"
	_ "github.com/lib/pq"
	"html/template"
	"net/http"
	"strconv"
)
var db *sql.DB
var tpl *template.Template
func init() {
	var err error
	db, err = sql.Open("postgres", "postgres://bond:password@localhost/bookstore?sslmode=disable")
	if err != nil {
		panic(err)
	}
	if err = db.Ping(); err != nil {
		panic(err)
	}
	fmt.Println("You connected to your database.")
	tpl = template.Must(template.ParseGlob("templates/*.gohtml"))
}
type Book struct {
	Isbn   string
	Title  string
	Author string
	Price  float32
}
func main() {
	http.HandleFunc("/", index)
	http.HandleFunc("/books", booksIndex)
	http.HandleFunc("/books/show", booksShow)
	http.HandleFunc("/books/create", booksCreateForm)
	http.HandleFunc("/books/create/process", booksCreateProcess)
	http.HandleFunc("/books/update", booksUpdateForm)
	http.HandleFunc("/books/update/process", booksUpdateProcess)
	http.HandleFunc("/books/delete/process", booksDeleteProcess)
	http.ListenAndServe(":8080", nil)
}
func index(w http.ResponseWriter, r *http.Request) {
	http.Redirect(w, r, "/books", http.StatusSeeOther)
}
func booksIndex(w http.ResponseWriter, r *http.Request) {
	if r.Method != "GET" {
		http.Error(w, http.StatusText(405), http.StatusMethodNotAllowed)
		return
	}
	rows, err := db.Query("SELECT * FROM books")
	if err != nil {
		http.Error(w, http.StatusText(500), 500)
		return
	}
	defer rows.Close()
	bks := make([]Book, 0)
	for rows.Next() {
		bk := Book{}
		err := rows.Scan(&bk.Isbn, &bk.Title, &bk.Author, &bk.Price) // order matters
		if err != nil {
			http.Error(w, http.StatusText(500), 500)
			return
		}
		bks = append(bks, bk)
	}
	if err = rows.Err(); err != nil {
		http.Error(w, http.StatusText(500), 500)
		return
	}
	tpl.ExecuteTemplate(w, "books.gohtml", bks)
}
func booksShow(w http.ResponseWriter, r *http.Request) {
	if r.Method != "GET" {
		http.Error(w, http.StatusText(405), http.StatusMethodNotAllowed)
		return
	}
	isbn := r.FormValue("isbn")
	if isbn == "" {
		http.Error(w, http.StatusText(400), http.StatusBadRequest)
		return
	}
	row := db.QueryRow("SELECT * FROM books WHERE isbn = $1", isbn)
	bk := Book{}
	err := row.Scan(&bk.Isbn, &bk.Title, &bk.Author, &bk.Price)
	switch {
	case err == sql.ErrNoRows:
		http.NotFound(w, r)
		return
	case err != nil:
		http.Error(w, http.StatusText(500), http.StatusInternalServerError)
		return
	}
	tpl.ExecuteTemplate(w, "show.gohtml", bk)
}
func booksCreateForm(w http.ResponseWriter, r *http.Request) {
	tpl.ExecuteTemplate(w, "create.gohtml", nil)
}
func booksCreateProcess(w http.ResponseWriter, r *http.Request) {
	if r.Method != "POST" {
		http.Error(w, http.StatusText(405), http.StatusMethodNotAllowed)
		return
	}
	bk := Book{}
	bk.Isbn = r.FormValue("isbn")
	bk.Title = r.FormValue("title")
	bk.Author = r.FormValue("author")
	p := r.FormValue("price")
	if bk.Isbn == "" || bk.Title == "" || bk.Author == "" || p == "" {
		http.Error(w, http.StatusText(400), http.StatusBadRequest)
		return
	}
	f64, err := strconv.ParseFloat(p, 32)
	if err != nil {
		http.Error(w, http.StatusText(406)+"Please hit back and enter a number for the price", http.StatusNotAcceptable)
		return
	}
	bk.Price = float32(f64)
	_, err = db.Exec("INSERT INTO books (isbn, title, author, price) VALUES ($1, $2, $3, $4)", bk.Isbn, bk.Title, bk.Author, bk.Price)
	if err != nil {
		http.Error(w, http.StatusText(500), http.StatusInternalServerError)
		return
	}
	tpl.ExecuteTemplate(w, "created.gohtml", bk)
}
func booksUpdateForm(w http.ResponseWriter, r *http.Request) {
	if r.Method != "GET" {
		http.Error(w, http.StatusText(405), http.StatusMethodNotAllowed)
		return
	}
	isbn := r.FormValue("isbn")
	if isbn == "" {
		http.Error(w, http.StatusText(400), http.StatusBadRequest)
		return
	}
	row := db.QueryRow("SELECT * FROM books WHERE isbn = $1", isbn)
	bk := Book{}
	err := row.Scan(&bk.Isbn, &bk.Title, &bk.Author, &bk.Price)
	switch {
	case err == sql.ErrNoRows:
		http.NotFound(w, r)
		return
	case err != nil:
		http.Error(w, http.StatusText(500), http.StatusInternalServerError)
		return
	}
	tpl.ExecuteTemplate(w, "update.gohtml", bk)
}
func booksUpdateProcess(w http.ResponseWriter, r *http.Request) {
	if r.Method != "POST" {
		http.Error(w, http.StatusText(405), http.StatusMethodNotAllowed)
		return
	}
	bk := Book{}
	bk.Isbn = r.FormValue("isbn")
	bk.Title = r.FormValue("title")
	bk.Author = r.FormValue("author")
	p := r.FormValue("price")
	if bk.Isbn == "" || bk.Title == "" || bk.Author == "" || p == "" {
		http.Error(w, http.StatusText(400), http.StatusBadRequest)
		return
	}
	f64, err := strconv.ParseFloat(p, 32)
	if err != nil {
		http.Error(w, http.StatusText(406)+"Please hit back and enter a number for the price", http.StatusNotAcceptable)
		return
	}
	bk.Price = float32(f64)
	_, err = db.Exec("UPDATE books SET isbn = $1, title=$2, author=$3, price=$4 WHERE isbn=$1;", bk.Isbn, bk.Title, bk.Author, bk.Price)
	if err != nil {
		http.Error(w, http.StatusText(500), http.StatusInternalServerError)
		return
	}
	tpl.ExecuteTemplate(w, "updated.gohtml", bk)
}
func booksDeleteProcess(w http.ResponseWriter, r *http.Request) {
	if r.Method != "GET" {
		http.Error(w, http.StatusText(405), http.StatusMethodNotAllowed)
		return
	}
	isbn := r.FormValue("isbn")
	if isbn == "" {
		http.Error(w, http.StatusText(400), http.StatusBadRequest)
		return
	}
	_, err := db.Exec("DELETE FROM books WHERE isbn=$1;", isbn)
	if err != nil {
		http.Error(w, http.StatusText(500), http.StatusInternalServerError)
		return
	}
	http.Redirect(w, r, "/books", http.StatusSeeOther)
}
Organise the above code in various sub packages
  
Google Cloud


app.yaml

application: astute-curve-100822
version: 1
runtime: go
api_version: go1

handlers:
- url: /admin/.*
  script: _go_app
  login: admin
- url: /.*
  script: _go_app
  login: required            
 
main.go
package main
import (
	"fmt"
	"net/http"
	"google.golang.org/appengine"
	"google.golang.org/appengine/user"
)
func init() {
	http.HandleFunc("/", index)
	http.HandleFunc("/admin/", admin)
}
func index(w http.ResponseWriter, r *http.Request) {
	ctx := appengine.NewContext(r)
	u := user.Current(ctx)
	url, err := user.LogoutURL(ctx, "/")
	if err != nil {
		http.Error(w, err.Error(), http.StatusInternalServerError)
		return
	}
	w.Header().Set("Content-Type", "text/html; charset=UTF-8")
	fmt.Fprintf(w, `Welcome, %s! (<a href="%s">sign out</a>)`, u, url)
}
func admin(w http.ResponseWriter, r *http.Request) {
	ctx := appengine.NewContext(r)
	u := user.Current(ctx)
	url, _ := user.LogoutURL(ctx, "/")
	w.Header().Set("Content-Type", "text/html; charset=UTF-8")
	fmt.Fprintf(w, `Welcome ADMIN, %s! (<a href="%s">sign out</a>)`, u, url)
}
 
Memcache


app.yaml
application: learning-1130
version: 1
runtime: go
api_version: go1
handlers:
- url: /.*
  script: _go_app

main.go
package main
import (
  "fmt"
  "net/http"
  "google.golang.org/appengine"
  "google.golang.org/appengine/memcache"
  "time"
) 
func init() {
  http.HandleFunc("/", index)
} 
func index(w http.ResponseWriter, r *http.Request) {
  ctx := appengine.NewContext(r)
  item1 := memcache.Item{
    Key:        "foo",
    Value:      []byte("bar"),
    Expiration: 10 * time.Second,
  }
  memcache.Set(ctx, &item1)
  item, err := memcache.Get(ctx, "foo")
  if err != nil {
    http.Error(w, err.Error(), http.StatusInternalServerError)
    return
  }
  fmt.Fprintln(w, string(item.Value))
} 
 
Datastore


 package evolved

 import (
   "fmt"
   "net/http"
 
   "google.golang.org/appengine"
   "google.golang.org/appengine/datastore"
 )
 
 func init() {
   http.HandleFunc("/", index)
   http.HandleFunc("/tools", showTools)
 }
 
 type Tool struct {
   Name        string
   Description string
 }

 func index(res http.ResponseWriter, req *http.Request) {
   if req.URL.Path == "/favicon.ico" {
     http.NotFound(res, req)
   }
   res.Header().Set("Content-Type", "text/html")
   if req.Method == "POST" {
     putTool(res, req)
   }
   fmt.Fprintln(res, `
       <form method="POST" action="/">
         <h1>Tool</h1>
         <input type="text" name="name"><br>
         <h1>Description</h1>
         <textarea name="descrip"></textarea>
         <input type="submit">
       </form>`)
 }
 
 func putTool(res http.ResponseWriter, req *http.Request) {
   name := req.FormValue("name")
   descrip := req.FormValue("descrip")
   ctx := appengine.NewContext(req)
   parentKey := datastore.NewKey(ctx, "House", "Garage", 0, nil)
   key := datastore.NewKey(ctx, "Tools", name, 0, parentKey)
   entity := &Tool{
     Name:        name,
     Description: descrip,
   }
   _, err := datastore.Put(ctx, key, entity)
   if err != nil {
     http.Error(res, err.Error(), 500)
     return
   }
 }
 
 func showTools(res http.ResponseWriter, req *http.Request) {
   html := ""
   ctx := appengine.NewContext(req)
   parentKey := datastore.NewKey(ctx, "House", "Garage", 0, nil)
   q := datastore.NewQuery("Tools").Ancestor(parentKey)
   iterator := q.Run(ctx)
   for {
     var entity Tool
     _, err := iterator.Next(&entity)
     if err == datastore.Done {
       break
     } else if err != nil {
       http.Error(res, err.Error(), 500)
       return
     }
     html += `
       <dt>` + entity.Name + `</dt>
       <dd>` + entity.Description + `</dd>
     `
   }
   res.Header().Set("Content-Type", "text/html")
   fmt.Fprintln(res, `<dl>`+html+`</dl>`)
 }
 
 
Cloud Storage: https://github.dev/saiashish9/golang-web-dev

WebRTC

https://webrtc.org

An open framework for a wen that enables Real Time Communication in the browser.

Web Sockets

The WebSocket API is an advanced technology that makes it possible to open a two-way interactive communication session between the user's browser and a server. With this API, you can send messages to a server and receive event-driven responses without having to poll the server for a reply.

Unlike HTTP, where you have to constantly request updates, with websockets, updates are sent immediately when they are available. WebSockets keeps a single, persistent connection open while eliminating latency problems that arise with HTTP request/response-based methods.

WebRTC ( Web Real Time Communication ) is a technology which enables web applications and sites to capture and optionaaly stream audio/ or video as well as to exchange arbitrary data b/w browsers w/o requiring an intermediary. We need js for webrtc at any browser.

It makes use of peer to peer n/w to communicate and share this data. Earlier there was a central point to communicate and share this data.

WebSockets are meant to enable bidirectional communication between a browser and a web server and WebRTC is meant to offer real time communication between browsers (predominantly voice and video communications).

WebRTC apps need a service via which they can exchange network and media metadata, a process known as signaling. However, once signaling has taken place, video/audio/data is streamed directly between clients, avoiding the performance cost of streaming via an intermediary server. They're built on top of http.
WebSocket on the other hand is designed for bi-directional communication between client and server. It is possible to stream audio and video over WebSocket (see here for example), but the technology and APIs are not inherently designed for efficient, robust streaming in the way that WebRTC is.

WebRTC Connection Cycle

Local description is used to describe itself, remote description is used to describe the device on other end of the connection.

We can establish connection between two devices via a intermediate called as signalling server.

SDP and Signalling

The process of signalling can be done w/o any medium. Heck we can even tweet the offer

But in serious terms, we usually use a websocket server beacuse of its duplex communication capabilities.

We can use regular HTTP, but we'll have to use long polling

github.com/gorilla/websocket can use used to establish connection in ho

Session Description Protocol

The configuration of endpoint on a webRTC cction is called a session description.It is expressed using the SDp

The description includes information about the kind of media being sent, its format, the transfer protocol being used the enpoint's IP address and port and other information needed to describe a media transfer enpoint

Offers and ansers are special descriptions.

Each peers keeps two descriptions on hand, the local descripton, describing itslef and the remote description describing the other end of the call

NAT, STUN ( Session Traversal Utilities for NAT(N/W Address Translation) ) & TURN Servers, ICE ( Interactive Connective Establishment ) Candidates

System Design
Configuration Steps:

1. Go to golang.org

2. Download arm based version for m1 mac

3. Execute following statements:

export GOROOT=/usr/local/go
export GOPATH=$HOME/Desktop/folders/projects/go-workspace
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH

5. Afterwards go to golang workspace (i.e., $HOME/Desktop/folders/projects/go-workspace)

6. Execute Following Commands:

mkdir video-chat
cd video-chat
go mod init video-chat-app

7. Place server directory and main.go except client directory

8. Then , excute go build main.go and then go run main.go

9. execute yarn create react-app client at root level. Make use of existing files and execute yarn start.

10. Open localhost:3000 and click at the button

11. Copy and paste the link in a new tab. We'll be able to establish video chat

```
