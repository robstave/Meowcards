# Golang Interview Preparation Flashcards - Set E

<!-- Card Start -->

### Front

What is composition in Go, and how does it differ from inheritance?

- A. Composition is a way to embed structs
- B. Composition is a form of polymorphism
- C. Composition is the same as inheritance
- D. Composition allows code reuse without inheritance

### Back

**A and D are correct.  But D is more correct**

Composition in Go is a design principle where structs embed other structs to reuse their fields and methods. This is achieved through embedding (A). Unlike inheritance in object-oriented languages, composition does not create a hierarchy but instead promotes flexibility and modularity (D).

```go
package main

import "fmt"

type Address struct {
    City, State string
}

func (a Address) FullAddress() string {
    return a.City + ", " + a.State
}

type Person struct {
    Name    string
    Address // Embedded struct
}

func main() {
    p := Person{
        Name: "Alice",
        Address: Address{
            City: "Wonderland",
            State: "Dreamland",
        },
    }

    fmt.Println(p.Name)             // Access Person field
    fmt.Println(p.FullAddress())    // Reuse Address method
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

How does embedding a struct in Go enable composition?

- A. It creates a parent-child relationship
- B. It allows direct access to embedded fields and methods
- C. It enforces encapsulation
- D. It requires explicit method calls

### Back

**B. It allows direct access to embedded fields and methods**

Embedding a struct in Go enables composition by allowing the fields and methods of the embedded struct to be accessed directly, as if they were part of the embedding struct.

```go
package main

import "fmt"

type Logger struct {
    Enabled bool
}

type Service struct {
    Name   string
    Logger // Embedded struct
}

func main() {
    s := Service{
        Name: "MyService",
        Logger: Logger{
            Enabled: true,
        },
    }

    fmt.Println(s.Name)       // Access Service field
    fmt.Println(s.Enabled)    // Access embedded Logger field
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What happens if an embedded struct in Go has a method with the same name as the embedding struct?

- A. The embedded method is overridden
- B. The embedding struct's method takes precedence
- C. Both methods are accessible via explicit calls
- D. It causes a compilation error

### Back

**C. Both methods are accessible via explicit calls**

If an embedded struct has a method with the same name as the embedding struct, both methods remain accessible. You can call the embedding struct's method directly and the embedded struct's method using the embedded struct's name.

```go
package main

import "fmt"

type A struct {}
func (a A) Print() {
    fmt.Println("A's Print")
}

type B struct {
    A
}
func (b B) Print() {
    fmt.Println("B's Print")
}

func main() {
    b := B{}
    b.Print()   // Calls B's Print
    b.A.Print() // Calls A's Print
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

How can composition in Go be used to implement interfaces?

- A. By embedding structs that implement the interface
- B. By creating a hierarchy of structs
- C. By overriding methods in embedded structs
- D. By using inheritance

### Back

**A. By embedding structs that implement the interface**

Composition can be used to implement interfaces by embedding structs that already satisfy the interface. The embedding struct automatically satisfies the interface if the embedded struct provides the required methods.

```go
package main

import "fmt"

type Printer interface {
    Print()
}

type ConsolePrinter struct {}
func (cp ConsolePrinter) Print() {
    fmt.Println("Printing to console")
}

type Service struct {
    ConsolePrinter // Embedded struct
}

func main() {
    var p Printer = Service{}
    p.Print() // Calls ConsolePrinter's Print method
}
```

<!-- Card End -->

<!-- Card Start -->

### Front

What are the advantages of using composition over inheritance in Go?

- A. Composition is faster
- B. Composition enforces encapsulation
- C. Composition is more flexible and promotes code reuse
- D. Composition simplifies polymorphism

### Back

**C. Composition is more flexible and promotes code reuse**

Composition is preferred over inheritance in Go because it avoids the rigidity of hierarchical relationships and allows for more modular and reusable code. It also enables embedding multiple structs, providing greater flexibility.

```go
package main

import "fmt"

type Address struct {
    City, State string
}

type Contact struct {
    Phone string
}

type Person struct {
    Name    string
    Address // Embedded struct
    Contact // Embedded struct
}

func main() {
    p := Person{
        Name: "Alice",
        Address: Address{
            City: "Wonderland",
            State: "Dreamland",
        },
        Contact: Contact{
            Phone: "123-456-7890",
        },
    }

    fmt.Println(p.Name)       // Access Person field
    fmt.Println(p.City)       // Access embedded Address field
    fmt.Println(p.Phone)      // Access embedded Contact field
}
```

<!-- Card End -->
