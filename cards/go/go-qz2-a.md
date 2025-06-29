# Golang Interview Preparation Flashcards

Here is a comprehensive set of 65 multiple choice flashcards for Golang interview preparation, focusing on architecture, design decisions, and core concepts:

<!-- Card Start -->

### Front

What is the primary design philosophy behind Go's error handling?

A) Errors should be hidden from developers
B) Explicit error handling over exceptions
C) Automatic error recovery
D) Error handling through try-catch blocks

### Back

**B) Explicit error handling over exceptions**

Go's philosophy is "errors are values" - making error handling explicit and forcing developers to consciously handle errors rather than letting them propagate implicitly through exceptions.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go's goroutines more efficient than traditional OS threads?

A) They run on the GPU
B) They use less memory and have faster context switching
C) They can only run one at a time
D) They automatically handle errors

### Back

**B) They use less memory and have faster context switching**

Goroutines start with only 2KB of stack space (vs 2MB for OS threads) and are multiplexed onto OS threads by the Go runtime, making context switching much faster.

**Traditional OS Threads**:
- Heavy memory footprint: Each thread starts with 2MB of stack space.
- Expensive creation: Involves system calls and kernel management.
- High context switching cost: Requires saving/restoring CPU registers, switching memory spaces, and updating kernel data structures.
- Limited scalability: Typically supports thousands of threads before performance degrades.

**Goroutines**:
- Lightweight: Start with only 2KB of stack space.
- Fast creation: Created as simple function calls.
- Efficient scheduling: Many goroutines are multiplexed onto fewer OS threads by the Go runtime.
- Massive scalability: Can handle hundreds of thousands or even millions of goroutines efficiently.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the main advantage of Go's garbage collector design?

A) It never runs during program execution
B) Low-latency, concurrent collection with minimal stop-the-world pauses
C) It requires manual memory management
D) It only works with pointers

### Back

**B) Low-latency, concurrent collection with minimal stop-the-world pauses**

Go's GC is designed for low-latency applications, running concurrently with the program and minimizing pause times, typically under 1ms.

<!-- Card End -->

<!-- Card Start -->

### Front

Why doesn't Go support generics (prior to Go 1.18)?

A) Technical limitations
B) To maintain simplicity and fast compilation
C) Performance reasons
D) Memory constraints

### Back

**B) To maintain simplicity and fast compilation**

Go's original design prioritized simplicity, readability, and fast compilation. The team believed generics would complicate the language, though they were eventually added in Go 1.18 with careful design.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary purpose of Go's interface{} type?

A) To define method contracts
B) To represent any type (empty interface)
C) To handle errors
D) To create generic functions

### Back

**B) To represent any type (empty interface)**

`interface{}` is the empty interface that can hold values of any type, as every type implements at least zero methods. It's Go's way of achieving dynamic typing when needed.

<!-- Card End -->

<!-- Card Start -->

### Front

What advantage does Go's static linking provide?

A) Faster runtime performance
B) Self-contained binaries with no external dependencies
C) Smaller binary sizes
D) Better security

### Back

**B) Self-contained binaries with no external dependencies**

Go statically links dependencies by default, creating standalone binaries that don't require external libraries or runtime environments, simplifying deployment.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the main benefit of Go's composition over inheritance model?

A) Faster execution
B) More flexible and easier to test code organization
C) Automatic method generation
D) Better memory usage

### Back

**B) More flexible and easier to test code organization**

Go favors composition over inheritance, allowing for more flexible designs, easier testing, and avoiding the complexity and coupling issues common with deep inheritance hierarchies.

<!-- Card End -->

<!-- Card Start -->

### Front

Why does Go not support operator overloading?

A) Performance concerns
B) To maintain code clarity and predictability
C) Technical limitations
D) Memory management issues

### Back

**B) To maintain code clarity and predictability**

Go avoids operator overloading to keep code simple and predictable. When you see `+`, you know exactly what it does without needing to understand custom implementations.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go particularly suitable for microservices architecture?

A) Large runtime environment
B) Fast compilation, small binaries, excellent concurrency support
C) Complex dependency management
D) Rich OOP features

### Back

**B) Fast compilation, small binaries, excellent concurrency support**

Go's fast build times, lightweight binaries, built-in concurrency primitives, and strong networking libraries make it ideal for microservices development and deployment.

<!-- Card End -->

 

<!-- Card Start -->

### Front

What is the purpose of Go's `select` statement?

A) To choose between different data types
B) To handle multiple channel operations concurrently
C) To select files from the filesystem
D) To implement conditional logic

### Back

**B) To handle multiple channel operations concurrently**

The `select` statement in Go is a powerful construct for managing multiple channel operations. It allows a goroutine to:

- **Wait on multiple channels**: The `select` statement listens to multiple channel operations (send or receive) and proceeds with the one that is ready first.
- **Enable non-blocking communication**: By including a `default` case, `select` can perform non-blocking operations when no channels are ready.
- **Handle timeouts**: Using a `time.After` channel, `select` can implement timeouts for operations.

**Example Usage**:
```go
select {
case msg := <-ch1:
    fmt.Println("Received from ch1:", msg)
case ch2 <- "data":
    fmt.Println("Sent to ch2")
case <-time.After(time.Second):
    fmt.Println("Timeout occurred")
default:
    fmt.Println("No channel operations ready")
}
```
This example demonstrates how `select` can handle multiple channels, send/receive operations, and timeouts in a concise and readable manner.

https://go.dev/play/p/X7VtVqH0y0N



<!-- Card End -->

<!-- Card Start -->

### Front

What advantage does Go's built-in race detector provide?

A) Faster code execution
B) Automatic race condition fixes
C) Detection of concurrent access issues during testing
D) Memory optimization

### Back

**C) Detection of concurrent access issues during testing**

Go's race detector (enabled with `-race` flag) helps identify data races during testing by monitoring memory access patterns, crucial for writing safe concurrent code.

<!-- Card End -->

<!-- Card Start -->

### Front

Why does Go use package-based organization rather than classes?

A) Better performance
B) Simpler dependency management and clearer API boundaries
C) Reduced memory usage
D) Faster compilation

### Back

**B) Simpler dependency management and clearer API boundaries**

Go's package-based organization provides several key advantages:

1. **Clear API Boundaries**: 
   - Packages create strong boundaries between code units
   - Only exported (capitalized) names are visible outside packages, enforcing intentional API design
   - Removes ambiguity about what's public/private compared to multiple levels of access modifiers

2. **Dependency Management Benefits**:
   - Package imports are explicit and clearly visible at file tops
   - Circular dependencies between packages are not allowed, enforcing cleaner architecture
   - Go modules (introduced in Go 1.11) use packages as the basic unit of versioning

3. **Code Organization Improvements**:
   - Encourages grouping related functionality, not just related data structures
   - Makes refactoring easier as moving code between packages is simpler than restructuring class hierarchies
   - Simplifies testing as package boundaries are natural seams for test/mock interfaces

This approach aligns with Go's philosophy of simplicity and explicit design, reducing the complexity often found in deep class hierarchies.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the main advantage of Go's channels over traditional mutex-based synchronization?

A) Lower memory usage
B) Higher-level abstraction that encourages safer concurrent designs
C) Faster execution
D) Automatic deadlock detection

### Back

**B) Higher-level abstraction that encourages safer concurrent designs**

Channels follow the principle "Don't communicate by sharing memory; share memory by communicating," leading to more maintainable and less error-prone concurrent code.

**Channels vs Mutexes**:
- **Channels**:
  - Designed for communication between goroutines by passing messages, avoiding shared state entirely.
  - Simplify synchronization by eliminating the need for explicit locking and unlocking.
  - Ideal for "easy stuff" like producer-consumer patterns, fan-out/fan-in workflows, and signaling between goroutines.

- **Mutexes**:
  - Used for protecting shared memory by enforcing mutual exclusion.
  - Require careful handling to avoid deadlocks, race conditions, and other concurrency bugs.
  - Necessary for low-level synchronization or when shared state cannot be avoided.

**When to Use Channels**:
- When the problem can be modeled as message passing (e.g., sending tasks to workers).
- For coordinating goroutines without exposing shared memory.

**When to Use Mutexes**:
- When performance is critical, and the overhead of channels is too high.
- For fine-grained control over shared memory access.

By encouraging message passing, channels reduce the need for mutexes in many scenarios, making concurrent code easier to reason about and less prone to errors.

<!-- Card End -->

# mark

<!-- Card Start -->

### Front

What makes Go's compilation speed exceptionally fast?

A) Simple syntax and efficient dependency resolution
B) Lack of features
C) Small standard library
D) Limited type system

### Back

**A) Simple syntax and efficient dependency resolution**

Go's fast compilation comes from deliberate design choices: simple syntax, efficient import system, no circular dependencies, and a streamlined compilation process.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary use case for Go's `context` package?

A) Error handling
B) Cancellation signals and request-scoped values across API boundaries
C) Memory management
D) Type conversion

### Back

**B) Cancellation signals and request-scoped values across API boundaries**

The `context` package provides a standardized way to carry cancellation signals, timeouts, and request-scoped values across API boundaries and goroutines.

**Key Context Features**:

1. **Cancellation Propagation**:
   - Allows parent operations to signal cancellation to all descendant operations
   - Enables graceful shutdown of long-running operations when they're no longer needed
   - Example: Canceling an HTTP request should stop all database queries and other operations triggered by that request


2. **Deadline Management**:
   - Provides automatic timeout functionality with `WithTimeout` and `WithDeadline`
   - Ensures operations don't run longer than intended, preventing resource leakage

   
```go
   package main

import (
	"context"
	"fmt"
	"time"
)

func fakeAPICall(ctx context.Context) error {
	select {
	case <-time.After(3 * time.Second): // Simulate a slow API call
		fmt.Println("API call finished")
		return nil
	case <-ctx.Done(): // Context was cancelled or timed out
		fmt.Println("API call canceled:", ctx.Err())
		return ctx.Err()
	}
}

func main() {
	// Timeout after 2 seconds
	ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
	defer cancel()

	err := fakeAPICall(ctx)
	if err != nil {
		fmt.Println("Handled error:", err)
	} else {
		fmt.Println("Success")
	}
}
```

3. **Request-Scoped Values**:
   - Carries request-specific data (e.g., user ID, auth tokens, request ID) through call chains
   - Avoids having to pass many parameters through every function in the call stack

**Common Usage Patterns**:

```go
// Creating a context with timeout
ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
defer cancel() // Always call cancel to release resources

// Using context to control an HTTP request
req, _ := http.NewRequestWithContext(ctx, "GET", url, nil)
resp, err := http.DefaultClient.Do(req)
if err != nil {
    // This could be due to the timeout or cancellation
}

// Passing request-scoped values
ctx = context.WithValue(ctx, "userID", "12345")
// Later retrieve it
userID, ok := ctx.Value("userID").(string)
```

The context pattern is essential for proper resource management in Go services, especially for handling concurrent requests in web servers and managing API dependencies.

<!-- Card End -->

<!-- Card Start -->

### Front

Why doesn't Go support exceptions?

A) Performance reasons
B) To encourage explicit error handling and program clarity
C) Technical limitations
D) Memory constraints

### Back

**B) To encourage explicit error handling and program clarity**

Go avoids exceptions to force developers to explicitly handle errors where they occur, leading to more predictable control flow and clearer error handling paths.

<!-- Card End -->

<!-- Card Start -->

### Front

What advantage does Go's zero-value concept provide?

A) Better performance
B) Eliminates uninitialized variable bugs and provides sensible defaults
C) Reduced memory usage
D) Faster compilation

### Back

**B) Eliminates uninitialized variable bugs and provides sensible defaults**

Every type in Go has a meaningful zero value (0 for numbers, "" for strings, nil for pointers), eliminating undefined behavior from uninitialized variables.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go interfaces particularly powerful?

A) Implicit implementation and duck typing
B) Multiple inheritance support
C) Automatic method generation
D) Runtime type checking

### Back

**A) Implicit implementation and duck typing**

Go interfaces are satisfied implicitly - if a type has the required methods, it implements the interface. This enables flexible, loosely-coupled designs and easy testing.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the main benefit of Go's `go fmt` tool?

A) Code optimization
B) Error detection
C) Enforces consistent code formatting across all Go code
D) Performance profiling

### Back

**C) Enforces consistent code formatting across all Go code**

`go fmt` eliminates formatting debates by enforcing a single, consistent code style across all Go projects, improving readability and reducing code review friction.

<!-- Card End -->

<!-- Card Start -->

### Front

Why is Go considered good for network programming?

A) Built-in GUI support
B) Excellent standard library with net/http, built-in concurrency
C) Automatic protocol handling
D) Database integration

### Back

**B) Excellent standard library with net/http, built-in concurrency**

Go's standard library includes robust networking packages, and its goroutines make it easy to handle thousands of concurrent network connections efficiently.

<!-- Card End -->

<!-- Card Start -->

### Front

What problem does Go's vendor directory solve?

A) Dependency versioning and reproducible builds
B) Code organization
C) Performance optimization
D) Memory management

### Back

**A) Dependency versioning and reproducible builds**

The vendor directory was a mechanism in Go to ensure reproducible builds by including specific versions of dependencies directly in the project. This approach solved the "dependency hell" problem by isolating dependencies from external changes. Although Go modules have largely replaced the vendor directory, it remains a useful tool for projects requiring strict control over dependency versions or offline builds.

<!-- Card Start -->

### Front

What is the main advantage of Go's struct embedding?

A) Memory optimization
B) Composition-based inheritance and method promotion
C) Type safety
D) Performance improvement

### Back

**B) Composition-based inheritance and method promotion**

Struct embedding allows composition-based "inheritance" where embedded types' methods are promoted to the embedding type, providing inheritance-like behavior through composition.

<!-- Card End -->

<!-- Card Start -->

### Front

Why does Go prefer short variable names in limited scopes?

A) Memory efficiency
B) Readability in context and reduced visual noise
C) Faster typing
D) Compilation speed

### Back

**B) Readability in context and reduced visual noise**

Go encourages short names in limited scopes (like `i` for loop counters) because the context makes the meaning clear, while longer names are used for broader scopes.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go's testing package unique?

A) Automatic test generation
B) Built-in table-driven testing support and simplicity
C) GUI test runner
D) Automatic mocking

### Back

**B) Built-in table-driven testing support and simplicity**

Go's testing package is simple yet powerful, encouraging table-driven tests and providing built-in benchmarking, making testing a first-class citizen in Go development.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary benefit of Go's modules system (introduced in Go 1.11)?

A) Faster compilation
B) Semantic versioning and dependency management outside GOPATH
C) Better performance
D) Reduced binary size

### Back

**B) Semantic versioning and dependency management outside GOPATH**

Go modules enable projects to exist outside GOPATH, provide semantic versioning, and offer better dependency management with reproducible builds.

<!-- Card End -->

<!-- Card Start -->

### Front

Why does Go not support method overloading?

A) Performance concerns
B) To maintain simplicity and avoid ambiguity
C) Memory limitations
D) Compilation complexity

### Back

**B) To maintain simplicity and avoid ambiguity**

Go avoids method overloading to keep the language simple and prevent the ambiguity and complexity that can arise from multiple methods with the same name but different signatures.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go particularly suitable for CLI tools?

A) GUI support
B) Fast compilation, static linking, and cross-compilation
C) Database connectivity
D) Web framework support

### Back

**B) Fast compilation, static linking, and cross-compilation**

Go's fast build times, self-contained binaries, and easy cross-compilation make it excellent for building CLI tools that can be distributed as single executables.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the purpose of Go's `init()` function?

A) Constructor for structs
B) Package initialization before main() or other functions
C) Error handling
D) Memory allocation

### Back

**B) Package initialization before main() or other functions**

`init()` functions run automatically before `main()` (or before the package is used), allowing for package-level initialization and setup that must happen before other code runs.

<!-- Card End -->

<!-- Card Start -->

### Front

What advantage does Go's slice design provide over arrays?

A) Better type safety
B) Dynamic sizing with underlying array efficiency
C) Automatic memory management
D) Faster iteration

### Back

**B) Dynamic sizing with underlying array efficiency**

Slices provide a dynamic view over underlying arrays, combining the efficiency of arrays with the flexibility of dynamic resizing, while sharing memory efficiently.

<!-- Card End -->

<!-- Card Start -->

### Front

Why does Go use UTF-8 as its default string encoding?

A) Performance reasons
B) Universal Unicode support with ASCII compatibility
C) Memory efficiency
D) Simplicity

### Back

**B) Universal Unicode support with ASCII compatibility**

UTF-8 provides full Unicode support while being backward compatible with ASCII, making Go internationally friendly without breaking existing ASCII-based tools and systems.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go's map implementation efficient?

A) Sorted keys
B) Hash table with efficient collision handling
C) Array-based storage
D) Linked list implementation

### Back

**B) Hash table with efficient collision handling**

Go's maps use hash tables with sophisticated collision resolution, providing average O(1) access time while handling hash collisions efficiently.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the main benefit of Go's `defer` statement for resource management?

A) Performance optimization
B) Guaranteed cleanup execution regardless of exit path
C) Memory allocation
D) Error prevention

### Back

**B) Guaranteed cleanup execution regardless of exit path**

`defer` ensures cleanup code runs when the function exits, regardless of whether it exits normally, returns early, or panics, making resource management more reliable.

<!-- Card End -->

<!-- Card Start -->

### Front

Why does Go not support traditional while loops?

A) Performance reasons
B) `for` loop provides all necessary iteration patterns
C) Memory efficiency
D) Compilation simplicity

### Back

**B) `for` loop provides all necessary iteration patterns**

Go's `for` loop can handle all iteration patterns (while, do-while, traditional for), reducing language complexity while maintaining full functionality.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go's concurrency model different from async/await patterns?

A) Go uses callbacks
B) Goroutines and channels provide CSP-style communication
C) Go is single-threaded
D) Go uses promises

### Back

**B) Goroutines and channels provide CSP-style communication**

Go implements Communicating Sequential Processes (CSP), where independent goroutines communicate through channels, rather than async/await's promise-based approach.

**B) CSP separates communication channels from processing entities**

**CSP (Communicating Sequential Processes)** is a concurrency model where processes (goroutines in Go) communicate by passing messages through channels, rather than sharing memory. This model emphasizes:

- **Message Passing**: Processes interact by sending and receiving messages over channels, avoiding shared state and reducing the risk of race conditions.
- **Channel as First-Class Citizen**: Channels are independent of the processes, allowing multiple goroutines to communicate flexibly.
- **Synchronization**: Sending and receiving on unbuffered channels is synchronous, ensuring coordination between goroutines.

**Comparison to Actor Model**:
- In the actor model, each actor has its own mailbox for receiving messages, tightly coupling communication to the actor.
- CSP's decoupling of channels from processes allows for more dynamic and reusable communication patterns, such as broadcasting or load balancing across multiple goroutines.

This separation in CSP enables Go to efficiently handle concurrent workloads with clear and predictable communication patterns.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the main advantage of Go's build constraints (build tags)?

A) Performance optimization
B) Conditional compilation for different platforms/environments
C) Faster compilation
D) Memory efficiency

### Back

**B) Conditional compilation for different platforms/environments**

Build tags allow conditional compilation, enabling platform-specific code, feature flags, and environment-specific builds without runtime overhead.

<!-- Card End -->

<!-- Card Start -->

### Front

Why does Go encourage small interfaces?

A) Performance benefits
B) Easier to implement, test, and maintain (interface segregation)
C) Memory efficiency
D) Faster compilation

### Back

**B) Easier to implement, test, and maintain (interface segregation)**

Small, focused interfaces follow the Interface Segregation Principle, making code more modular, easier to test with mocks, and easier to implement incrementally.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go's reflection capabilities unique?

A) Compile-time reflection
B) Runtime type inspection with laws of reflection
C) Automatic code generation
D) Performance optimization

### Back

**B) Runtime type inspection with laws of reflection**

Go's reflection follows three laws: reflection goes from interface value to reflection object, from reflection object to interface value, and to modify a reflection object, the value must be settable.

<!-- Card End -->

<!-- Card Start -->

### Front

What problem does Go's escape analysis solve?

A) Security vulnerabilities
B) Automatic stack vs heap allocation decisions
C) Race conditions
D) Memory leaks

### Back

**B) Automatic stack vs heap allocation decisions**

Go's escape analysis determines whether variables should be allocated on the stack or heap, optimizing memory allocation without programmer intervention while maintaining memory safety.

<!-- Card End -->

<!-- Card Start -->

### Front

Why is Go considered good for containerized applications?

A) Built-in Docker support
B) Small static binaries and minimal runtime requirements
C) Automatic scaling
D) Container orchestration features

### Back

**B) Small static binaries and minimal runtime requirements**

Go produces small, self-contained binaries with no external dependencies, making them ideal for containers where minimizing image size and complexity is crucial.

<!-- Card End -->

<!-- Card Start -->

### Front

What advantage does Go's pointer design provide over C/C++?

A) Automatic dereferencing
B) Memory safety without pointer arithmetic
C) Faster access
D) Automatic allocation

### Back

**B) Memory safety without pointer arithmetic**

Go provides the benefits of pointers (efficiency, reference semantics) while eliminating dangerous pointer arithmetic, preventing buffer overflows and memory corruption.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go's standard library philosophy distinctive?

A) Minimal functionality
B) "Batteries included" with consistent, well-designed APIs
C) Third-party dependencies
D) Platform-specific implementations

### Back

**B) "Batteries included" with consistent, well-designed APIs**

Go's standard library is comprehensive and well-designed, providing most common functionality out of the box with consistent APIs, reducing the need for external dependencies.

<!-- Card End -->

<!-- Card Start -->

### Front

Why does Go use explicit type conversions rather than implicit ones?

A) Performance reasons
B) Type safety and clarity of intent
C) Memory efficiency
D) Compilation speed

### Back

**B) Type safety and clarity of intent**

Explicit type conversions prevent subtle bugs from implicit conversions and make the programmer's intent clear, reducing unexpected behavior and improving code reliability.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go particularly suitable for DevOps and infrastructure tools?

A) GUI capabilities
B) Fast compilation, static binaries, excellent CLI and network support
C) Database integration
D) Web frameworks

### Back

**B) Fast compilation, static binaries, excellent CLI and network support**

Go's fast builds, self-contained binaries, strong networking libraries, and excellent CLI support make it ideal for creating DevOps tools, monitoring systems, and infrastructure automation.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the main benefit of Go's method sets and interface satisfaction rules?

A) Performance optimization
B) Clear rules for interface implementation and embedding behavior
C) Memory efficiency
D) Compilation speed

### Back

**B) Clear rules for interface implementation and embedding behavior**

Go's method sets provide clear, predictable rules for when types satisfy interfaces, especially with pointer vs value receivers, ensuring consistent behavior in interface-based designs.

<!-- Card End -->

<!-- Card Start -->

### Front

Why does Go not support generic types (prior to 1.18) but supports generic functions through interfaces?

A) Technical limitations
B) Interface{} and type assertions provided sufficient flexibility
C) Performance concerns
D) Compilation complexity

### Back

**B) Interface{} and type assertions provided sufficient flexibility**

Before generics, Go used `interface{}` with type assertions and interfaces to achieve polymorphism, which the designers felt provided sufficient flexibility while maintaining language simplicity.

<!-- Card End -->

<!-- Card Start -->

### Front

What makes Go's garbage collector well-suited for server applications?

A) No garbage collection
B) Low-latency, concurrent collection with minimal stop-the-world pauses
C) It only runs when the application is idle
D) It moves all memory management to disk

### Back

**B) Low-latency, concurrent collection with minimal stop-the-world pauses**

Go's garbage collector is designed for predictable, low-latency performance with sub-millisecond pauses, making it ideal for responsive server applications that handle many concurrent requests.

<!-- Card End -->

<!-- Card Start -->

### Front

Which feature best represents Go's approach to API design?

A) Extensive use of operator overloading
B) Composition over inheritance
C) Dependency injection frameworks
D) Runtime reflection for all operations

### Back

**B) Composition over inheritance**

Go deliberately omits inheritance in favor of composition through embedded types and interfaces, leading to simpler, more flexible code that avoids deep class hierarchies and the "diamond problem" of multiple inheritance.

<!-- Card End -->

<!-- Card Start -->

### Front

What architectural pattern does Go's standard library HTTP server implement?

A) Model-View-Controller
B) Event-driven architecture
C) Handler pattern
D) Aspect-oriented programming

### Back

**C) Handler pattern**

Go's HTTP server implements the Handler pattern through the `http.Handler` interface, allowing any type with a `ServeHTTP` method to process HTTP requests. This enables clean separation of concerns and middleware chains for request processing.

<!-- Card End -->

<!-- Card Start -->

### Front

What does "zero value" initialization mean in Go's design philosophy?

A) All variables must be explicitly initialized
B) Variables are always initialized to nil
C) Every type has a useful default state without explicit initialization
D) Variables start with random values until assigned

### Back

**C) Every type has a useful default state without explicit initialization**

Go initializes variables to their "zero value" (0 for numeric types, false for booleans, "" for strings, nil for pointers/slices/maps/channels), ensuring safe usage without explicit initialization and eliminating a whole class of undefined behavior bugs.

<!-- Card End -->
 