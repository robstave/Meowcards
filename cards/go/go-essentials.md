
Note...these cards are not really front back all the time.  They are more like code snippet and explanation


<!-- Card Start -->

### Front


Initialize and print a slice and an array in Go.
```go
s := []int{1, 2, 3, 4, 5} 
fmt.Println(s)

a := [...]int{1, 2, 3, 4, 5} 
fmt.Println(a)
```

### Back

 
<!-- Card End -->
<!-- Card Start -->

### Front
 
Initialize a slice of strings and append a new string to it.

```go
s := []string{"apple", "banana", "cherry"}
s = append(s, "date")   
fmt.Println(s)
```

use Make to create a slice of integers with length 3 and capacity 5, then append two more integers. 
```go
s := make([]int, 3, 5)
s = append(s, 4, 5)
fmt.Println(s)
```

### Back

<!-- Card End -->
<!-- Card Start -->

### Front

If you use make to create a slice but do not append any elements, what will be the length and capacity of the slice?

```go
s := make([]int, 0)       // len=0, cap=0
s := make([]int, 5)       // len=5, cap=5
s := make([]int, 5, 10)   // len=5, cap=10
fmt.Println(len(s), cap(s))
```

note you can not do this
```go   
s := make([]int)       // Error: missing length and capacity
```

### Back
<!-- Card End -->
<!-- Card Start -->

### Front

the idiomatic way to check an error in Go is

```go
result, err := someFunction()
if err != nil {
    // handle the error
}       
// continue with result
```

another form is

```go
if err := someFunction(); err != nil {
    // handle the error
}
// continue with result
```

### Back

<!-- Card End -->
<!-- Card Start -->

### Front

there is no while in Go, but you can do this

```go
for x < 10 {
    // code to execute
}
```
### Back

<!-- Card End -->
<!-- Card Start -->

### Front

 
```go   
for i := 0; i < 10; i++ {
    // code to execute
}
```
is the same as
```go   
for range 10 {
    // code to execute
}
```

### Back

<!-- Card End -->
<!-- Card Start -->

### Front

How do you create a channel in Go?

```go
ch1 := make(chan string)
```

 
### Back

<!-- Card End -->

    


<!-- Card Start -->

### Front
 string.Builder is used to efficiently build strings in Go. It minimizes memory copying and allocations.

 ```go
 var b strings.Builder  
    b.WriteString("Hello, ")

    b.WriteString("World!")
    result := b.String()
    fmt.Println(result) // Output: Hello, World!

```

### Back

<!-- Card End -->


<!-- Card Start -->

### Front

strconv.Itoa converts an integer to a string.

```go       
num := 123
str := strconv.Itoa(num)
fmt.Println(str) // Output: "123"
```
### Back

<!-- Card End -->




<!-- Card Start -->

### Front
Runes

In Go, a rune is an alias for int32 and represents a Unicode code point. Runes are used to handle characters beyond the ASCII set.

```go
r := 'a' // rune literal
fmt.Println(r)        // Output: 97 (Unicode code point for 'a')

fmt.Printf("%c\n", r) // Output: a (character representation)
```
 
### Back

<!-- Card End -->

<!-- Card Start -->

### Front
 
### Back

<!-- Card End -->


<!-- Card Start -->

### Front
 
### Back

<!-- Card End -->
