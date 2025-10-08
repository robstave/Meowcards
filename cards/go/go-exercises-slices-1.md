


<!-- Card Start -->

### Front

What is the output of the following Go code?

```go
s := []int{1, 2, 3, 4, 5} 
s = append(s[:2], s[3:]...) 
fmt.Println(s)
```

### Back

The output will be:

`[1 2 4 5]`

This operation effectively removes the element at index 2 (the third element) from the slice.

note:

```go
    fmt.Println(s[:2])  // [1,2]
	fmt.Println(s[3:])  // [4,5]
	fmt.Println(s[:0])  // []
	fmt.Println(s[0:]) // [1,2,3,4,5]
```

the `...` spreads the slice so its like
```go
append(s[:2],4,5)
```
<!-- Card End -->

<!-- Card Start -->

### Front

How do you add an element to the end of a slice in Go?

### Back

To add an element to the end of a slice in Go, you use the `append` function:

```go
s := []int{1, 2, 3} 
s = append(s, 4)
```

After this operation, `s` will be `[1,2,3,4]`.

remember, its a slice.  An array in go is always fixed size.


<!-- Card End --> <!-- Card Start -->

### Front

What does the following Go code do?



```go
s := []int{1, 2, 3, 4, 5} 
s = s[1:]
```


### Back

This code removes the first element from the slice `s`.

After this operation, `s` will be `[2,3,4,5]`.

This is similar to the `shift()` operation in JavaScript.

<!-- Card End --> <!-- Card Start -->

### Front

How can you remove the last element from a slice in Go?

### Back

To remove the last element from a slice in Go, you can use slice notation:

```go
s := []int{1, 2, 3, 4, 5} 
s = s[:len(s)-1]
```


After this operation, `s` will be `[1,2,3,4]`.

This is similar to the `pop()` operation in JavaScript.

<!-- Card End --> <!-- Card Start -->

### Front

What is the output of the following Go code?

```go
s := []int{1, 2, 3, 4, 5} 
s = append([]int{0}, s...) 
fmt.Println(s)
```


### Back

The output will be:

text

`[0 1 2 3 4 5]`

This operation adds the element 0 to the beginning of the slice.  
It's similar to the `unshift()` operation in JavaScript.

<!-- Card End --> <!-- Card Start -->

### Front

How do you create a copy of a slice in Go?

### Back

To create a copy of a slice in Go, you can use the `copy` function or the append trick:

```go
original := []int{1, 2, 3} 
copy1 := make([]int, len(original)) 
copy(copy1, original) // or copy2 := append([]int(nil), original...)
```

Both `copy1` and `copy2` will be independent copies of `original`.

<!-- Card End --> 
<!-- Card Start -->


### Front

What does the following Go code do?

```go
s := []int{1, 2, 3, 4, 5} 
s = append(s[:2], append([]int{10}, s[2:]...)...)
```


### Back

This code inserts the value 10 at index 2 of the slice `s`.

After this operation, `s` will be `[1,2,10,3,4,5]`.

This is similar to using `splice()` in JavaScript to insert an element.

<!-- Card End --> <!-- Card Start -->

### Front

How do you reverse a slice in Go?

### Back

To reverse a slice in Go, you can use a for loop:

```go
s := []int{1, 2, 3, 4, 5} 
for i, j := 0, len(s)-1; i < j; i, j = i+1, j-1 {       
   s[i], s[j] = s[j], s[i] 
}
```



After this operation, `s` will be `[5,4,3,2,1]`.

<!-- Card End --> <!-- Card Start -->

### Front

What is the output of the following Go code?

go

```go
s := []int{1, 2, 3, 4, 5} 
fmt.Println(s[2:4])
```


### Back

The output will be:

text

`[3 4]`

This is a slice operation that returns a new slice containing elements from index 2 (**inclusive**) to index 4 (**exclusive**) of the original slice.

<!-- Card End --> <!-- Card Start -->

### Front

How do you clear all elements from a slice in Go?

### Back

To clear all elements from a slice in Go, you can simply reassign it to an empty slice:

```go
s := []int{1, 2, 3, 4, 5}
s = []int{}
```

Or, to reuse the existing array:

go

`s = s[:0]`

After either of these operations, `len(s)` will be 0.

<!-- Card End --> 


<!-- Card Start -->

### Front

What does the following Go code do?

```go
s := []int{1, 2, 3, 4, 5} 
s = append(s[:1], s[2:]...)
```
### Back

This code removes the second element (index 1) from the slice `s`.

After this operation, `s` will be `[1,3,4,5]`.

This is similar to using `splice(1, 1)` in JavaScript.

<!-- Card End --> 

<!-- Card Start -->

### Front

How do you check if a slice is empty in Go?

### Back

To check if a slice is empty in Go, you can compare its length to zero:

```go
s := []int{} 
if len(s) == 0 {     
  fmt.Println("Slice is empty") 
}


```

<!-- Card End --> <!-- Card Start -->

### Front

What is the output of the following Go code?

```go
s := []int{1, 2, 3, 4, 5} 
fmt.Println(s[:]) 
fmt.Println(s[1:]) 
fmt.Println(s[:3])
```

### Back

The output will be:

text

`[1 2 3 4 5] [2 3 4 5] [1 2 3]`

These are different slice operations:

- `s[:]` returns the entire slice
    
- `s[1:]` returns a slice from index 1 to the end
    
- `s[:3]` returns a slice from the start to index 3 (exclusive)
    

<!-- Card End --> 
<!-- Card Start -->

### Front

How do you concatenate two slices in Go?

### Back

To concatenate two slices in Go, you can use the `append` function:

```go
s1 := []int{1, 2, 3} 
s2 := []int{4, 5, 6} 
s3 := append(s1, s2...)

```


After this operation, `s3` will be `[1,2,3,4,5,6]`.

<!-- Card End --> 

<!-- Card Start -->

### Front

How do you create a slice with a specific length and capacity in Go?

### Back

To create a slice with a specific length and capacity in Go, you can use the `make` function:

go

`s := make([]int, 5, 10)`

This creates a slice of integers with a length of 5 and a capacity of 10.

<!-- Card End --> 

<!-- Card Start -->

### Front

What is the output of the following Go code?

```go
s := []int{1, 2, 3, 4, 5} 
fmt.Println(len(s), cap(s)) 
s = append(s, 6) 
fmt.Println(len(s), cap(s))

```

### Back

The output will be:

text

`5 5 6 10`

Initially, the length and capacity are both 5. After appending, the length becomes 6, and the capacity doubles to 10 (Go's growth strategy for slices).

<!-- Card End -->

<!-- Card Start -->

### Front

How do you remove duplicate elements from a slice in Go?

### Back

To remove duplicate elements from a slice in Go, you can use a map:

```go
func removeDuplicates(s []int) []int {     
  seen := make(map[int]bool)    
  result := []int{}    
  for _, v := range s {        
    if !seen[v] {            
      seen[v] = true            
      result = append(result, v)        
    }    
  }    
return result 
}

```

This function returns a new slice with duplicates removed.

<!-- Card End -->

 

<!-- Card Start -->

### Front

What does the following Go code do?

```go
s := []int{1, 2, 3, 4, 5} 
copy(s[2:], s[3:]) 
s = s[:len(s)-1]
```

### Back

This code removes the element at index 2 from the slice `s` while preserving the order of the remaining elements.

After these operations, `s` will be `[1,2,4,5]`.

This is an efficient way to remove an element from the middle of a slice.

```go
	s := []int{1, 2, 3, 4, 5, 6, 7, 8}
	fmt.Println(s[3:5])
	fmt.Println(s[5:8])

	copy(s[3:4], s[5:8])
	fmt.Println(s)


```

```go
[4 5]
[6 7 8]
[1 2 3 6 5 6 7 8]
```
 note that we are copying into 3:4....which is just going to be the 6
 if we did
 `copy(s[3:5], s[5:8])`
 you would have
 `[1 2 3 6 7 6 7 8]`
 

<!-- Card End --> 

<!-- Card Start -->

### Front

How do you find the index of an element in a slice in Go?

### Back

To find the index of an element in a slice in Go, you can use a for loop:

```go
func indexOf(s []int, val int) int {     
  for i, v := range s {        
    if v == val {            
      return i        
    }   
 }    

  return -1  // not found 

}
```


This function returns the index of the first occurrence of `val` in `s`, or -1 if not found.

<!-- Card End --> 

<!-- Card Start -->

### Front

What is the output of the following Go code?

```go
s := []int{1, 2, 3, 4, 5} 
s = append(s[:2], append([]int{10, 20}, s[2:]...)...) 
fmt.Println(s)
```

### Back

The output will be:

text

`[1 2 10 20 3 4 5]`

This operation inserts the elements 10 and 20 at index 2 of the slice.

<!-- Card End --> 
<!-- Card Start -->

### Front

How do you rotate a slice in Go?

### Back

To rotate a slice in Go, you can use this function:

```go
func rotate(s []int, k int) []int {     
   if len(s) == 0 {       
    return s    
   }    
   
   k = k % len(s)    
   return append(s[k:], s[:k]...)
}
```


For example, `rotate([]int{1, 2, 3, 4, 5}, 2)` would return `[3,4,5,1,2]`.

<!-- Card End --> <!-- Card Start -->

### Front

What does the following Go code do?

go

```go 
s := []int{1, 2, 3, 4, 5} 
s = s[:len(s):len(s)]
```

### Back

This code creates a new slice `s` with the same length as the original, but with its capacity set to its length.

This operation is useful when you want to prevent future append operations from modifying the underlying array of the original slice.

<!-- Card End --> <!-- Card Start -->

### Front

How do you check if a slice contains a specific element in Go?

### Back

To check if a slice contains a specific element in Go, you can use a for loop:

go

```go
func contains(s []int, e int) bool {     
  for _, v := range s {        
    if v == e {            
      return true        
    }    
  }    
  return false 
}
```

This function returns true if the slice `s` contains the element `e`, and false otherwise.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the output of the following Go code?

```go
s := []int{1, 2, 3, 4, 5} 
fmt.Println(s[:3:3])
```

`

### Back

The output will be:

text

`[1 2 3]`

This slice operation creates a new slice with length 3 and capacity 3, containing the first three elements of `s`.

<!-- Card End --> 

 
<!-- Card Start -->

### Front

How do you implement a stack using a slice in Go?

### Back

You can implement a stack using a slice in Go like this:

```go
type Stack []int 

func (s *Stack) Push(v int) {     
  *s = append(*s, v) 
} 
  
func (s *Stack) Pop() int {     
  if len(*s) == 0 {        
    return 0 // or error    
  }

  v := (*s)[len(*s)-1]    
  *s = (*s)[:len(*s)-1]    
  return v 
}
```


This implements Push and Pop operations for a stack of integers.

```go

package main

import (
	"fmt"
)

type Stack []int

func (s *Stack) Push(v int) {
	*s = append(*s, v)
}

func (s *Stack) Pop() int {
	if len(*s) == 0 {
		return 0 // or error
	}

	v := (*s)[len(*s)-1]
	*s = (*s)[:len(*s)-1]
	return v
}

func main() {

	myStack := Stack{1, 2, 3}

	fmt.Println(myStack)

	myStack.Push(3)

	fmt.Println(myStack)

	myStack.Pop()
	myStack.Pop()

	fmt.Println(myStack)

}


```

<!-- Card End --> 


<!-- Card Start -->

### Front

What does the following Go code do?

```go
s := []int{1, 2, 3, 4, 5} 
s = append(s[:2], append(make([]int, 3), s[2:]...)...)
```

`

### Back

This code inserts three zero elements at index 2 of the slice `s`.

After this operation, `s` will be `[1 2 0 0 0 3 4 5]`.

This is a way to insert multiple elements at a specific index in a slice.

```go
s := []int{1, 2, 3, 4, 5} 

append(make([]int, 3), s[2:]...)   // [0 0 0 3 4 5]
//so
s = append(s[:2], append(make([]int, 3), s[2:]...)...)
// `[1 2 0 0 0 3 4 5]`

```



<!-- Card End --> 


<!-- Card Start -->

### Front

How do you implement a queue using slices in Go?

### Back

You can implement a queue using slices in Go like this:

```go
type Queue []int 

func (q *Queue) Enqueue(v int) {     
 *q = append(*q, v) }
 
func (q *Queue) Dequeue() int {     
   if len(*q) == 0 {        return 0 // or error    }   
    v := (*q)[0]    *q = (*q)[1:]    return v 
    }
```


This implements Enqueue and Dequeue operations for a queue of integers.

```go
package main

import (
	"fmt"
)

type Queue []int

func (q *Queue) Enqueue(v int) {
	*q = append(*q, v)
}

func (q *Queue) Dequeue() int {
	if len(*q) == 0 {
		return 0 // or error
	}
	v := (*q)[0]
	*q = (*q)[1:]
	return v
}

func main() {

	q := Queue{1, 2}

	fmt.Println(q) // [1,2]
	q.Enqueue(3)
	fmt.Println(q) // [1,2,3]
	q.Dequeue()
	fmt.Println(q) //[2,3]

}
```

<!-- Card End --> 

<!-- Card Start -->

### Front

What is the output of the following Go code?

```go
s := []int{1, 2, 3, 4, 5} 
fmt.Println(append(s[:2], s[1:]...))
```

### Back

The output will be:

text

`[1 2 2 3 4 5]`

This operation creates a new slice that duplicates the element at index 1.

<!-- Card End --> 

<!-- Card Start -->

### Front

How do you sort a slice of integers in ascending order in Go?

### Back

To sort a slice of integers in ascending order in Go, you can use the `sort` package:

```go

import "sort" 
s := []int{5, 2, 6, 3, 1, 4} 
sort.Ints(s)

```

After this operation, `s` will be `[1,2,3,4,5,6]`.

<!-- Card End --> 
<!-- Card Start -->

### Front

What does the following Go code do?

```go
s := []int{1, 2, 3, 4, 5} 
copy(s[2:], s[1:]) 
s[1] = 0
```


### Back

This code shifts all elements from index 1 one position

```go

package main

import (
	"fmt"
)

func main() {

	s := []int{1, 2, 3, 4, 5}
	copy(s[2:], s[1:])
	s[1] = 0

	fmt.Println(s) // [ 1, 0, 2, 3, 4]

}
```



<!-- Card Start -->

### Front

What does the following Go code do?

```go
s := []int{1, 2, 3, 4, 5} 
fmt.Println(s[2:]) 
fmt.Println(s[1:]) 
fmt.Println(s[0:]) 
fmt.Println(s[:]) 
fmt.Println(s[:0]) 
fmt.Println(s[3:3]) 
 
```


### Back

 

```go
package main

import (
	"fmt"
)

func main() {

	s := []int{1, 2, 3, 4, 5}
	fmt.Println(s[2:])  //[3 4 5]
	fmt.Println(s[1:])  //[2 3 4 5]
	fmt.Println(s[0:])  //[1 2 3 4 5]
	fmt.Println(s[:])   //[1 2 3 4 5]
	fmt.Println(s[:0])  //[]
	fmt.Println(s[3:3]) //[]
	fmt.Println(s[3:4]) //[4]
	fmt.Println(s[3:5]) //[4 5]

}

 

 
```





#### Citations:

1. [https://www.perplexity.ai/search/write-an-article-that-shows-ho-.GeZOjw9SUOjwQ5dYw724A](https://www.perplexity.ai/search/write-an-article-that-shows-ho-.GeZOjw9SUOjwQ5dYw724A)
2. [https://www.fullstackfoundations.com/blog/javascript-array-methods](https://www.fullstackfoundations.com/blog/javascript-array-methods)
3. [https://community.zapier.com/featured-articles-65/add-remove-items-in-an-array-with-push-pop-shift-unshift-14074](https://community.zapier.com/featured-articles-65/add-remove-items-in-an-array-with-push-pop-shift-unshift-14074)
4. [https://dev.to/swarnaliroy94/remove-items-from-arrays-with-shift-pop-methods-5caf](https://dev.to/swarnaliroy94/remove-items-from-arrays-with-shift-pop-methods-5caf)
5. [https://codingnomads.com/javascript-array-unshift-shift-pop-push](https://codingnomads.com/javascript-array-unshift-shift-pop-push)
6. [https://go.dev/wiki/SliceTricks](https://go.dev/wiki/SliceTricks)
7. [https://stackoverflow.com/questions/8073673/how-can-i-add-new-array-elements-at-the-beginning-of-an-array-in-javascript](https://stackoverflow.com/questions/8073673/how-can-i-add-new-array-elements-at-the-beginning-of-an-array-in-javascript)
8. [https://www.youtube.com/watch?v=o724TbnN4Mk](https://www.youtube.com/watch?v=o724TbnN4Mk)
9. [https://stackoverflow.com/questions/33834742/remove-and-adding-elements-to-array-in-go-lang](https://stackoverflow.com/questions/33834742/remove-and-adding-elements-to-array-in-go-lang)
10. [https://forum.freecodecamp.org/t/push-pop-unshift-shift-info-graphic/480531](https://forum.freecodecamp.org/t/push-pop-unshift-shift-info-graphic/480531)
11. [https://www.youtube.com/watch?v=9YsbNPyFtsI](https://www.youtube.com/watch?v=9YsbNPyFtsI)
12. [https://stackoverflow.com/questions/65958894/is-it-possible-to-connect-methods-like-sort-shift-pop-push-and-unshift](https://stackoverflow.com/questions/65958894/is-it-possible-to-connect-methods-like-sort-shift-pop-push-and-unshift)
13. [https://stackoverflow.com/questions/22614237/javascript-runtime-complexity-of-array-functions](https://stackoverflow.com/questions/22614237/javascript-runtime-complexity-of-array-functions)
14. [https://www.w3schools.com/js/js_array_methods.asp](https://www.w3schools.com/js/js_array_methods.asp)
15. [https://go.dev/play/p/wNgO9LeX514](https://go.dev/play/p/wNgO9LeX514)
16. [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
17. [https://javascript.info/array-methods](https://javascript.info/array-methods)
18. [https://daily.dev/blog/pop-and-push-in-javascript-array-essentials](https://daily.dev/blog/pop-and-push-in-javascript-array-essentials)
19. [https://www.youtube.com/watch?v=sdHmOOnZVw4](https://www.youtube.com/watch?v=sdHmOOnZVw4)
20. [https://stackoverflow.com/questions/34623795/is-there-a-way-to-method-chain-push-and-shift-array-methods](https://stackoverflow.com/questions/34623795/is-there-a-way-to-method-chain-push-and-shift-array-methods)