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
- B. Methods with value receivers can be called on both values and pointers
- C. Value types cannot implement interfaces with pointer methods
- D. Pointer methods always require interface pointers

### Back

**B. Methods with value receivers can be called on both values and pointers**

Method sets in Go follow these rules:
- Methods with value receivers can be called on both values and pointers (because Go can dereference the pointer)
- Methods with pointer receivers can only be called on pointers or addressable values (because Go needs to get the address)

```go
type Stringer interface {
    String() string
}

type Person struct {
    Name string
}

// Value receiver
func (p Person) String() string {
    return p.Name
}

// Both work:
var s1 Stringer = Person{"Alice"}
var s2 Stringer = &Person{"Bob"}
```

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
- B. When the struct is large or you need to modify the receiver
- C. Only when implementing interfaces
- D. Only for public methods

### Back

**B. When the struct is large or you need to modify the receiver**

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

If a type has any methods with pointer receivers that are needed to satisfy an interface, then only pointers of that type implement the interface.

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
