# Golang Interview Preparation Flashcards - Set F

<!-- Card Start -->

### Front

How can you implement a stack in Go using slices?

- A. Use a built-in stack type
- B. Use slices with append and slicing
- C. Use a map with integer keys
- D. Use a linked list

### Back

**B. Use slices with append and slicing**

Go does not have a built-in stack type, but you can implement a stack using slices. The `append` function is used to push elements, and slicing is used to pop elements.

```go
package main

import "fmt"

func main() {
    stack := []int{}

    // Push
    stack = append(stack, 1)
    stack = append(stack, 2)
    fmt.Println("Stack after push:", stack)

    // Pop
    top := stack[len(stack)-1]
    stack = stack[:len(stack)-1]
    fmt.Println("Popped element:", top)
    fmt.Println("Stack after pop:", stack)
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What does this code do?

```go
stack := []int{1, 2, 3}
stack = append(stack, 4)
fmt.Println(stack)
```

- A. Adds 4 to the stack
- B. Removes 4 from the stack
- C. Clears the stack
- D. Prints the stack without modification

### Back

**A. Adds 4 to the stack**

The `append` function adds an element to the end of the slice, effectively pushing it onto the stack.

Output:
```plaintext
[1, 2, 3, 4]
```

<!-- Card End -->

<!-- Card Start -->

### Front

How can you implement a "peek" operation for a stack in Go?

- A. Use the first element of the slice
- B. Use the last element of the slice
- C. Use a map with integer keys
- D. Use a linked list

### Back

**B. Use the last element of the slice**

The "peek" operation retrieves the top element of the stack without removing it. In Go, this can be done by accessing the last element of the slice.

```go
package main

import "fmt"

func main() {
    stack := []int{1, 2, 3}

    // Peek
    top := stack[len(stack)-1]
    fmt.Println("Top element:", top)
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What does this code do?

```go
stack := []int{1, 2, 3}
stack = stack[:len(stack)-1]
fmt.Println(stack)
```

- A. Adds an element to the stack
- B. Removes the top element from the stack
- C. Clears the stack
- D. Prints the stack without modification

### Back

**B. Removes the top element from the stack**

Slicing the stack to exclude the last element effectively pops the top element off the stack.

Output:
```plaintext
[1, 2]
```

<!-- Card End -->

<!-- Card Start -->

### Front

How can you implement a "clear" operation for a stack in Go?

- A. Set the slice to nil
- B. Use the `clear` function
- C. Use a map with integer keys
- D. Use a linked list

### Back

**A. Set the slice to nil**

To clear a stack implemented with a slice, you can set the slice to nil or an empty slice.

```go
package main

import "fmt"

func main() {
    stack := []int{1, 2, 3}

    // Clear
    stack = nil
    fmt.Println("Stack after clear:", stack)
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What does this code do?

```go
stack := []int{1, 2, 3}
stack = append([]int{0}, stack...)
fmt.Println(stack)
```

- A. Adds 0 to the stack
- B. Removes 0 from the stack
- C. Prepends 0 to the stack
- D. Clears the stack

### Back

**C. Prepends 0 to the stack**

The `append` function with slicing can be used to prepend an element to the stack.

Output:
```plaintext
[0, 1, 2, 3]
```

<!-- Card End -->

<!-- Card Start -->

### Front

How can you iterate over all keys and values in a Go map?

- A. Use a `for` loop with `range`
- B. Use a `while` loop
- C. Use a `for` loop with integer indices
- D. Use a `foreach` function

### Back

**A. Use a `for` loop with `range`**

In Go, you can iterate over all keys and values in a map using a `for` loop with the `range` keyword.

```go
package main

import "fmt"

func main() {
    m := map[string]int{"a": 1, "b": 2, "c": 3}

    for key, value := range m {
        fmt.Printf("Key: %s, Value: %d\n", key, value)
    }
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

How can you check if a key exists in a Go map?

- A. Use the `contains` function
- B. Use the `in` operator
- C. Use the `value, ok := map[key]` syntax
- D. Use a `for` loop

### Back

**C. Use the `value, ok := map[key]` syntax**

In Go, you can check if a key exists in a map by using the `value, ok := map[key]` syntax. The `ok` variable will be `true` if the key exists and `false` otherwise.

```go
package main

import "fmt"

func main() {
    m := map[string]int{"a": 1, "b": 2}

    value, ok := m["a"]
    if ok {
        fmt.Println("Key exists with value:", value)
    } else {
        fmt.Println("Key does not exist")
    }
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

How can you delete a key from a Go map?

- A. Use the `delete` function
- B. Use the `remove` function
- C. Use the `clear` function
- D. Use a `for` loop

### Back

**A. Use the `delete` function**

In Go, you can delete a key from a map using the `delete` function.

```go
package main

import "fmt"

func main() {
    m := map[string]int{"a": 1, "b": 2}

    delete(m, "a")
    fmt.Println("Map after deletion:", m)
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

How can you initialize a map in Go?

- A. Use the `new` function
- B. Use the `make` function
- C. Use the `init` function
- D. Use a `for` loop

### Back

**B. Use the `make` function**

In Go, you can initialize a map using the `make` function.

```go
package main

import "fmt"

func main() {
    m := make(map[string]int)
    m["a"] = 1
    m["b"] = 2
    fmt.Println("Initialized map:", m)
}
```

<!-- Card End -->
