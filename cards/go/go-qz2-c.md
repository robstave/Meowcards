# Golang Interview Preparation Flashcards - Set C

Here is an additional set of 30 multiple choice flashcards for Golang interview preparation, focusing on advanced concepts, best practices, and practical scenarios:

<!-- Card Start -->

### Front

What is the correct way to check if a key exists in a map in Go?

- A. if map[key] != nil
- B. if _, exists := map[key]; exists
- C. if value, ok := map[key]; ok
- D. if map.hasKey(key)

### Back

**C. if value, ok := map[key]; ok**

The comma ok idiom is the standard way to check if a key exists in a map. The second return value is a boolean indicating whether the key was found.

```go
m := map[string]int{"a": 1, "b": 2}
if value, ok := m["a"]; ok {
    fmt.Println("Key exists with value:", value)
} else {
    fmt.Println("Key does not exist")
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens when you close a channel in Go?

- A. All pending operations panic immediately
- B. Future sends panic, but receives return zero values and false
- C. The channel becomes nil
- D. All goroutines waiting on the channel are terminated

### Back

**B. Future sends panic, but receives return zero values and false**

Closing a channel:
- Makes future sends panic
- Allows receives to continue returning the zero value and false for the "ok" boolean
- Immediately unblocks all goroutines waiting to receive from the channel

```go
ch := make(chan int, 2)
ch <- 1
close(ch)
// ch <- 2  // This would panic
val, ok := <-ch // val=1, ok=true
val, ok = <-ch  // val=0, ok=false
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary difference between `new()` and `make()` in Go?

- A. `new()` is for structs, `make()` is for primitives
- B. `new()` returns a pointer to zero value, `make()` initializes built-in types
- C. `new()` allocates on heap, `make()` allocates on stack
- D. They are functionally identical

### Back

**B. `new()` returns a pointer to zero value, `make()` initializes built-in types**

- `new(T)` allocates memory for type T, sets it to zero value, and returns a pointer (*T)
- `make()` is only for slices, maps, and channels, creating and initializing these types and returning the type itself (not a pointer)

```go
p := new(int)        // *int, points to 0
s := make([]int, 5)  // []int, initialized slice with length 5
```

<!-- Card End -->

<!-- Card Start -->

### Front

Which Go feature allows you to define methods on any named type?

- A. Type embedding
- B. Interface implementation
- C. Method sets
- D. Type aliasing

### Back

**C. Method sets**

Go allows you to define methods on any named type (it's not just for structs) by using method sets. This includes custom types based on built-in types.

```go
type MyInt int

func (m MyInt) Double() MyInt {
    return m * 2
}

var x MyInt = 5
fmt.Println(x.Double()) // 10
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the correct way to implement a string method for custom error types in Go?

- A. Implement the `String() string` method
- B. Implement the `Error() string` method
- C. Implement the `Message() string` method
- D. Override the `toString()` method

### Back

**B. Implement the `Error() string` method**

Custom error types must implement the `error` interface by providing an `Error() string` method. The `String()` method is for the `fmt.Stringer` interface.

```go
type CustomError struct {
    Code    int
    Message string
}

func (e CustomError) Error() string {
    return fmt.Sprintf("Error %d: %s", e.Code, e.Message)
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

In Go, what does the expression `s[1:3]` return when `s` is a slice?

- A. Elements at indices 1 and 3
- B. Elements at indices 1, 2, and 3
- C. Elements at indices 1 and 2
- D. Elements starting from index 1 with length 3

### Back

**C. Elements at indices 1 and 2**

Slice expressions use half-open intervals: `s[start:end]` includes elements from index `start` up to but not including index `end`.

```go
s := []int{0, 1, 2, 3, 4}
sub := s[1:3] // []int{1, 2}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of the `sync.Once` type in Go?

- A. To ensure a function is called exactly once across all goroutines
- B. To create a single-use channel
- C. To implement a singleton pattern
- D. To synchronize exactly one goroutine

### Back

**A. To ensure a function is called exactly once across all goroutines**

`sync.Once` provides a mechanism to ensure that a function is executed exactly once, regardless of how many goroutines call it. It's commonly used for one-time initialization.

```go
var once sync.Once
var instance *Database

func GetDatabase() *Database {
    once.Do(func() {
        instance = &Database{}
        instance.Connect()
    })
    return instance
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

Which statement about Go's type system is correct?

- A. Go supports inheritance through struct embedding
- B. Go has dynamic typing with optional static typing
- C. Go uses composition and interfaces instead of inheritance
- D. Go allows multiple inheritance through interfaces

### Back

**C. Go uses composition and interfaces instead of inheritance**

Go doesn't have traditional inheritance. Instead, it uses composition (struct embedding) and interfaces to achieve code reuse and polymorphism, following the principle "composition over inheritance."

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between buffered and unbuffered channels in Go?

- A. Buffered channels are faster than unbuffered channels
- B. Unbuffered channels block until both sender and receiver are ready
- C. Buffered channels can only hold primitive types
- D. Unbuffered channels can hold unlimited values

### Back

**B. Unbuffered channels block until both sender and receiver are ready**

- **Unbuffered channels**: Synchronous communication - sends block until a receiver is ready
- **Buffered channels**: Asynchronous up to buffer capacity - sends only block when buffer is full

```go
unbuffered := make(chan int)     // Synchronous
buffered := make(chan int, 3)    // Can hold 3 values before blocking
```

<!-- Card End -->

<!-- Card Start -->

### Front

What does the `go vet` tool do?

- A. Optimizes Go code for better performance
- B. Examines Go source code and reports suspicious constructs
- C. Formats Go code according to standard conventions
- D. Generates documentation from Go source code

### Back

**B. Examines Go source code and reports suspicious constructs**

`go vet` is a static analysis tool that examines Go source code and reports suspicious constructs that are likely to be bugs, such as unreachable code, shadowed variables, or incorrect printf format strings.

<!-- Card End -->

<!-- Card Start -->

### Front

How do you properly handle a panic in Go?

- A. Use try-catch blocks around the code
- B. Use `recover()` inside a deferred function
- C. Use `panic.Handle()` method
- D. Panics cannot be handled and will always crash the program

### Back

**B. Use `recover()` inside a deferred function**

`recover()` must be called inside a deferred function to catch panics. It returns the value passed to `panic()` and stops the panic from propagating.

```go
func safeFunction() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered from:", r)
        }
    }()
    panic("Something went wrong!")
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the correct way to iterate over a map in Go while ensuring deterministic order?

- A. Use `range` directly on the map
- B. Sort the keys first, then iterate over the sorted keys
- C. Use `map.Keys()` method
- D. Maps automatically maintain insertion order

### Back

**B. Sort the keys first, then iterate over the sorted keys**

Maps in Go have randomized iteration order for security reasons. To get deterministic order, you must extract and sort the keys first.

```go
keys := make([]string, 0, len(m))
for k := range m {
    keys = append(keys, k)
}
sort.Strings(keys)
for _, k := range keys {
    fmt.Println(k, m[k])
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary use case for Go's `sync.WaitGroup`?

- A. To limit the number of concurrent goroutines
- B. To wait for a collection of goroutines to finish
- C. To share data between goroutines safely
- D. To implement priority queues for goroutines

### Back

**B. To wait for a collection of goroutines to finish**

`sync.WaitGroup` is used to wait for multiple goroutines to complete their work before proceeding. It's essential for coordinating concurrent operations.

```go
var wg sync.WaitGroup
for i := 0; i < 5; i++ {
    wg.Add(1)
    go func(i int) {
        defer wg.Done()
        fmt.Println("Goroutine", i)
    }(i)
}
wg.Wait() // Blocks until all goroutines call Done()
```

<!-- Card End -->

<!-- Card Start -->

### Front

Which function is used to convert between different numeric types in Go?

- A. Go has automatic type conversion for compatible types
- B. Use type assertion syntax: value.(int)
- C. Use explicit type conversion: int(value)
- D. Use the `convert` package functions

### Back

**C. Use explicit type conversion: int(value)**

Go requires explicit type conversion for all numeric conversions, even between compatible types like `int` and `int64`. This prevents accidental precision loss.

```go
var i int = 42
var f float64 = float64(i)  // Must be explicit
var j int64 = int64(i)      // Must be explicit
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens when you send to a closed channel in Go?

- A. The send operation blocks indefinitely
- B. The send operation returns false
- C. The program panics
- D. The value is silently discarded

### Back

**C. The program panics**

Sending to a closed channel causes a runtime panic. This is different from receiving from a closed channel, which returns the zero value and false.

```go
ch := make(chan int)
close(ch)
ch <- 1 // This will panic: "send on closed channel"
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of Go's build tags (build constraints)?

- A. To version different builds of the same application
- B. To conditionally compile code based on build conditions
- C. To optimize code for different architectures automatically
- D. To generate documentation for different build targets

### Back

**B. To conditionally compile code based on build conditions**

Build tags allow conditional compilation based on factors like operating system, architecture, or custom tags, enabling platform-specific code.

```go
//go:build linux && amd64
// +build linux,amd64

package main

// This file only compiles on Linux AMD64 systems
```

<!-- Card End -->

<!-- Card Start -->

### Front

Which of the following best describes Go's approach to dependency management?

- A. Uses a centralized package repository like npm
- B. Relies on GOPATH exclusively for all dependencies
- C. Uses modules with semantic versioning and minimal version selection
- D. Requires manual downloading and linking of dependencies

### Back

**C. Uses modules with semantic versioning and minimal version selection**

Go modules (introduced in Go 1.11) use semantic versioning and a minimal version selection algorithm to resolve dependencies, providing reproducible builds without dependency conflicts.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the correct way to create a custom error with additional context in Go?

- A. Use `fmt.Errorf()` with format specifiers
- B. Create a struct that implements the error interface
- C. Use the `errors.New()` function with concatenation
- D. Both A and B are correct approaches

### Back

**D. Both A and B are correct approaches**

Go provides multiple ways to create custom errors:

```go
// Using fmt.Errorf (simple cases)
err := fmt.Errorf("operation failed: %w", originalErr)

// Custom struct (complex cases)
type ValidationError struct {
    Field string
    Value interface{}
}

func (e ValidationError) Error() string {
    return fmt.Sprintf("invalid value %v for field %s", e.Value, e.Field)
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between `append()` and manually assigning to slice indices?

- A. `append()` is always faster than manual assignment
- B. `append()` can grow the slice capacity, manual assignment cannot
- C. Manual assignment is type-safe, `append()` is not
- D. There is no functional difference

### Back

**B. `append()` can grow the slice capacity, manual assignment cannot**

`append()` automatically grows the underlying array when capacity is exceeded, while manual assignment to indices beyond the slice length will panic.

```go
s := make([]int, 2, 5)
s[0] = 1  // OK
s[1] = 2  // OK
// s[2] = 3  // This would panic - index out of range

s = append(s, 3)  // OK - extends the slice
```

<!-- Card End -->

<!-- Card Start -->

### Front

Which statement about Go's `interface{}` type is most accurate?

- A. It's equivalent to `Object` in Java
- B. It can hold any value but requires type assertion to access
- C. It provides runtime polymorphism for all types
- D. It's deprecated in favor of generics

### Back

**B. It can hold any value but requires type assertion to access**

`interface{}` (or `any` in Go 1.18+) can hold values of any type since all types implement the empty interface, but you need type assertions or type switches to access the underlying value.

```go
var x interface{} = 42
val, ok := x.(int)  // Type assertion
if ok {
    fmt.Println(val + 1)
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of the `go generate` command?

- A. To automatically generate Go code from templates
- B. To generate random test data for unit tests
- C. To run code generation tools as part of the build process
- D. To generate performance benchmarks

### Back

**C. To run code generation tools as part of the build process**

`go generate` scans for special comments in Go source files and executes the specified commands, typically used for code generation tools like stringer, mockgen, or protobuf generators.

```go
//go:generate stringer -type=Status
type Status int

const (
    Pending Status = iota
    Running
    Completed
)
```

<!-- Card End -->

<!-- Card Start -->

### Front

How does Go handle string immutability?

- A. Strings are mutable and can be modified in place
- B. Strings are immutable; operations create new strings
- C. String mutability depends on how they're declared
- D. Only string literals are immutable

### Back

**B. Strings are immutable; operations create new strings**

Strings in Go are immutable. Any operation that appears to modify a string actually creates a new string. For efficient string building, use `strings.Builder` or `bytes.Buffer`.

```go
s := "hello"
s += " world"  // Creates a new string, doesn't modify original
// Use strings.Builder for efficient concatenation
var builder strings.Builder
builder.WriteString("hello")
builder.WriteString(" world")
result := builder.String()
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary advantage of Go's statically linked binaries?

- A. Faster execution due to optimized linking
- B. Smaller binary sizes compared to dynamic linking
- C. Self-contained deployment without external dependencies
- D. Better security through code obfuscation

### Back

**C. Self-contained deployment without external dependencies**

Go's static linking creates self-contained binaries that include all dependencies, making deployment simpler and more reliable across different environments without worrying about missing libraries or version conflicts.

<!-- Card End -->

<!-- Card Start -->

### Front

Which Go feature helps prevent data races at compile time?

- A. The race detector (`-race` flag)
- B. Go's type system and escape analysis
- C. Automatic mutex insertion
- D. Channel-only communication

### Back

**A. The race detector (`-race` flag)**

While Go's design encourages race-free code, the race detector is a runtime tool (enabled at compile time with `-race`) that helps detect data races during testing and development.

```bash
go run -race main.go
go test -race ./...
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the recommended way to signal cancellation across multiple goroutines in Go?

- A. Use a shared boolean variable with mutex protection
- B. Use a dedicated "quit" channel
- C. Use the `context.Context` cancellation pattern
- D. Use `sync.Cond` for signaling

### Back

**C. Use the `context.Context` cancellation pattern**

The `context.Context` pattern is the idiomatic way to handle cancellation and timeouts across goroutines, providing a standardized approach for propagating cancellation signals.

```go
ctx, cancel := context.WithCancel(context.Background())
defer cancel()

go worker(ctx)
go worker(ctx)

// Later...
cancel() // Signals all workers to stop
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens when you range over a nil slice in Go?

- A. The program panics
- B. The loop executes once with zero values
- C. The loop doesn't execute at all
- D. It causes a compilation error

### Back

**C. The loop doesn't execute at all**

Ranging over a nil slice is safe in Go - the loop simply doesn't execute any iterations, similar to ranging over an empty slice.

```go
var s []int // nil slice
for i, v := range s {
    fmt.Println(i, v) // This never executes
}
fmt.Println("Loop completed") // This executes
```

<!-- Card End -->

<!-- Card Start -->

### Front

Which statement about Go's garbage collector tuning is correct?

- A. The GC can be completely disabled for better performance
- B. GOGC environment variable controls GC target percentage
- C. GC tuning requires recompiling the Go runtime
- D. The GC automatically adapts and cannot be configured

### Back

**B. GOGC environment variable controls GC target percentage**

The `GOGC` environment variable sets the target percentage for heap growth before the next GC cycle. The default is 100 (meaning GC triggers when heap doubles).

```bash
export GOGC=50   # More frequent GC
export GOGC=200  # Less frequent GC
export GOGC=off  # Disable GC (not recommended for most cases)
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the correct way to implement a timeout for a goroutine operation?

- A. Use `time.Sleep()` with error checking
- B. Use `context.WithTimeout()` and select statement
- C. Use `sync.Mutex` with timer
- D. Use `runtime.SetTimeout()` function

### Back

**B. Use `context.WithTimeout()` and select statement**

The idiomatic way to implement timeouts is using `context.WithTimeout()` combined with a `select` statement to handle both the operation and timeout.

```go
ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
defer cancel()

select {
case result := <-doWork(ctx):
    fmt.Println("Work completed:", result)
case <-ctx.Done():
    fmt.Println("Operation timed out")
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What is the difference between `var` declarations and short variable declarations (`:=`) in Go?

- A. `:=` can only be used inside functions
- B. `var` creates global variables, `:=` creates local variables
- C. `:=` requires type inference, `var` allows explicit types
- D. There is no functional difference

### Back

**A. `:=` can only be used inside functions**

Short variable declarations (`:=`) can only be used inside functions, while `var` declarations can be used at both package and function level. `:=` also performs both declaration and assignment.

```go
var globalVar int = 42  // OK at package level

func main() {
    var localVar int = 42   // OK
    shortVar := 42          // OK, equivalent to above
    
    // shortVar := 43 outside function would be a syntax error
}
```

<!-- Card End -->
