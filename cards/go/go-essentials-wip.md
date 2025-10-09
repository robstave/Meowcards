<!-- Card Start -->

### Front
 
 In Go, a **method set** is the collection of all methods that are accessible on a particular type or pointer to that type.

The method set determines which interfaces a type satisfies and follows specific rules:

**For a value of type `T`:**
- Its method set includes all methods with a receiver of type `T`
- It does NOT include methods with a receiver of type `*T`

**For a value of type `*T` (pointer):**
- Its method set includes methods with a receiver of type `T` AND methods with a receiver of type `*T`
- In other words, pointer types have a superset of the methods available to value types

**Why this matters:**

```go
type Counter struct {
    count int
}

// Value receiver
func (c Counter) Get() int {
    return c.count
}

// Pointer receiver
func (c *Counter) Increment() {
    c.count++
}
```

In this example:
- `Counter` has a method set of just `Get()`
- `*Counter` has a method set of both `Get()` and `Increment()`

This is crucial for interface satisfaction: if an interface requires `Increment()`, only `*Counter` satisfies it, not `Counter`. The distinction exists because methods with pointer receivers need to be able to modify the receiver, which requires an addressable value.




### Back

none

<!-- Card End -->

<!-- Card Start -->

### Front


maps require initialization before use. You can create a map using the `make` function:

if you try to read from or write to a nil map, it will cause a runtime panic.

so this will not work
```go
 var m map[string]int // m is nil

    m["k1"] = 7        // panic: assignment to entry in nil map
    fmt.Println(m)
```

examples



```go
 package main

import (
    "fmt"
    "maps"
)

func main() {

    m := make(map[string]int)

    m["k1"] = 7
    m["k2"] = 13

    fmt.Println("map:", m)

    v1 := m["k1"]
    fmt.Println("v1:", v1)

    v3 := m["k3"]
    fmt.Println("v3:", v3)

    fmt.Println("len:", len(m))

    delete(m, "k2")
    fmt.Println("map:", m)

    clear(m)
    fmt.Println("map:", m)

    _, prs := m["k2"]
    fmt.Println("prs:", prs)

    n := map[string]int{"foo": 1, "bar": 2}
  
    }
}
```
 
### Back

none

<!-- Card End -->

<!-- Card Start -->

### Front 

A typical pattern in Go is to embed a struct within another struct to promote its fields and methods. This allows the fields and methods of the embedded struct to be accessed directly on the embedding struct, enabling composition over inheritance.

When embedding a `sync.Mutex` in a struct, it ensures thread-safe access to the struct's data. Note that the zero value of `sync.Mutex` is ready to use, so no explicit initialization is required.

Here is an example of initializing a struct with an embedded `sync.Mutex`:

```go
type MyMap struct {
    data map[string]string
    mu   sync.Mutex
}

func NewMyMap() *MyMap {
    return &MyMap{
        data: make(map[string]string),
    }
}

func (m *MyMap) Set(key, value string) {
    m.mu.Lock()
    defer m.mu.Unlock()
    m.data[key] = value
}

func (m *MyMap) Get(key string) (string, bool) {
    m.mu.Lock()
    defer m.mu.Unlock()
    val, ok := m.data[key]
    return val, ok
}

m := NewMyMap()
m.Set("key1", "value1")
value, exists := m.Get("key1")
fmt.Println(value, exists)
```

This pattern ensures that the `data` map is protected by the mutex, making it safe for concurrent access.

### Back

Embedding a `sync.Mutex` in a struct is a common idiomatic pattern in Go for ensuring thread-safe access to shared data. The zero value of `sync.Mutex` is ready to use, so no explicit initialization is needed. This approach ties the mutex to the data it protects, promoting better encapsulation and reducing the risk of misuse.
<!-- Card End -->










<!-- Card Start -->

### Front

```go
// MAP - zero value is nil and NOT usable
var m map[string]string
m["key"] = "value"  // PANIC! Must use make()

// SLICE - zero value is nil but IS usable
var s []string
s = append(s, "value")  // Works fine! No make() needed
```

If you know the size upfront, make() can be more efficient:
```go
s := make([]string, 0, 10) // len=0, cap=10
s = append(s, "value")      // Works fine, no reallocation until >10
```

 
### Back

none

<!-- Card End -->

<!-- Card Start -->

### Front


Embedding a struct in Go allows you to promote its fields and methods to the embedding struct, enabling direct access without explicit qualification. This is useful for composition and code reuse.

Fields and methods of the embedded struct can be accessed directly on the embedding struct.
They are promoted to the embedding struct.

```go

 package main

import "fmt"

type ID struct {
	Name string
	Age  int
}
type Wallet struct{ Value int }

type Person struct {
	ID
	Wallet
}

func main() {
	anId := ID{
		Name: "Rob",
		Age:  33,
	}
	aPerson := Person{}
	aPerson.Value = 44
	aPerson.ID = anId

	fmt.Printf("Hello %s\n", aPerson.Name)
	fmt.Printf("value:%d\n", aPerson.Wallet.Value)
	fmt.Printf("value:%d\n", aPerson.Value)

}

```
 
### Back
https://go.dev/play/p/tnHJhrMPbVm
none

<!-- Card End -->


<!-- Card Start -->

### Front
 
### Back

none

<!-- Card End -->

<!-- Card Start -->

### Front

**What is `iota` in Go and how is it used?**

### Back

`iota` is a predeclared identifier in Go used to simplify the creation of enumerated constants. It starts at 0 and increments by 1 for each constant in a block.

Example:

```go
const (
    A = iota // 0
    B        // 1
    C        // 2
)

fmt.Println(A, B, C) // Output: 0 1 2
```

`iota` is reset to 0 whenever a new `const` block is started.

---

<!-- Card End -->
 
 

<!-- Card Start -->

### Front

```go
package main
import "fmt"

func main() {

	myMap := map[string]int{}
	myMap["fred"] = 3
	myMap["george"] = 6
	fmt.Println(myMap)
}

```

### Back
none
<!-- Card End -->




 



<!-- Card Start -->
### Front

**How do you convert an array to a slice in Go?**

### Back

In Go, you can convert an array to a slice by slicing it using the `[:]` syntax. This creates a slice that references the same underlying array.

Example:

```go
func main() {
    arr := [3]int{3, 2, 4} // Array of fixed size
    slc := arr[:]          // Slice referencing the array
    fmt.Println(slc)       // Output: [3 2 4]
}
```

Key Points:
- The slice shares the same underlying data as the array.
- Modifying the slice will also modify the array, and vice versa.
<!-- Card End -->



<!-- Card Start -->
### Front

**what is a function literal in Go?**

### Back

A function literal in Go is an anonymous function that is defined inline and can be assigned to a variable, passed as an argument, or executed immediately. It is a way to create functions without naming them.

Example:

```go
func main() {
    add := func(a, b int) int {
        return a + b
    }
    fmt.Println(add(3, 4)) // Output: 7
}
```
 
 
<!-- Card End -->
