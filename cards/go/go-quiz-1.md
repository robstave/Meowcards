Here is a set of 30 multiple choice flashcards for studying Golang:

<!-- Card Start -->

### Front

What is the correct way to declare a variable in Go?

A) var x int = 5  
B) int x = 5  
C) x := 5  
D) Both A and C are correct

### Back

D) Both A and C are correct

Go allows variable declaration using either the `var` keyword or the short declaration operator `:=`.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is NOT a built-in data type in Go?

A) int  
B) float64  
C) char  
D) bool

### Back

C) char

Go does not have a `char` type. It uses `rune` for Unicode characters and `byte` for ASCII characters.

<!-- Card End -->
<!-- Card Start -->

### Front

What does the `defer` keyword do in Go?

A) Terminates the program  
B) Delays the execution of a function until the surrounding function returns  
C) Defines a new function  
D) Creates a loop

### Back

B) Delays the execution of a function until the surrounding function returns

`defer` is used to ensure that a function call is performed later in a program's execution, usually for cleanup purposes.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is used to handle errors in Go?

A) try-catch blocks  
B) if err != nil  
C) throw statement  
D) exception handling

### Back

B) if err != nil

Go uses explicit error checking with the `if err != nil` pattern instead of exceptions.

<!-- Card End -->
<!-- Card Start -->

### Front

What is a goroutine in Go?

A) A type of variable  
B) A lightweight thread managed by the Go runtime  
C) A built-in function  
D) A package for handling errors

### Back

B) A lightweight thread managed by the Go runtime

Goroutines are functions or methods that run concurrently with other functions or methods.

<!-- Card End --> 
<!-- Card Start -->

### Front

Which keyword is used to create a new struct type in Go?

A) struct  
B) type  
C) new  
D) create

### Back

B) type

The `type` keyword is used to define new types, including structs, in Go.

<!-- Card End --> 
<!-- Card Start -->

### Front

What is the purpose of the `make` function in Go?

A) To allocate memory for built-in types  
B) To create a new struct  
C) To define a new function  
D) To import packages

### Back

A) To allocate memory for built-in types

`make` is used to create slices, maps, and channels with initial capacity.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is true about Go's garbage collection?

A) It requires manual memory management  
B) It's automatic and runs concurrently  
C) It's not available in Go  
D) It only works for certain data types

### Back

B) It's automatic and runs concurrently

Go features automatic garbage collection that runs concurrently with the program.

<!-- Card End --> 
<!-- Card Start -->

### Front

What is the purpose of the `init()` function in Go?

A) To initialize variables  
B) To start the main program  
C) To be called before the main() function  
D) To import packages

### Back

C) To be called before the main() function

The `init()` function is automatically executed before the `main()` function in Go programs.

<!-- Card End --> 
<!-- Card Start -->

### Front

Which of the following is used for string formatting in Go?

A) printf()  
B) fmt.Printf()  
C) String.format()  
D) strconv.Format()

### Back

B) fmt.Printf()

`fmt.Printf()` is used for formatted I/O in Go, similar to C's printf.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the correct way to declare a slice in Go?

A) var s []int  
B) s := make([]int, 5)  
C) s := []int{1, 2, 3}  
D) All of the above

### Back

D) All of the above

Slices can be declared using var, make, or with a literal.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is true about interfaces in Go?

A) They must be explicitly implemented  
B) They are implicitly implemented  
C) They require a special keyword to implement  
D) They can only be used with structs

### Back

B) They are implicitly implemented

In Go, types implement interfaces implicitly by implementing the methods.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of the `range` keyword in Go?

A) To create a new range of numbers  
B) To iterate over elements in various data structures  
C) To define the scope of variables  
D) To specify a range of values in a switch statement

### Back

B) To iterate over elements in various data structures

`range` is used in for loops to iterate over slices, arrays, maps, strings, and channels.

<!-- Card End -->
<!-- Card Start -->

### Front

Which package is used for unit testing in Go?

A) unittest  
B) test  
C) testing  
D) assert

### Back

C) testing

The `testing` package provides support for automated testing of Go packages.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of the `go` keyword in Go?

A) To import packages  
B) To define functions  
C) To start a new goroutine  
D) To create a loop

### Back

C) To start a new goroutine

The `go` keyword is used to start a new goroutine, allowing for concurrent execution.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is used to handle concurrent access to shared resources in Go?

A) locks  
B) mutexes  
C) semaphores  
D) All of the above

### Back

D) All of the above

Go provides various synchronization primitives, including locks, mutexes, and semaphores, for handling concurrent access.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of the `select` statement in Go?

A) To choose from multiple send/receive channel operations  
B) To select items from a slice  
C) To choose between multiple if conditions  
D) To select a specific case in a switch statement

### Back

A) To choose from multiple send/receive channel operations

`select` allows a goroutine to wait on multiple communication operations.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is true about pointers in Go?

A) Go doesn't support pointers  
B) Pointers are automatically dereferenced  
C) The & operator is used to get the address of a variable  
D) Pointers are only used with structs

### Back

C) The & operator is used to get the address of a variable

In Go, & is used to get the address of a variable, and * is used to dereference a pointer.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of the `iota` identifier in Go?

A) To create infinite loops  
B) To generate a sequence of related constants  
C) To define interface methods  
D) To initialize variables

### Back

B) To generate a sequence of related constants

`iota` is used in constant declarations to create a sequence of related values.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is true about methods in Go?

A) They can only be defined for struct types  
B) They can be defined for any type  
C) They require a special keyword to define  
D) They are the same as functions

### Back

B) They can be defined for any type

In Go, methods can be defined for any named type, not just structs.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of the `recover` function in Go?

A) To recover deleted files  
B) To handle panics and prevent the program from crashing  
C) To restore previous versions of variables  
D) To recover lost network connections

### Back

B) To handle panics and prevent the program from crashing

`recover` is used to regain control of a panicking goroutine.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is used to create an empty interface in Go?

A) interface{}  
B) emptyInterface  
C) any  
D) void

### Back

A) interface{}

An empty interface is denoted by `interface{}` and can hold values of any type.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of the `fallthrough` keyword in Go switch statements?

A) To exit the switch statement  
B) To skip to the next case  
C) To execute the next case regardless of its condition  
D) To return to the previous case

### Back

C) To execute the next case regardless of its condition

`fallthrough` forces the execution to fall through to the next case.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is true about channels in Go?

A) They are used for file I/O  
B) They facilitate communication between goroutines  
C) They are a type of array  
D) They are used to implement interfaces

### Back

B) They facilitate communication between goroutines

Channels are the pipes that connect concurrent goroutines.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of the `go mod` command in Go?

A) To modify source code files  
B) To manage module dependencies  
C) To compile Go programs  
D) To run Go programs

### Back

B) To manage module dependencies

`go mod` is used for module maintenance, including dependency management.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is NOT a valid loop construct in Go?

A) for i := 0; i < 10; i++ {}  
B) for key, value := range map {}  
C) for condition {}  
D) while condition {}

### Back

D) while condition {}

Go does not have a `while` loop. All loops are expressed using the `for` keyword.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of the `_` (blank identifier) in Go?

A) To create anonymous functions  
B) To ignore values that you don't want to use  
C) To define private variables  
D) To indicate the end of a statement

### Back

B) To ignore values that you don't want to use

The blank identifier is used to discard unwanted values returned by functions or in multiple assignments.

<!-- Card End -->
<!-- Card Start -->

### Front

Which of the following is true about error handling in Go?

A) Errors are special exceptions  
B) Errors are values  
C) Errors are handled using try-catch blocks  
D) Errors are automatically propagated

### Back

B) Errors are values

In Go, errors are just values that can be returned, checked, and passed around like any other value.

<!-- Card End -->
<!-- Card Start -->

### Front

What is the purpose of the `init()` function in Go packages?

A) To initialize global variables  
B) To set up the package before it's used  
C) To run tests for the package  
D) Both A and B

### Back

D) Both A and B

The `init()` function is used to set up the package and can be used to initialize global variables before the main function is called.

<!-- Card End -->