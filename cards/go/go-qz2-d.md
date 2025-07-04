# Golang Interview Preparation Flashcards - Set D

Here is another set of multiple choice flashcards for Golang interview preparation, focusing on advanced concepts, best practices, and practical scenarios:

<!-- Card Start -->

### Front

What is the purpose of the `iota` keyword in Go?

- A. To define constants with sequential values
- B. To create dynamic variables
- C. To implement loops
- D. To manage memory allocation

### Back

**A. To define constants with sequential values**

The `iota` keyword is used to simplify the creation of enumerated constants in Go. It starts at 0 and increments by 1 for each constant in the same block.

```go
const (
    First = iota // 0
    Second        // 1
    Third         // 2
)
fmt.Println(First, Second, Third) // Output: 0 1 2
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of the `fallthrough` statement in a Go `switch`?

- A. To exit the `switch` immediately
- B. To execute the next case regardless of its condition
- C. To repeat the current case
- D. To handle default cases

### Back

**B. To execute the next case regardless of its condition**

The `fallthrough` statement in Go allows control to pass to the next case in a `switch`, even if the condition for the next case is not met. It must be the last statement in a case block.

```go
switch n := 2; n {
case 1:
    fmt.Println("One")
case 2:
    fmt.Println("Two")
    fallthrough
case 3:
    fmt.Println("Three")
}
// Output: Two\nThree
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens if a `break` statement is used in a Go `switch`?

- A. It skips the current case and evaluates the next one
- B. It exits the `switch` entirely
- C. It causes a runtime error
- D. It has no effect in Go `switch`

### Back

**B. It exits the `switch` entirely**

The `break` statement in Go is used to exit a `switch` or loop prematurely. However, in Go `switch` statements, cases automatically break unless `fallthrough` is explicitly used.

```go
switch n := 2; n {
case 1:
    fmt.Println("One")
case 2:
    fmt.Println("Two")
    break
case 3:
    fmt.Println("Three")
}
// Output: Two
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary difference between buffered and unbuffered channels in Go?

- A. Buffered channels are faster than unbuffered channels
- B. Unbuffered channels block until both sender and receiver are ready
- C. Buffered channels can only hold primitive types
- D. Unbuffered channels can hold unlimited values

### Back

**B. Unbuffered channels block until both sender and receiver are ready**

Buffered channels allow asynchronous communication up to their capacity, while unbuffered channels require both sender and receiver to be ready at the same time.

```go
unbuffered := make(chan int)     // Synchronous
buffered := make(chan int, 3)    // Can hold 3 values before blocking
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens when a buffered channel in Go is full?

- A. The program panics
- B. The sender blocks until space is available
- C. The receiver blocks until the channel is empty
- D. The channel discards the oldest value

### Back

**B. The sender blocks until space is available**

When a buffered channel is full, the sender blocks until a receiver reads from the channel, freeing up space.

```go
ch := make(chan int, 2)
ch <- 1
ch <- 2
// ch <- 3 // This would block until a value is read
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is a key advantage of using buffered channels in Go?

- A. They eliminate the need for synchronization
- B. They allow asynchronous communication between goroutines
- C. They automatically resize when full
- D. They are faster than unbuffered channels

### Back

**B. They allow asynchronous communication between goroutines**

Buffered channels enable goroutines to send and receive messages without waiting for the other party, as long as the buffer has capacity.

```go
ch := make(chan int, 2)
ch <- 1
ch <- 2
fmt.Println(<-ch) // Reads 1
fmt.Println(<-ch) // Reads 2
```

<!-- Card End -->

<!-- Card Start -->

### Front

When implementing an interface in Go, what is the main difference between using a value receiver `(kv MyKV)` and a pointer receiver `(kv *MyKV)`?

- A. Value receivers can't access struct fields
- B. Pointer receivers allow the method to modify the receiver
- C. Value receivers run faster
- D. Pointer receivers are required for interfaces

### Back

**B. Pointer receivers allow the method to modify the receiver**

Value receivers operate on a copy of the value, while pointer receivers allow methods to modify the original value. If your method needs to modify the receiver's state, use a pointer receiver.

```go
type Counter struct {
    count int
}

// Modifies the original Counter
func (c *Counter) Increment() {
    c.count++
}

// Works on a copy - original Counter is unchanged
func (c Counter) IncrementCopy() {
    c.count++
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

Which statement about method sets and interfaces in Go is correct?

- A. Methods with pointer receivers can only be called on pointers
- B. Value types cannot implement interfaces with pointer methods
- C. Methods with value receivers can be called on both values and pointers
- D. Pointer methods always require interface pointers

### Back

**C. Methods with value receivers can be called on both values and pointers**

Method sets in Go follow these rules:
- Methods with value receivers can be called on both values and pointers (because Go can dereference the pointer)
- Methods with pointer receivers can only be called on pointers or addressable values (because Go needs to get the address)

```go
package main

import (
	"fmt"
)

type Stringer interface {
	String() string
}

type Person struct {
	Name string
}

// Value receiver - this method is defined on the VALUE type Person
// This means both Person and *Person can call this method
func (p Person) String() string {
	return p.Name
}

func main() {
	// ========== PART 1: Working with VALUE types ==========
	
	// p1 is a VALUE of type Person (not a pointer)
	p1 := Person{"Alice"}
	fmt.Println("p1 type: Person (value)")
	fmt.Println("p1.String():", p1.String()) // Direct method call on value
	
	// s1 is an interface variable that holds a Person VALUE
	// Since String() has a value receiver, Person implements Stringer
	var s1 Stringer = p1  // p1 (the value) is copied into the interface
	fmt.Println("s1 holds a Person value")
	fmt.Println("s1.String():", s1.String()) // Calls String() on the copied value
	
	fmt.Println() // Blank line for readability
	
	// ========== PART 2: Working with POINTER types ==========
	
	// p2 is a POINTER to a Person (*Person)
	p2 := &Person{"Bob"}  // &Person{"Bob"} creates a pointer to a Person
	fmt.Println("p2 type: *Person (pointer)")
	fmt.Println("p2.String():", p2.String()) // Go automatically dereferences: (*p2).String()
	
	// s2 is an interface variable that holds a *Person POINTER
	// This works because Go has a special rule: if a method is defined with a value receiver,
	// both the value type AND the pointer type implement the interface
	var s2 Stringer = p2  // p2 (the pointer) is stored in the interface
	fmt.Println("s2 holds a *Person pointer")
	fmt.Println("s2.String():", s2.String()) // Go calls String() on the value that p2 points to
	
	fmt.Println() // Blank line for readability
	
	// ========== PART 3: Demonstrating the key difference ==========
	
	fmt.Println("=== Key Difference Demonstration ===")
	
	// Let's modify the original values to see what happens
	p1.Name = "Alice Modified"
	p2.Name = "Bob Modified"
	
	fmt.Println("After modification:")
	fmt.Println("p1.String():", p1.String())           // "Alice Modified"
	fmt.Println("s1.String():", s1.String())           // Still "Alice" - why?
	fmt.Println("p2.String():", p2.String())           // "Bob Modified"  
	fmt.Println("s2.String():", s2.String())           // "Bob Modified" - why?
	
	fmt.Println()
	fmt.Println("=== Explanation ===")
	fmt.Println("s1 contains a COPY of the original p1 value")
	fmt.Println("s2 contains the same POINTER as p2, pointing to the same memory location")
	
	// ========== PART 4: Type assertions to prove the point ==========
	
	fmt.Println()
	fmt.Println("=== Type Assertions ===")
	
	// Extract the actual values from the interfaces
	if val, ok := s1.(Person); ok {
		fmt.Printf("s1 contains Person value: %+v\n", val)
	}
	
	if ptr, ok := s2.(*Person); ok {
		fmt.Printf("s2 contains *Person pointer: %+v\n", ptr)
		fmt.Printf("s2 points to Person value: %+v\n", *ptr)
	}
}
```

<!-- Card End -->

<!-- Card Start -->

### Front
How do method sets in Go determine whether a type satisfies an interface?

- A. Only pointer methods can satisfy interfaces
- B. Value receiver methods can be called on both values and pointers
- C. Pointer receiver methods can only be called on pointers
- D. Both B and C are correct


### Back
D. Both B and C are correct

Method sets in Go define which methods are available for a type or pointer to a type. The rules are:

1. Value receiver methods:

- Can be called on both values and pointers.
- The compiler automatically dereferences the pointer if needed.


2. Pointer receiver methods:

- Can only be called on pointers or addressable values.
- This is because the method may modify the receiver, requiring its address.

Here’s a more detailed example:

```go
package main

import "fmt"

// Define an interface
type Stringer interface {
    String() string
}

// Define a struct
type Person struct {
    Name string
}

// Value receiver method
func (p Person) String() string {
    return "Value receiver: " + p.Name
}

// Pointer receiver method
func (p *Person) UpdateName(newName string) {
    p.Name = newName
}

func main() {
    // Example 1: Value receiver method
    p1 := Person{Name: "Alice"}
    var s1 Stringer = p1 // Works because value receiver methods are in the method set of both values and pointers
    fmt.Println(s1.String()) // Output: Value receiver: Alice

    // Example 2: Pointer receiver method
    p2 := &Person{Name: "Bob"}
    var s2 Stringer = p2 // Works because pointer receiver methods are in the method set of pointers
    fmt.Println(s2.String()) // Output: Value receiver: Bob

    // Example 3: Calling pointer receiver method on a value
    // p1.UpdateName("Charlie") // Compiler error: cannot call pointer receiver method on a value
    p2.UpdateName("Dave")    // Works because p2 is a pointer
    fmt.Println(p2.Name)     // Output: Dave
}
```

Key Takeaways:
Value receiver methods are more flexible because they can be called on both values and pointers.
Pointer receiver methods are necessary when the method modifies the receiver or when the type is large and copying is expensive.
Interfaces can be satisfied by either values or pointers, depending on the method set.

<!-- Card End -->

<!-- Card Start -->

### Front

In Go, when is it preferable to use value receivers for methods?

- A. When the struct is large
- B. When method needs to modify the receiver
- C. When the type is small and naturally copied (like primitive types)
- D. Only for interfaces

### Back

**C. When the type is small and naturally copied (like primitive types)**

Use value receivers when:
- The type is small and naturally copied (like int, float, small structs)
- The type is immutable
- You don't need to modify the receiver
- Methods should have value semantics (each call operates on an independent copy)

```go
type Point struct {
    X, Y float64
}

// Good use of value receiver - small struct, no need to modify
func (p Point) Distance(q Point) float64 {
    return math.Sqrt(math.Pow(p.X-q.X, 2) + math.Pow(p.Y-q.Y, 2))
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

When should you prefer pointer receivers for methods in Go?

- A. Always, as they're more efficient
- B. Only for public methods
- C. Only when implementing interfaces
- D. When the struct is large or you need to modify the receiver

### Back

**D. When the struct is large or you need to modify the receiver**

Pointer receivers are preferable when:
- You need to modify the receiver
- The struct is large (to avoid copying large amounts of data)
- The type contains fields that cannot be copied (like mutexes)
- You want consistent behavior across all methods of the type

```go
type Database struct {
    data   map[string]string
    logger *Logger
    mutex  sync.Mutex  // Should not be copied
}

// Correct - uses pointer receiver
func (db *Database) Insert(key, value string) {
    db.mutex.Lock()
    defer db.mutex.Unlock()
    db.data[key] = value
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens if a Go type has a mix of pointer and value receiver methods while implementing an interface?

- A. It causes a compilation error
- B. The type can only implement the interface via pointers
- C. The value receiver methods are automatically promoted to pointer receivers
- D. The compiler chooses the most efficient implementation

### Back

**B. The type can only implement the interface via pointers**

If a type has any methods with pointer receivers that are needed to satisfy an interface, then **only pointers of that type implement the interface.**

```go
type Worker interface {
    DoWork()
    Report() string
}

type Employee struct {
    name string
    logs []string
}

// Pointer receiver - modifies state
func (e *Employee) DoWork() {
    e.logs = append(e.logs, "Work done")
}

// Value receiver - just reads
func (e Employee) Report() string {
    return strings.Join(e.logs, ", ")
}

// Valid: pointer implements both methods
var w1 Worker = &Employee{"Alice", []string{}}

// Invalid: value doesn't implement DoWork
// var w2 Worker = Employee{"Bob", []string{}} // Won't compile
```

So...

<!-- Card End -->

<!-- Card Start -->

### Front

What effect does the choice between value and pointer receivers have on method call performance in Go?

- A. Value receivers are always faster
- B. Pointer receivers are always faster
- C. Large structs are more efficient with pointer receivers
- D. There is no performance difference

### Back

**C. Large structs are more efficient with pointer receivers**

Performance considerations for method receivers:
- For small types (primitives, small structs): value receivers often perform better (avoid indirection)
- For large structs: pointer receivers are more efficient (avoid copying)
- Benchmarking is recommended for performance-critical code

```go
// Small struct - value receiver might be faster
type Point struct {
    X, Y float64
}

// Large struct - pointer receiver is more efficient
type Image struct {
    Width, Height int
    Pixels        [][]Color // Large data
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

In Go, what happens when you call a method requiring a pointer receiver on a non-addressable value?

- A. Go automatically makes a copy that can be addressed
- B. The code compiles but panics at runtime
- C. The compiler rejects the code
- D. The method silently operates on a temporary copy

### Back

**C. The compiler rejects the code**

You cannot call a pointer-receiver method on a non-addressable value because Go needs to take the value's address, which isn't possible for non-addressable values (like literals or temporary values).

```go
type Counter struct {
    count int
}

func (c *Counter) Increment() {
    c.count++
}

// Valid - variable is addressable
counter := Counter{}
counter.Increment()

// Invalid - literal is not addressable
// Counter{}.Increment() // Compiler error
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the relationship between method receivers and the ability to satisfy interfaces in Go?

- A. Only pointer methods can satisfy interfaces
- B. A type with value receiver methods implements an interface for both values and pointers
- C. A type with pointer receiver methods implements an interface only for pointers
- D. The choice of receiver has no impact on interface implementation

### Back

**B and C are both correct, but the most complete answer is: A type with value receiver methods implements an interface for both values and pointers, but a type with pointer receiver methods implements an interface only for pointers**

Interface satisfaction rules:
- If all interface methods have value receivers in the implementation, both the type and pointers to the type satisfy the interface
- If any method has a pointer receiver, only pointers to the type satisfy the interface

```go
type Printer interface {
    Print()
}

type Document struct {
    content string
}

func (d Document) Print() { // Value receiver
    fmt.Println(d.content)
}

// Both work:
var p1 Printer = Document{"Hello"}
var p2 Printer = &Document{"World"}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the best practice for receiver types when implementing a Go interface like this:

```go
type KV interface {
    Set(key, val string)
    Get(key string) string
}
```

- A. Always use pointer receivers
- B. Always use value receivers
- C. Use pointer receivers for methods that modify state (Set) and value receivers for others (Get)
- D. Choose based on the size of the implementing struct

### Back

**A. Always use pointer receivers**

When implementing interfaces, it's best practice to be consistent with receiver types across all methods. Since the `Set` method typically modifies state, pointer receivers make the most sense for the entire implementation.

```go
type MyKV struct {
    data map[string]string
}

func (kv *MyKV) Set(key, val string) {
    if kv.data == nil {
        kv.data = make(map[string]string)
    }
    kv.data[key] = val
}

func (kv *MyKV) Get(key string) string {
    return kv.data[key]
}
```

Mixing receiver types can lead to confusion and unexpected behavior when using the interface.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes pointer receivers in Go different from reference parameters in languages like C++?

- A. Go has no reference types, only values and pointers
- B. Pointer receivers are automatically dereferenced
- C. Pointer receivers can only point to structs
- D. Pointer receivers use garbage collection

### Back

**A. Go has no reference types, only values and pointers**

Go's design philosophy is simpler than many other languages:
- Everything is passed by value (always a copy)
- There are no reference types as in C++ or Java
- Pointers are explicitly denoted with * and &
- Slices, maps, and channels contain internal pointers but the container itself is still passed by value

This makes reasoning about code more straightforward—you either have a value or a pointer to a value, with no hidden reference semantics.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary purpose of `sync.Mutex` in Go?

- A. To coordinate execution order between goroutines
- B. To provide exclusive access to shared resources
- C. To allow multiple goroutines to execute simultaneously
- D. To automatically synchronize map access

### Back

**B. To provide exclusive access to shared resources**

`sync.Mutex` provides mutual exclusion, ensuring that only one goroutine can access a shared resource at a time, preventing race conditions.

```go
type Counter struct {
    mu    sync.Mutex
    count int
}

func (c *Counter) Increment() {
    c.mu.Lock()
    defer c.mu.Unlock()
    c.count++
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens if you try to unlock an already unlocked `sync.Mutex` in Go?

- A. Nothing, it's a safe operation
- B. The program will panic
- C. The next Lock will fail
- D. It blocks until another goroutine locks it

### Back

**B. The program will panic**

Unlocking an unlocked mutex causes a runtime panic in Go. This is a deliberate design to catch programming errors.

```go
var mu sync.Mutex
mu.Lock()
mu.Unlock()
mu.Unlock() // This will panic: "sync: unlock of unlocked mutex"
```

<!-- Card End -->

<!-- Card Start -->

### Front

What's the difference between `sync.Mutex` and `sync.RWMutex` in Go?

- A. RWMutex allows multiple writers but only one reader
- B. RWMutex allows multiple readers but only one writer
- C. RWMutex automatically handles timeouts, Mutex doesn't
- D. RWMutex works across network boundaries, Mutex is process-local

### Back

**B. RWMutex allows multiple readers but only one writer**

`sync.RWMutex` provides more granular locking than a standard mutex:
- Multiple goroutines can acquire a read lock simultaneously (RLock)
- Only one goroutine can hold a write lock (Lock) at a time
- When a write lock is held, no read locks can be acquired

```go
type SafeMap struct {
    mu   sync.RWMutex
    data map[string]string
}

// Multiple goroutines can read simultaneously
func (m *SafeMap) Get(key string) string {
    m.mu.RLock()
    defer m.mu.RUnlock()
    return m.data[key]
}

// Only one goroutine can write at a time
func (m *SafeMap) Set(key, value string) {
    m.mu.Lock()
    defer m.mu.Unlock()
    m.data[key] = value
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is a common mistake when using `sync.Mutex` with struct methods in Go?

- A. Forgetting to initialize the mutex
- B. Using value receivers instead of pointer receivers
- C. Using Lock() and Unlock() in different methods
- D. Locking for too long

### Back

**B. Using value receivers instead of pointer receivers**

Using a value receiver with methods that lock/unlock a mutex is incorrect because each method call operates on a copy of the mutex, making synchronization ineffective.

```go
// INCORRECT - mutex is copied with each method call
type Counter struct {
    mu    sync.Mutex
    count int
}

func (c Counter) Increment() { // Value receiver creates a copy
    c.mu.Lock()
    defer c.mu.Unlock()
    c.count++ // Modifies the copy, not original
}

// CORRECT - uses pointer receiver
func (c *Counter) Increment() {
    c.mu.Lock()
    defer c.mu.Unlock()
    c.count++
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

How can you protect access to a map for concurrent use in Go?

- A. Maps are automatically thread-safe in Go
- B. Use a mutex to synchronize all access to the map
- C. Use the `concurrent-map` package
- D. Enable concurrent access with a special flag

### Back

**B. Use a mutex to synchronize all access to the map**

Maps in Go are not thread-safe by default. Concurrent access to a map without synchronization can lead to race conditions and crashes.

```go
type SafeMap struct {
    mu sync.Mutex
    m  map[string]string
}

func (s *SafeMap) Get(key string) string {
    s.mu.Lock()
    defer s.mu.Unlock()
    return s.m[key]
}

func (s *SafeMap) Set(key, value string) {
    s.mu.Lock()
    defer s.mu.Unlock()
    s.m[key] = value
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary purpose of atomic operations in Go?

- A. To replace mutexes entirely
- B. To provide lightweight synchronization for simple shared state
- C. To enable concurrent access to maps
- D. To simplify goroutine management

### Back

**B. To provide lightweight synchronization for simple shared state**

Atomic operations in Go, provided by the `sync/atomic` package, are used for low-level synchronization without the overhead of mutexes. They are ideal for counters, flags, and other simple shared state.

```go
import "sync/atomic"

var counter int32

atomic.AddInt32(&counter, 1) // Increment counter atomically
atomic.LoadInt32(&counter)  // Read counter atomically
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between `sync.Mutex` and `sync/atomic` in Go?

- A. Mutexes are faster than atomic operations
- B. Atomic operations are limited to simple types like integers
- C. Mutexes can only be used with structs
- D. Atomic operations require more memory

### Back

**B. Atomic operations are limited to simple types like integers**

While `sync.Mutex` can guard complex shared resources, `sync/atomic` is limited to simple types like integers and pointers. Mutexes are more versatile but come with higher overhead.

```go
// Mutex example
var mu sync.Mutex
var data map[string]string

mu.Lock()
data["key"] = "value"
mu.Unlock()

// Atomic example
var counter int32
atomic.AddInt32(&counter, 1)
```

<!-- Card End -->

<!-- Card Start -->

### Front

When should you use `sync.RWMutex` instead of `sync.Mutex` in Go?

- A. When you need to synchronize access to a map
- B. When reads are frequent and writes are rare
- C. When you need to prevent race conditions
- D. When you need to synchronize goroutines

### Back

**B. When reads are frequent and writes are rare**

`sync.RWMutex` allows multiple readers to access a resource simultaneously but restricts writes to a single goroutine. This is ideal for scenarios where reads dominate.

```go
type SafeMap struct {
    mu   sync.RWMutex
    data map[string]string
}

func (m *SafeMap) Get(key string) string {
    m.mu.RLock()
    defer m.mu.RUnlock()
    return m.data[key]
}

func (m *SafeMap) Set(key, value string) {
    m.mu.Lock()
    defer m.mu.Unlock()
    m.data[key] = value
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens if you use `sync.Mutex` incorrectly in Go?

- A. The program will panic
- B. The program will deadlock
- C. The program will crash
- D. The program will ignore the error

### Back

**B. The program will deadlock**

Incorrect use of `sync.Mutex`, such as forgetting to unlock it, can lead to deadlocks where goroutines are stuck waiting indefinitely.

```go
var mu sync.Mutex

mu.Lock()
// Forgetting to unlock
// mu.Unlock() // Uncomment to fix deadlock
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of `sync.Cond` in Go?

- A. To provide mutual exclusion
- B. To signal goroutines waiting for a condition
- C. To manage atomic operations
- D. To synchronize access to maps

### Back

**B. To signal goroutines waiting for a condition**

`sync.Cond` is used for signaling between goroutines, allowing them to wait for a specific condition to be met.

```go
var mu sync.Mutex
var cond = sync.NewCond(&mu)

func worker() {
    mu.Lock()
    cond.Wait() // Wait for signal
    fmt.Println("Worker resumed")
    mu.Unlock()
}

func main() {
    go worker()
    mu.Lock()
    cond.Signal() // Signal worker
    mu.Unlock()
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the role of `context.Context` in Go concurrency?

- A. To manage goroutine lifecycles
- B. To synchronize access to shared resources
- C. To replace mutexes
- D. To simplify atomic operations

### Back

**A. To manage goroutine lifecycles**

`context.Context` is used to control goroutine lifecycles, enabling cancellation, timeouts, and passing metadata.

```go
import "context"

func worker(ctx context.Context) {
    for {
        select {
        case <-ctx.Done():
            fmt.Println("Worker stopped")
            return
        default:
            fmt.Println("Worker running")
        }
    }
}

func main() {
    ctx, cancel := context.WithCancel(context.Background())
    go worker(ctx)
    cancel() // Stop worker
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens if you call `context.WithCancel` but forget to call the cancel function?

- A. The program will panic
- B. The program will leak resources
- C. The program will deadlock
- D. The program will ignore the error

### Back

**B. The program will leak resources**

Forgetting to call the cancel function of `context.WithCancel` can lead to resource leaks as the context remains active indefinitely.

```go
ctx, cancel := context.WithCancel(context.Background())
// cancel() // Uncomment to prevent resource leak
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between buffered and unbuffered channels in Go?

- A. Buffered channels block until both sender and receiver are ready
- B. Buffered channels allow asynchronous communication
- C. Unbuffered channels can hold multiple values
- D. Buffered channels are faster

### Back

**B. Buffered channels allow asynchronous communication**

Buffered channels enable goroutines to send and receive messages without waiting for the other party, as long as the buffer has capacity.

```go
ch := make(chan int, 2)
ch <- 1
ch <- 2
fmt.Println(<-ch) // Reads 1
fmt.Println(<-ch) // Reads 2
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens if you try to send to a closed channel in Go?

- A. The program will panic
- B. The program will deadlock
- C. The program will crash
- D. The program will ignore the error

### Back

**A. The program will panic**

Sending to a closed channel causes a runtime panic in Go.

```go
ch := make(chan int)
close(ch)
// ch <- 1 // Uncomment to see panic
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of `select` in Go?

- A. To synchronize goroutines
- B. To wait on multiple channel operations
- C. To manage atomic operations
- D. To replace mutexes

### Back

**B. To wait on multiple channel operations**

The `select` statement allows a goroutine to wait on multiple channel operations, proceeding with the first one that becomes available.

```go
ch1 := make(chan int)
ch2 := make(chan int)

select {
case val := <-ch1:
    fmt.Println("Received from ch1:", val)
case val := <-ch2:
    fmt.Println("Received from ch2:", val)
default:
    fmt.Println("No channels ready")
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens when you pass a value argument to a function in Go?

- A. The function modifies the original value
- B. The function panics if the value is immutable
- C. The function creates a pointer to the value
- D. The function works on a copy of the value

### Back

**B. The function works on a copy of the value**

In Go, passing a value argument to a function creates a copy of the value. Changes made inside the function do not affect the original value.

```go
func modifyValue(x int) {
    x = 42
}

func main() {
    num := 10
    modifyValue(num)
    fmt.Println(num) // Output: 10
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens when you pass a pointer argument to a function in Go?

- A. The function works on a copy of the pointer
- B. The function creates a new pointer
- C. The function modifies the original value
- D. The function panics if the pointer is nil

### Back

**C. The function modifies the original value**

Passing a pointer argument allows the function to modify the original value by dereferencing the pointer.

```go
func modifyPointer(x *int) {
    *x = 42
}

func main() {
    num := 10
    modifyPointer(&num)
    fmt.Println(num) // Output: 42
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between returning a value and returning a pointer in Go?

- A. Returning a value creates a copy
- B. Returning a pointer creates a copy
- C. Returning a value modifies the original value
- D. Returning a pointer is less efficient

### Back

**A. Returning a value creates a copy**

Returning a value creates a copy of the original value, while returning a pointer allows the caller to access and modify the original value.

```go
func returnValue() int {
    return 42
}

func returnPointer() *int {
    val := 42
    return &val
}

func main() {
    v := returnValue()
    fmt.Println(v) // Output: 42

    p := returnPointer()
    fmt.Println(*p) // Output: 42
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

When should you prefer returning a pointer over a value in Go?

- A. When the value is small and immutable
- B. When the value is large or needs to be modified
- C. When the value is a primitive type
- D. When the value is a constant

### Back

**B. When the value is large or needs to be modified**

Returning a pointer is preferable when the value is large (to avoid copying) or when the caller needs to modify the value.

```go
type LargeStruct struct {
    data [1024]int
}

func returnPointer() *LargeStruct {
    return &LargeStruct{}
}

func main() {
    ls := returnPointer()
    ls.data[0] = 42
    fmt.Println(ls.data[0]) // Output: 42
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens if you return a pointer to a local variable in Go?

- A. The program panics
- B. The pointer becomes invalid
- C. The pointer remains valid
- D. The program crashes

### Back

**C. The pointer remains valid** but is not a preferred practice

Returning a pointer to a local variable is technically safe in Go because the runtime ensures the memory remains valid. However, this is not a preferred practice as it can lead to confusion and potential misuse. Instead, consider using heap-allocated variables for clarity and safety.

```go
func returnPointer() *int {
    val := 42
    return &val // Not preferred
}

func returnHeapPointer() *int {
    val := new(int)
    *val = 42
    return val // Preferred
}

func main() {
    p := returnHeapPointer()
    fmt.Println(*p) // Output: 42
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is a heap-allocated variable in Go?

- A. A variable stored in the stack
- B. A variable whose memory is managed dynamically
- C. A variable that cannot be modified
- D. A variable that is automatically garbage collected

### Back

**B. A variable whose memory is managed dynamically**

Heap-allocated variables in Go are created using the `new` or `make` functions. Their memory is managed dynamically and remains valid as long as references to them exist.

```go
func createHeapVariable() *int {
    val := new(int)
    *val = 42
    return val
}

func main() {
    p := createHeapVariable()
    fmt.Println(*p) // Output: 42
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

When should you use heap-allocated variables in Go?

- A. When the variable is small and temporary
- B. When the variable needs to persist beyond the function scope
- C. When the variable is immutable
- D. When the variable is a constant

### Back

**B. When the variable needs to persist beyond the function scope**

Heap-allocated variables are useful when the variable needs to persist beyond the scope of the function that created it.

```go
func createPersistentVariable() *int {
    val := new(int)
    *val = 42
    return val
}

func main() {
    p := createPersistentVariable()
    fmt.Println(*p) // Output: 42
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between stack and heap allocation in Go?

- A. Stack allocation is faster but limited in scope
- B. Heap allocation is faster but limited in scope
- C. Stack allocation is slower but persists longer
- D. Heap allocation is slower but persists longer

### Back

**A. Stack allocation is faster but limited in scope**

Stack allocation is faster because memory is automatically reclaimed when the function exits. However, if a pointer to a stack-allocated variable is passed or returned, Go's escape analysis will promote it to the heap, ensuring it persists beyond the function scope. Heap allocation is slower but allows variables to persist beyond the function scope.

```go
func stackExample() int {
    val := 42
    return val // Stack allocated
}

func heapExample() *int {
    val := new(int)
    *val = 42
    return val // Heap allocated
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

How does Go manage memory for heap-allocated variables?

- A. Manual memory management
- B. Automatic garbage collection
- C. Reference counting
- D. Memory pooling

### Back

**B. Automatic garbage collection**

Go uses automatic garbage collection to manage memory for heap-allocated variables. The runtime ensures that memory is freed when it is no longer referenced.

```go
func createHeapVariable() *int {
    val := new(int)
    *val = 42
    return val
}

func main() {
    p := createHeapVariable()
    fmt.Println(*p) // Output: 42
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What are the advantages of heap allocation in Go?

- A. Faster memory access
- B. Reduced memory usage
- C. Easier debugging
- D. Persistent memory beyond function scope

### Back

**B. Persistent memory beyond function scope**

Heap allocation allows variables to persist beyond the scope of the function that created them, making it useful for long-lived objects.

```go
func createHeapVariable() *int {
    val := new(int)
    *val = 42
    return val
}

func main() {
    p := createHeapVariable()
    fmt.Println(*p) // Output: 42
}
```

<!-- Card End -->
