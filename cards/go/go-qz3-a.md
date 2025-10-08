<!-- Card Start -->
### Front
In Go, what is a variadic function and how do you declare one?

### Back
A variadic function accepts zero or more arguments of a specified type using the `...T` syntax as the final parameter.

```go
func sum(nums ...int) int {
	total := 0
	for _, v := range nums { // v is the value
		total += v
	}
	return total
}

sum()            // 0
sum(1, 2, 3, 4)  // 10
```

Rules:
- Only the last parameter can be variadic
- Inside the function, `nums` behaves like a slice `[]int`
- Callers can pass zero or many arguments

<!-- Card End -->

<!-- Card Start -->
### Front
How do you forward a slice to a variadic parameter, and what is the difference between passing the slice and using `...`?

### Back
Use the `...` expansion to pass each element as an argument. Without it, the slice itself is a single argument (type mismatch if not `[]T`).

```go
func logAll(vals ...string) { /* ... */ }

items := []string{"a", "b", "c"}
logAll(items...) // expands to logAll("a", "b", "c")

// logAll(items) // compile error: []string not assignable to ...string without expansion

// note also
// items := [...]string{"a", "b", "c"}
// logAll(items) // cannot use sliceONames (variable of type [3]string) as []string value in argument

// because [3]string is an array type, not a slice type
```

You can also capture remaining args:
```go
func headAndTail(head string, tail ...string) { }
```

<!-- Card End -->

<!-- Card Start -->
### Front
What are ordering, zero-argument, and mixing rules for variadic parameters in Go?

### Back
Rules:
- Variadic parameter must be last: `func f(a int, rest ...string)`
- Zero args OK: `f(3)` gives `rest == []string{}`
- You can mix fixed + variadic: `func join(sep string, parts ...string)`
- Within the function the variadic parameter is an ordinary slice (can re-slice, iterate, len/appends)

Example:
```go
func join(sep string, parts ...string) string {
	return strings.Join(parts, sep)
}
join(",", "a", "b", "c") // "a,b,c"
```

<!-- Card End -->

<!-- Card Start -->
### Front
What performance considerations apply to variadic functions in Go?

### Back
Each call creates a slice header (and may allocate a new backing array when args are passed). For hot paths:
- Prefer taking an explicit `[]T` slice if callers already have one
- Avoid per-call allocations by reusing a pre-allocated slice (when using explicit slice parameter)
- Small arg counts are usually fine; measure before optimizing

Micro-optimization example:
```go
// Variadic (may allocate on each call)
func add(nums ...int) int { /* ... */ }

// Slice form (caller controls allocation)
func addSlice(nums []int) int { /* ... */ }
```

Use benchmarks (`go test -bench .`) to decide.

<!-- Card End -->

<!-- Card Start -->
### Front
What is the difference between `made := make([]int, 5)` and `madeCap := make([]int, 0, 8)` in Go?

### Back
`make([]int, 5)` creates a slice with:
- len = 5, cap = 5
- Elements initialized to zero values (0s)
- Valid indices: 0..4 immediately usable

`make([]int, 0, 8)` creates a slice with:
- len = 0, cap = 8
- No elements yet (cannot index until appended)
- First append does not allocate (space pre-reserved up to 8)

Example:
```go
made := make([]int, 5)      // [0 0 0 0 0]
madeCap := make([]int, 0, 8) // [] len=0 cap=8

made[2] = 42        // OK (already length 5)
// madeCap[0] = 1   // panic: index out of range (len=0)
madeCap = append(madeCap, 1,2,3) // grows len to 3, cap still 8
```

Use the second form when preallocating capacity for future appends without paying for initial length.

<!-- Card End -->

<!-- Card Start -->
### Front
How do growth and mutation differ after creating `made := make([]int,5)` vs `madeCap := make([]int,0,8)`?

### Back
Mutation:
- `made` allows direct index assignment immediately (len==5)
- `madeCap` requires `append` before indexing (len starts at 0)

Growth behavior:
- Appending to `made` (cap=5) triggers allocation once len exceeds 5
- Appending up to 8 items into `madeCap` uses existing capacity (no reallocation) then grows

Illustration:
```go
made := make([]int, 5)      // len=5 cap=5
made = append(made, 99)     // len=6 cap likely 10 (implementation-dependent growth)

madeCap := make([]int,0,8)  // len=0 cap=8
for i:=0;i<8;i++ { madeCap = append(madeCap, i) } // len=8 cap=8 no allocs
madeCap = append(madeCap, 8) // triggers reallocation (cap grows, e.g., 16)
```

Rule of thumb:
- Use non-zero length when you need an initialized fixed-size working slice immediately.
- Use zero length with extra capacity when you plan to build the slice incrementally.

<!-- Card End -->

<!-- Card Start -->
### Front
What is `strings.Builder` in Go and why use it?

### Back
`strings.Builder` efficiently builds strings by minimizing allocations and copies. Instead of repeated `s += part` (which creates new strings each time), the builder writes into a growable buffer and produces a string once with `String()`.

Benefits:
- Fewer allocations for multi-append workloads
- Clear, incremental construction API
- `WriteString`, `WriteByte`, `WriteRune`, `Write` for flexibility

Example:
```go
var b strings.Builder
b.WriteString("hello")
b.WriteByte(' ')
b.WriteString("world")
s := b.String() // "hello world"
```

<!-- Card End -->

<!-- Card Start -->
### Front
How do you use common `strings.Builder` methods and pre-size capacity?

### Back
Methods:
- `WriteString(string) (int, error)`
- `WriteByte(byte) error`
- `WriteRune(rune) (int, error)`
- `Write([]byte) (int, error)`
- `Grow(n int)` to preallocate capacity
- `Reset()` to reuse the buffer (invalidates prior String())

Example:
```go
parts := []string{"a", "b", "c"}
var b strings.Builder
b.Grow(2*len(parts)) // rough prealloc
for i, p := range parts {
	if i > 0 { b.WriteByte(',') }
	b.WriteString(p)
}
result := b.String() // "a,b,c"
```

<!-- Card End -->

<!-- Card Start -->
### Front
What are pitfalls and best practices when using `strings.Builder`?

### Back
Pitfalls:
- Don’t use the builder after taking `String()` if you plan to keep the string; `Reset()` invalidates previous contents
- `String()` returns a copy of the builder’s data; avoid calling it repeatedly in loops
- Not safe for concurrent use (wrap with sync or build per goroutine)

Best practices:
- Prefer over `bytes.Buffer` when you only need a string result
- Use `Grow()` when you can estimate size to reduce reallocations
- For heavy rune work, `WriteRune` is convenient and UTF-8 correct

```go
// Anti-pattern: repeated String() in loop
for _, p := range parts {
	b.WriteString(p)
	_ = b.String() // avoid; defer final String() to the end
}
```

<!-- Card End -->

<!-- Card Start -->
### Front
What does `strconv.Itoa` do in Go, and how is it used?

### Back
`strconv.Itoa` converts an `int` to its decimal string representation.

```go
import "strconv"

num := 123
s := strconv.Itoa(num) // "123"

// Concatenate with other strings
msg := "count=" + strconv.Itoa(7) // "count=7"
```

For the reverse (string → int), use `strconv.Atoi` or `strconv.ParseInt`.

<!-- Card End -->

<!-- Card Start -->
### Front
When should you use `strconv.Itoa` versus `fmt.Sprintf` or `strconv.FormatInt`?

### Back
Guidelines:
- Use `strconv.Itoa(i)` for simple `int` → string (fast, no formatting overhead)
- Use `strconv.FormatInt(n, base)` for specific bases or when working with `int64`
- Use `fmt.Sprintf("%d", i)` when you’re already formatting a larger string (but it’s slower than `Itoa` for pure conversion)

Examples:
```go
strconv.Itoa(42)               // "42"
strconv.FormatInt(42, 16)      // "2a" (hex)
fmt.Sprintf("user-%d", 42)     // "user-42" (convenient in templates)
```

Pitfalls:
- `Atoi`/`ParseInt` return errors; handle them for untrusted input
- `Itoa` uses the native int width; for cross-arch consistency prefer explicit sizes with `FormatInt`/`FormatUint`

<!-- Card End -->
