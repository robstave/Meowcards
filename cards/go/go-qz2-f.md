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

In Go, what is a rune?

- A. An alias for byte (uint8) representing a UTF-8 code unit
- B. An alias for int32 representing a Unicode code point
- C. A struct holding a grapheme cluster
- D. A UTF-16 code unit

### Back

**B. An alias for int32 representing a Unicode code point**

`rune` is a type alias for `int32`. It holds a Unicode scalar value (code point), independent of UTF-8 encoding. A single rune may be encoded as 1–4 bytes in UTF-8.

<!-- Card End -->

<!-- Card Start -->

### Front

What does `len(s)` return for a Go string containing UTF-8, and how do you get the rune count?

- A. `len(s)` returns rune count; `utf8.RuneCountInString(s)` returns bytes
- B. `len(s)` returns bytes; `utf8.RuneCountInString(s)` returns rune count
- C. Both return bytes
- D. Both return rune count

### Back

**B. `len(s)` returns bytes; `utf8.RuneCountInString(s)` returns rune count**

```go
s := "😺a"        // cat face + 'a'
fmt.Println(len(s))                     // 5 (UTF-8 bytes: 4 + 1)
fmt.Println(utf8.RuneCountInString(s))  // 2 (runes)
```

<!-- Card End -->

<!-- Card Start -->

### Front

Which statement about iterating a string in Go is correct?

- A. `for i := range s` yields runes; `s[i]` returns rune
- B. `for _, r := range s` yields runes; `s[i]` returns a byte (UTF-8 code unit)
- C. `for i := range s` yields bytes; `s[i]` returns bytes but `range` is invalid for UTF-8
- D. `for _, b := range s` yields bytes; `s[i]` returns runes

### Back

**B. `for _, r := range s` yields runes; `s[i]` returns a byte (UTF-8 code unit)**

`range` over a string decodes UTF-8 and yields rune values with `i` as the starting byte index of each rune. Direct indexing `s[i]` accesses a single byte, not a whole rune.

```go
for i, r := range s {              // r is rune, i is byte offset
    fmt.Printf("%d: %U\n", i, r)
}
b := s[0] // byte
```

<!-- Card End -->

<!-- Card Start -->

### Front

How do you safely take the first N characters (runes) of a string that may contain multi-byte UTF-8?

- A. Slice bytes: `s[:N]`
- B. Convert to `[]rune` and slice: `string([]rune(s)[:N])`
- C. Use `[]byte(s)[:N]` then cast back to string
- D. Use `len(s[:N])` to ensure rune boundary

### Back

**B. Convert to `[]rune` and slice: `string([]rune(s)[:N])`**

Converting to `[]rune` respects code point boundaries; slicing by bytes risks cutting a rune in the middle and producing invalid UTF-8.

```go
prefix := string([]rune(s)[:N])
```

For streaming, use `utf8.DecodeRuneInString` to step rune-by-rune without allocating a whole `[]rune`.

<!-- Card End -->

<!-- Card Start -->

### Front

What happens when decoding invalid UTF-8 with `utf8.DecodeRuneInString` and how can you validate a string?

- A. It panics; use recover to handle invalid bytes
- B. It returns `utf8.RuneError` and size 1; use `utf8.ValidString(s)` for validation
- C. It skips invalid bytes silently
- D. It returns zero rune and size 0

### Back

**B. It returns `utf8.RuneError` and size 1; use `utf8.ValidString(s)` for validation**

```go
r, size := utf8.DecodeRuneInString(s[i:])
if r == utf8.RuneError && size == 1 {
    // invalid UTF-8 byte encountered
}
fmt.Println(utf8.ValidString(s)) // true if s is valid UTF-8
```

Also useful: rune literals `'\u00E9'`, `'\U0001F431'`, and encoding with `utf8.EncodeRune`.

<!-- Card End -->

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
