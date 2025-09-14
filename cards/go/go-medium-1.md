
#meowmorize 

# Group 1 
<!-- Card Start -->

### Front

**What is the main purpose of using `select` in Go?**

### Back

The `select` statement lets a goroutine wait on multiple communication operations (channel sends and receives), proceeding with the one that's ready first.

```go
select { 
  case msg := <-ch1:     
     fmt.Println("Received", msg) 
  case ch2 <- "sending":     
     fmt.Println("Sent successfully") 
}
```


<!-- Card End --> 

<!-- Card Start -->

### Front

**What is channel fanning out in Go?**

### Back

Channel fanning out refers to distributing tasks from a single input channel across multiple goroutines to parallelize workload and increase throughput.
Fan out is used when multiple functions read from the same channel. The reading will stop only when the channel is closed. This characteristic is often used to distribute work amongst a group of workers to parallelize the CPU and I /O.

```go

package main 
import ( 
  "fmt" 
  "sync" 
) 

// generator creates a channel and sends numbers into it 
func generator(nums ...int) <-chan int { 
    myChannel := make(chan int) 
  
    go func() { 
        for _, val := range nums { 
            myChannel <- val 
        } 
        close(myChannel) 
    }() 
    
    return myChannel 
} 

// worker processes data received from the channel 
func worker(id int, ch <-chan int, wg *sync.WaitGroup) { 
    defer wg.Done() 
    for val := range ch { 
        fmt.Printf("Worker %d received: %v\n", id, val) 
    } 
} 

func main() { 
    data := []int{1, 2, 3, 4, 5}
    ch := generator(data...) 
    var wg sync.WaitGroup numWorkers := 3 

// Number of worker goroutines 

// Fan-out: Start multiple workers to process data from the same channel 

    for i := 1; i <= numWorkers; i++ { 
        wg.Add(1) 
        go worker(i, ch, &wg) 
    } 
    wg.Wait() // Wait for all workers to finish 

}
```

https://go.dev/play/p/0QBxnOuVi0J



<!-- Card End --> <!-- Card Start -->

### Front

**What is the primary use of `context.Context` in Go?**

### Back

`context.Context` provides cancellation signals, deadlines/timeouts, and value propagation across API boundaries and goroutine trees.

<!-- Card End -->
<!-- Card Start -->

### Front

**How to propagate a cancellation signal using context? (Example)**

### Back

```go
ctx, cancel := context.WithCancel(context.Background()) 

go func(ctx context.Context) {    
    select {     
        case <-ctx.Done():  
            fmt.Println("Cancelled")     
    } 
}(ctx) 

cancel() // trigger cancellation

```


<!-- Card End --> 
<!-- Card Start -->

### Front

**When would you use `context.WithValue`?**

### Back

To pass request-scoped data implicitly, like request IDs or authentication details, across API boundaries or goroutines.

<!-- Card End --> 
<!-- Card Start -->

### Front

**How do you set a timeout using the context package?**

### Back

```go
ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second) 
defer cancel()  

select { 
  case <-ctx.Done():     
    fmt.Println("Timeout:", ctx.Err()) 
}
```

<!-- Card End --> 
<!-- Card Start -->

### Front

**What's an effective way to handle errors in goroutines?**

### Back

Use an error channel to send errors back to the main goroutine or a central error-handling mechanism.

```go
errCh := make(chan error) 

go func() {     
    if err := doWork(); err != nil {                      errCh <- err     
    } 
}()
```

<!-- Card End --> 

<!-- Card Start -->

### Front

**Buffered channels introduce what potential issue?**

### Back

If a buffered channel becomes full (for sends) or empty (for receives), it can lead to goroutine blocking and backpressure issues.

<!-- Card End --> 

<!-- Card Start -->

### Front

**When might you prefer using buffered channels?**

### Back

When you want decoupling of goroutines, avoiding immediate synchronization, and tolerating bursts of traffic.

<!-- Card End -->

<!-- Card Start -->

### Front

**Channel directionality syntax for send-only channels?**

### Back

 ```go
chan<- int
```

<!-- Card End --> 
<!-- Card Start -->

### Front

**Channel directionality syntax for receive-only channels?**

### Back

```go
<-chan int
```

<!-- Card End --> 
<!-- Card Start -->

### Front

**What's the benefit of specifying channel directionality explicitly?**

### Back

Improves code clarity, safety, and prevents misuse by enforcing constraints at compile time.

<!-- Card End -->
<!-- Card Start -->

### Front

**What does `sync.Mutex` achieve in Go?**

### Back

It ensures mutual exclusion to protect shared resources from concurrent access issues like race conditions.

<!-- Card End -->
<!-- Card Start -->

### Front

**Difference between `sync.Mutex` and `sync.RWMutex`?**

### Back

- `sync.Mutex` allows exclusive lock/unlock.
- `sync.RWMutex` allows concurrent reads but exclusive writes, ideal for read-heavy workloads.

<!-- Card End -->
 <!-- Card Start -->

### Front

**Primary use case of `sync.WaitGroup`?**

### Back

Waiting for a collection of goroutines to finish before proceeding.

<!-- Card End --> 
<!-- Card Start -->

### Front

**Explain `sync.Once`?**

what is it for.

### Back

Ensuring initialization code runs exactly once:

```go

var once sync.Once
once.Do(func() {
    fmt.Println("This runs once!")
})
```

see https://cristiancurteanu.com/understanding-go-sync-once/

  In Go, sync.Once provides an elegant and thread-safe way to implement this pattern.

```go
package main

import (
    "fmt"
    "sync"
)

type Singleton struct {
    data string
}

var instance *Singleton
var once sync.Once

func GetInstance() *Singleton {
    once.Do(func() {
        fmt.Println("Creating Singleton instance")
        instance = &Singleton{data: "I'm the only one!"}
    })
    return instance
}

func main() {
    for i := 0; i < 5; i++ {
        go func() {
            fmt.Printf("%p\n", GetInstance())
        }()
    }

    // Wait for goroutines to finish
    fmt.Scanln()
}
```
In this example, we're using sync.Once to ensure that our Singleton struct is instantiated only once, even when GetInstance() is called concurrently from multiple goroutines.

Let's break down the benefits of using sync.Once for this Singleton implementation:

**Thread-safety**: sync.Once guarantees that the initialization function is called exactly once, even in a concurrent environment. This eliminates race conditions during initialization.
**Lazy initialization**: The Singleton instance is created only when GetInstance() is first called, not when the program starts. This can be beneficial for resource management.
**Simplicity**: Compared to other thread-safe Singleton implementations (like using mutexes), sync.Once provides a cleaner and more idiomatic solution in Go.
**Performance**: After the first call, subsequent calls to once.Do() are essentially no-ops, making it very efficient.

 

<!-- Card End --> 
<!-- Card Start -->

### Front

**What scenario might require `sync.Cond`?**

### Back

Complex waiting/signaling patterns where goroutines must wait until specific conditions are met.

https://www.slingacademy.com/article/using-sync-cond-for-conditional-synchronization-in-go/


Here is a simplified example demonstrating a producer-consumer problem where multiple consumers wait for the producer to add an item to a shared resource:

```go

package main

import (
    "fmt"
    "sync"
)

var (
    mu    sync.Mutex
    cond  = sync.NewCond(&mu)
    queue []int
)

func produce(item int) {
    mu.Lock()
    queue = append(queue, item)
    fmt.Println("Produced:", item)
    cond.Signal()  // Notify one waiting consumer
    mu.Unlock()
}

func consume() {
    mu.Lock()
    for len(queue) == 0 {
        cond.Wait()
    }
    item := queue[0]
    queue = queue[1:]
    fmt.Println("Consumed:", item)
    mu.Unlock()
}

func main() {
    for i := 0; i < 5; i++ {
        go consume()
    }

    for i := 0; i < 5; i++ {
        produce(i)
    }
}
```
In this code, several consumer Goroutines are waiting for the produce function to insert items into a queue. Once an item is produced, a consumer is notified and processes the item.

<!-- Card End --> 
<!-- Card Start -->

### Front

**When are atomic operations preferable?**

### Back

For lock-free synchronization on primitive types like counters or flags, avoiding overhead from mutexes.

<!-- Card End --> 
<!-- Card Start -->

### Front

**Define a simple method on a custom type. (Example)**

### Back

```go
type Person struct {
    Name string
}

func (p Person) Greet() string {
    return "Hello " + p.Name
}

```

<!-- Card End --> 
<!-- Card Start -->

### Front

**What is struct embedding in Go used for?**

### Back

To reuse and extend functionality of existing structs through composition.

<!-- Card End --> 
<!-- Card Start -->

### Front

**What's a value receiver in method definition?**

### Back

A method receiver that gets a copy of the struct, modifications don't persist.

```go
func (p Person) Method() {}
```



<!-- Card End --> 
<!-- Card Start -->

### Front

**What's a pointer receiver in method definition?**

### Back

A method receiver that gets a pointer, allowing modifications to persist:

```go
func (p *Person) Method() {}
```
 

<!-- Card End --> 
<!-- Card Start -->

### Front

**When to use pointer receivers? (Select all that apply)**

- a  Small structs
- b  Methods modify receiver
- c  Large structs (to avoid copying overhead)

### Back

B and C 

b Methods modify receiver  
c Large structs (to avoid copying overhead)

<!-- Card End --> 
<!-- Card Start -->

### Front

**When to use value receivers? (Select all that apply)**

- A  Small structs
- B  Modifying struct state
- C  Immutability desired

### Back
A and C

Small structs  
Immutability desired

<!-- Card End --> 
<!-- Card Start -->

### Front

**What happens if you close an already closed channel?**

### Back

Causes a panic at runtime.

<!-- Card End --> 
<!-- Card Start -->

### Front

**Can you read from a closed channel?**

### Back

Yes, reads return zero-value immediately, with `ok` as false:

```go

val, ok := <-ch // ok will be false if ch is closed`

```

<!-- Card End --> 
<!-- Card Start -->

### Front

**What pattern helps distribute work across goroutines from one channel?**

### Back

Fan-out pattern.

<!-- Card End --> 
<!-- Card Start -->

### Front

**When should you avoid using context values excessively?**

### Back

Context values should not replace explicit function parameters and shouldn't store optional parameters or application state extensively.

<!-- Card End --> 
<!-- Card Start -->

### Front

**Example of atomic increment operation?**

### Back

```go
var count int64 atomic.AddInt64(&count, 1)
```
 

<!-- Card End --> 
<!-- Card Start -->

### Front

**How to properly use `sync.WaitGroup`? (Example)**

### Back

```go
var wg sync.WaitGroup 
wg.Add(1)  

go func() {     
     defer wg.Done()     
     // work 
}()  
wg.Wait()
```

<!-- Card End -->

# Batch 2

Here are 5 additional flashcards specifically addressing Go messaging syntax, including your particular interest in `<- msg` vs `msg <-`:

<!-- Card Start -->

### Front

**In Go channels, what is the difference between `<- msg` and `msg <-` syntax?**

### Back

- `<- msg` means **receiving** a value from channel `msg`.
  ```go
  val := <-msg
  ```
- `msg <- val` means **sending** a value (`val`) into channel `msg`.
  ```go
  msg <- val
  ```

<!-- Card End -->

<!-- Card Start -->

### Front

**What is the correct way to send a value to a channel in Go?**

- A: `value := <- channel`
- B: `channel <- value`
- C: `<-channel value`

### Back

b 
```go
channel <- value
```

<!-- Card End -->

<!-- Card Start -->

### Front

**Which syntax correctly reads from a Go channel named `ch`?**

- A `val := <-ch`
- B `ch <- val`
- C `<-ch val`

### Back

A
```go
val := <-ch
```

<!-- Card End -->

<!-- Card Start -->

### Front

**What does the following Go code snippet do?**
```go
select {
case ch <- v:
    // ...
default:
    // ...
}
```

### Back

Attempts a **non-blocking send** of value `v` into channel `ch`. If `ch` is full or not ready, it executes the `default` case.

#### Why Does a Regular Send Block?
Normally, when sending to an unbuffered channel:

```go

ch <- v  // BLOCKS until another goroutine receives
```

If there’s no receiver waiting, the program blocks and waits indefinitely.
If another goroutine is receiving from ch, then the value is sent immediately.
For a buffered channel:

```go
ch := make(chan int, 2)
ch <- 1 // Does NOT block (buffer has space)
ch <- 2 // Does NOT block (buffer has space)
ch <- 3 // BLOCKS (buffer is full until a value is received)
```

#### What Does select {} Do?
The select statement in Go allows handling multiple channel operations at once.

When using:

```go
select {
case ch <- v:
    // Value sent successfully
default:
    // Channel is full or no receiver, so do something else
}
```
If ch is ready to accept a value, the case ch <- v: branch executes.
If ch is blocked (full or no receiver), the default: case executes immediately, preventing blocking.

```go
func main() {
	ch := make(chan int, 2)
	select {
	case ch <- 1:
		// Value sent successfully
		fmt.Println("do 1")
	default:
		// Channel is full or no receiver, so do something else
		fmt.Println("booo")
	}

	select {
	case ch <- 2:
		// Value sent successfully
		fmt.Println("do 2")
	default:
		// Channel is full or no receiver, so do something else
		fmt.Println("booo")
	}

	select {
	case ch <- 2:
		// Value sent successfullyblocked  :(

		fmt.Println("booo")
	default:
		// Channel is full or no receiver, so do something else
		fmt.Println("do 3")
	}

}
```
prints:
```
do 1
do 2
do 3
```


https://go.dev/play/p/Rser0d2KowY

<!-- Card End -->

<!-- Card Start -->

### Front

**How do you check if a channel is closed after receiving from it?**

### Back

Use the two-value receive syntax:
```go
val, ok := <-ch
if !ok {
    fmt.Println("Channel closed!")
}
```
- `ok` is `false` if the channel has been closed.

<!-- Card End -->

<!-- Card Start -->

### Front

```go

func main() {
    ch := make(chan int)

    go func() {
        v := <-ch // Receives a value
        fmt.Println("Received:", v)
    }()

    select {
    case ch <- 42:
        fmt.Println("Value sent")
    default:
        fmt.Println("Channel blocked, skipping send")
    }
}
```
What will it say?

### Back

This will say that the channel is blocked and skip the send most of the time.
but it might also not.  
**It all depends on the scheduler.**

https://go.dev/play/p/AUgGX1T0K06


you can but a small sleep in there
```go
     time.Sleep(10 * time.Millisecond) // Allow goroutine to start
     select {....
```
and your good to go.  But you know...that kinda sucks

Try

```go

package main

import (
    "fmt"
    "sync"
)

func main() {
    var wg sync.WaitGroup
    ch := make(chan int)

    wg.Add(1)
    go func() {
         wg.Done()
        v := <-ch // Receives a value
        fmt.Println("Received:", v)
    }()

    wg.Wait() // Ensures the goroutine is ready

    select {
    case ch <- 42:
        fmt.Println("Value sent")
    default:
        fmt.Println("Channel blocked, skipping send")
    }
}
```

https://go.dev/play/p/n91qFVp_A0N


<!-- Card End -->

<!-- Card Start -->

### Front

```go
 package main

import (
	"fmt"
	"time"
)

func f(from string) {
	fmt.Println(from)
}

func main() {

	f("hello1")

	go f("hello2")

	go func(msg string) {
		fmt.Println(msg)
	}("hello3")

	time.Sleep(time.Second)
	fmt.Println("done")
}
```
 what is the difference between hello1, hello2 and hello3

### Back

- hello1 is a straight up synchronous function call
- hello2 is a go proc
- hello3 is an anonymous function ( still a go proc)

you need to do the delay at the end to see the results.
<!-- Card End -->