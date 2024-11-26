# Unit 1

## **1. History of Go**

Go, also known as Golang, was created at Google by Robert Griesemer, Rob Pike, and Ken Thompson. The language was first announced in 2009. The motivation behind Go was to address issues that the creators saw in other languages used at Google, such as C++ and Java, including slow build times, dependency management, and the complexity of codebases.

**Key Historical Milestones:**
- **2007:** Development of Go started.
- **2009:** Go was publicly announced.
- **2012:** Go 1.0 was released, establishing a stable language specification and API.
- **2020:** Go 1.15 was released, including numerous performance improvements and features.
- **Ongoing:** Continuous updates and improvements, with Go 2 in development focusing on generics and error handling improvements.

---

## **2. Datatypes in Go**

Go is a statically typed language, and it supports several basic and composite datatypes.

### **Basic Datatypes:**
- **Boolean:** `bool`
  ```go
  var isActive bool = true
  ```

- **Numeric:**
  - **Integer:** `int`, `int8`, `int16`, `int32`, `int64`
  ```go
  var age int = 30
  ```
  - **Unsigned Integer:** `uint`, `uint8`, `uint16`, `uint32`, `uint64`
  ```go
  var distance uint = 100
  ```
  - **Floating-point:** `float32`, `float64`
  ```go
  var height float64 = 5.9
  ```
  - **Complex numbers:** `complex64`, `complex128`
  ```go
  var c complex128 = complex(5, 7)
  ```

- **String:** `string`
  ```go
  var name string = "John Doe"
  ```

### **Composite Datatypes:**
- **Array:** Fixed-size collections of elements.
  ```go
  var arr [3]int = [3]int{1, 2, 3}
  ```

- **Slice:** Dynamic-size, flexible view into arrays.
  ```go
  var slice []int = []int{1, 2, 3}
  ```

- **Struct:** Collection of fields.
  ```go
  type Person struct {
      Name string
      Age  int
  }
  var p = Person{Name: "Alice", Age: 30}
  ```

- **Map:** Collection of key-value pairs.
  ```go
  var m = map[string]int{"Alice": 25, "Bob": 30}
  ```

- **Channel:** Concurrency primitive for communication between goroutines.
  ```go
  var ch = make(chan int)
  ```

---

## **3. Garbage Collection in Go**

Go features an automatic garbage collection mechanism that helps manage memory automatically, freeing up memory that is no longer in use. Go uses a concurrent garbage collector, meaning it runs concurrently with the application, minimizing stop-the-world pauses and improving performance.

**Key Features:**
- **Mark-and-Sweep Algorithm:** The garbage collector marks live objects and then sweeps away the unmarked objects.
- **Concurrent GC:** The garbage collector works alongside the running program, reducing latency.
- **Generational Approach:** Newer objects are collected more frequently than older ones.

**Example demonstrating garbage collection:**
```go
package main

import (
    "fmt"
    "runtime"
)

func main() {
    var m runtime.MemStats
    runtime.ReadMemStats(&m)
    fmt.Printf("HeapAlloc before: %v KB\n", m.HeapAlloc/1024)

    makeGarbage()

    runtime.ReadMemStats(&m)
    fmt.Printf("HeapAlloc after: %v KB\n", m.HeapAlloc/1024)
}

func makeGarbage() {
    for i := 0; i < 1000000; i++ {
        _ = make([]byte, 1024)
    }
}
```

**Output:**
```
HeapAlloc before: 392 KB
HeapAlloc after: 2096 KB
```

---

## **4. Concurrency in Go**

Go's concurrency model is based on goroutines and channels, inspired by CSP (Communicating Sequential Processes).

### **Goroutines:**
- Lightweight threads managed by the Go runtime.
- Created using the `go` keyword.
- Example:
  ```go
  package main

  import (
      "fmt"
      "time"
  )

  func say(s string) {
      for i := 0; i < 5; i++ {
          time.Sleep(100 * time.Millisecond)
          fmt.Println(s)
      }
  }

  func main() {
      go say("world")
      say("hello")
  }
  ```

  **Output:**
  ```
  hello
  world
  hello
  world
  hello
  world
  hello
  world
  hello
  ```

### **Channels:**
- Used for communication between goroutines.
- Example:
  ```go
  package main

  import "fmt"

  func sum(s []int, c chan int) {
      sum := 0
      for _, v := range s {
          sum += v
      }
      c <- sum // Send sum to channel
  }

  func main() {
      s := []int{7, 2, 8, -9, 4, 0}
      c := make(chan int)

      go sum(s[:len(s)/2], c)
      go sum(s[len(s)/2:], c)

      x, y := <-c, <-c // Receive from channel

      fmt.Println(x, y, x+y)
  }
  ```

  **Output:**
  ```
  -5 17 12
  ```

---

## **5. Difference between Go & C++, JAVA**

### **Go vs C++**
- **Memory Management:**
  - Go: Automatic garbage collection.
  - C++: Manual memory management using `new`, `delete`, and smart pointers.
- **Concurrency:**
  - Go: Built-in concurrency with goroutines and channels.
  - C++: Uses threads and libraries like Boost, std::thread.
- **Syntax and Complexity:**
  - Go: Simple and concise syntax, fewer features.
  - C++: Complex syntax with extensive features (templates, multiple inheritance).
- **Compilation:**
  - Go: Fast compilation times.
  - C++: Slower compilation due to template instantiation and other features.
- **Standard Library:**
  - Go: Rich standard library with built-in support for concurrency, web servers, etc.
  - C++: Standard library with extensive third-party libraries.

### **Go vs Java**
- **Memory Management:**
  - Go: Automatic garbage collection.
  - Java: Automatic garbage collection.
- **Concurrency:**
  - Go: Goroutines and channels for concurrency.
  - Java: Threads, `ExecutorService`, and other concurrency utilities.
- **Syntax and Complexity:**
  - Go: Simple, concise syntax without generics (planned for Go 2).
  - Java: Verbose syntax with extensive features like generics, annotations, and reflection.
- **Compilation:**
  - Go: Compiled to native code, fast compilation.
  - Java: Compiled to bytecode, runs on the JVM.
- **Performance:**
  - Go: Often faster due to direct compilation to machine code.
  - Java: JIT compilation can lead to high performance but has an initial warm-up time.

# Unit 2

## **1. Variables and Constants**

### **Variables**  
In Go, variables are declared using the `var` keyword or the shorthand `:=` operator (for local variables). Go is statically typed, meaning variables have a fixed type after declaration.  

#### **Syntax for Variable Declaration**  
```go
var variableName dataType
```
- **Explicit declaration**:  
  ```go
  var x int = 10
  ```
- **Implicit declaration (type inferred)**:  
  ```go
  y := 20 // `y` is inferred as an int
  ```

#### **Example:**
```go
package main

import "fmt"

func main() {
    var a int = 10
    b := "Hello, Go!" // Shorthand declaration
    var c, d float64 = 5.5, 7.2 // Multiple variables

    fmt.Println("Integer:", a)
    fmt.Println("String:", b)
    fmt.Println("Floats:", c, d)
}
```

**Output:**
```
Integer: 10
String: Hello, Go!
Floats: 5.5 7.2
```

---

### **Constants**  
Constants are immutable values that are declared using the `const` keyword. They are evaluated at compile time.  

#### **Syntax for Constant Declaration**  
```go
const constantName = value
```

#### **Example:**
```go
package main

import "fmt"

func main() {
    const Pi = 3.14
    const Greeting = "Welcome to Go!"

    fmt.Println("Value of Pi:", Pi)
    fmt.Println("Message:", Greeting)
}
```

**Output:**
```
Value of Pi: 3.14
Message: Welcome to Go!
```

---

## **2. Conditional Statements and Loop Statements**

### **Conditional Statements**  
Go supports standard conditional statements like `if`, `if-else`, and `switch`.

#### **If-Else Statement**  
```go
package main

import "fmt"

func main() {
    num := 10

    if num%2 == 0 {
        fmt.Println("Even number")
    } else {
        fmt.Println("Odd number")
    }
}
```

**Output:**
```
Even number
```

#### **Switch Statement**  
Go’s `switch` statement is more flexible than other languages as it doesn’t require a `break` after each case.  
```go
package main

import "fmt"

func main() {
    day := 3

    switch day {
    case 1:
        fmt.Println("Monday")
    case 2:
        fmt.Println("Tuesday")
    case 3:
        fmt.Println("Wednesday")
    default:
        fmt.Println("Invalid day")
    }
}
```

**Output:**
```
Wednesday
```

---

### **Loop Statements**  
Go only has a `for` loop, which can mimic `while` and infinite loops.  

#### **For Loop Syntax:**
```go
for initialization; condition; increment {
    // Code block
}
```

#### **Example:**
```go
package main

import "fmt"

func main() {
    for i := 1; i <= 5; i++ {
        fmt.Println("Value of i:", i)
    }
}
```

**Output:**
```
Value of i: 1
Value of i: 2
Value of i: 3
Value of i: 4
Value of i: 5
```

#### **While Loop Equivalent:**
```go
package main

import "fmt"

func main() {
    num := 5
    for num > 0 {
        fmt.Println("Countdown:", num)
        num--
    }
}
```

**Output:**
```
Countdown: 5
Countdown: 4
Countdown: 3
Countdown: 2
Countdown: 1
```

#### **Infinite Loop:**
```go
package main

import "fmt"

func main() {
    count := 0
    for {
        fmt.Println("Infinite Loop:", count)
        count++
        if count == 3 {
            break // Exit condition
        }
    }
}
```

**Output:**
```
Infinite Loop: 0
Infinite Loop: 1
Infinite Loop: 2
```

---

## **3. 1D and 2D Array Declaration and Differences**

### **1D Arrays**  
- Arrays in Go are fixed in size and declared with a specific type.  
- Syntax:  
  ```go
  var arrayName [size]dataType
  ```

#### **Example:**
```go
package main

import "fmt"

func main() {
    var arr [5]int // Declare an integer array of size 5
    arr[0] = 10
    arr[1] = 20
    arr[2] = 30

    fmt.Println("1D Array:", arr)
}
```

**Output:**
```
1D Array: [10 20 30 0 0]
```

---

### **2D Arrays**  
- A 2D array is an array of arrays.  
- Syntax:  
  ```go
  var arrayName [rows][columns]dataType
  ```

#### **Example:**
```go
package main

import "fmt"

func main() {
    var matrix [2][3]int // Declare a 2D array with 2 rows and 3 columns
    matrix[0][0] = 1
    matrix[0][1] = 2
    matrix[0][2] = 3
    matrix[1][0] = 4
    matrix[1][1] = 5
    matrix[1][2] = 6

    fmt.Println("2D Array:")
    for _, row := range matrix {
        fmt.Println(row)
    }
}
```

**Output:**
```
2D Array:
[1 2 3]
[4 5 6]
```

---

### **Differences Between 1D and 2D Arrays**

| **Aspect**         | **1D Array**                          | **2D Array**                          |
|---------------------|----------------------------------------|----------------------------------------|
| **Definition**      | Single list of elements.              | Array of arrays (matrix-like).         |
| **Memory Layout**   | Linear memory layout.                 | Row-major order (rows stored linearly).|
| **Declaration**     | `var arr [size]dataType`              | `var matrix [rows][columns]dataType`   |
| **Example**         | `[10, 20, 30]`                        | `[[1, 2, 3], [4, 5, 6]]`              |

---

## **4. Syntax for Control Structures**

### **If-Else Syntax**
```go
if condition {
    // Code block
} else if anotherCondition {
    // Code block
} else {
    // Code block
}
```

### **Switch Syntax**
```go
switch variable {
case value1:
    // Code block
case value2:
    // Code block
default:
    // Code block
}
```

### **For Loop Syntax**
```go
for initialization; condition; increment {
    // Code block
}
```

### **Range Loop (for iterating over arrays, slices, maps):**
```go
for index, value := range array {
    // Code block
}
```

# Unit 3

## **Functions and Types of Functions in Go**

A **function** in Go is a block of code designed to perform a specific task. Functions are central to Go’s modularity and code reuse. They are defined using the `func` keyword.

### **Types of Functions in Go**

1. **Basic Functions**:
   - A standard function takes input arguments, performs operations, and optionally returns a value.
   - Syntax:
     ```go
     func functionName(parameters) returnType {
         // Function body
     }
     ```
   - Example:
     ```go
     func add(a int, b int) int {
         return a + b
     }
     fmt.Println(add(2, 3)) // Output: 5
     ```

2. **Variadic Functions**:
   - Accept a variable number of arguments.
   - Use the ellipsis (`...`) in the parameter list.
   - Example:
     ```go
     func sum(numbers ...int) int {
         total := 0
         for _, num := range numbers {
             total += num
         }
         return total
     }
     fmt.Println(sum(1, 2, 3, 4)) // Output: 10
     ```

3. **Anonymous Functions**:
   - Functions without a name, typically used for short tasks or as a parameter to another function.
   - Example:
     ```go
     func main() {
         result := func(a, b int) int { return a + b }(3, 4)
         fmt.Println(result) // Output: 7
     }
     ```

4. **Higher-Order Functions**:
   - Functions that take other functions as arguments or return functions.
   - Example:
     ```go
     func operate(a int, b int, op func(int, int) int) int {
         return op(a, b)
     }
     func add(a, b int) int { return a + b }
     fmt.Println(operate(2, 3, add)) // Output: 5
     ```

5. **Named Return Values**:
   - You can predefine the names of the return variables in the function signature, and use a simple `return` statement.
   - Example:
     ```go
     func divide(a, b int) (result int, err error) {
         if b == 0 {
             err = fmt.Errorf("division by zero")
             return
         }
         result = a / b
         return
     }
     ```

6. **Method Functions**:
   - Functions associated with a specific type (often structs).
   - Example:
     ```go
     type Circle struct {
         Radius float64
     }
     func (c Circle) Area() float64 {
         return 3.14 * c.Radius * c.Radius
     }
     circle := Circle{Radius: 5}
     fmt.Println(circle.Area()) // Output: 78.5
     ```

---

## **Defer, Panic, and Recover Statements**

### **Defer**
- **Definition**: The `defer` keyword postpones the execution of a function or statement until the surrounding function exits.
- **Use Cases**:
  - Cleaning up resources (e.g., closing files, unlocking mutexes).
  - Ensuring certain actions are executed even in case of errors or panics.
- **Behavior**:
  - Deferred calls are executed in **LIFO (Last-In, First-Out)** order.
  - Example:
    ```go
    func main() {
        defer fmt.Println("World")
        fmt.Println("Hello")
    }
    // Output:
    // Hello
    // World
    ```

### **Panic**
- **Definition**: The `panic` statement is used to stop the ordinary flow of execution. It’s typically used to signal critical errors from which the program cannot recover.
- **Use Cases**:
  - Out-of-bound errors.
  - Unrecoverable situations like corrupted program state.
- **Behavior**:
  - Panicking unwinds the stack, executing deferred calls in the process.
  - Example:
    ```go
    func main() {
        defer fmt.Println("This will print before panic exits")
        panic("A severe error occurred")
    }
    ```

### **Recover**
- **Definition**: The `recover` function is used to regain control of a panicking goroutine. It prevents the program from crashing.
- **Use Cases**:
  - Gracefully handling panics.
  - Logging the error and continuing program execution.
- **Behavior**:
  - `recover` works only within deferred functions.
  - Example:
    ```go
    func main() {
        defer func() {
            if r := recover(); r != nil {
                fmt.Println("Recovered from:", r)
            }
        }()
        panic("Something went wrong")
    }
    // Output:
    // Recovered from: Something went wrong
    ```

---

## **Structs and Interfaces**

### **Structs in Go**
- **Definition**: A `struct` is a composite data type that groups together variables (fields) under a single type.
- **Syntax**:
  ```go
  type StructName struct {
      fieldName fieldType
  }
  ```
- **Features**:
  - Fields in a struct can have different types.
  - Structs allow embedding for pseudo-inheritance.

- **Example**:
  ```go
  type Person struct {
      Name string
      Age  int
  }
  func main() {
      p := Person{Name: "Alice", Age: 30}
      fmt.Println(p.Name, p.Age) // Output: Alice 30
  }
  ```

- **Struct with Methods**:
  ```go
  func (p Person) Greet() string {
      return "Hello, " + p.Name
  }
  fmt.Println(p.Greet()) // Output: Hello, Alice
  ```

---

### **Interfaces in Go**
- **Definition**: An `interface` defines a set of method signatures that a type must implement. It allows polymorphism by decoupling behavior from the underlying implementation.
- **Syntax**:
  ```go
  type InterfaceName interface {
      MethodName(params) returnType
  }
  ```
- **Features**:
  - No explicit declaration is needed to implement an interface; if a type implements all the methods in an interface, it implicitly satisfies the interface.
  - Interfaces can be empty (`interface{}`), acting as a placeholder for any type.

- **Example**:
  ```go
  type Shape interface {
      Area() float64
  }
  type Circle struct {
      Radius float64
  }
  func (c Circle) Area() float64 {
      return 3.14 * c.Radius * c.Radius
  }
  func PrintArea(s Shape) {
      fmt.Println("Area:", s.Area())
  }
  func main() {
      c := Circle{Radius: 5}
      PrintArea(c) // Output: Area: 78.5
  }
  ```

- **Empty Interface**:
  - Can store any value.
  - Example:
    ```go
    func PrintValue(i interface{}) {
        fmt.Println(i)
    }
    PrintValue(42)           // Output: 42
    PrintValue("Hello, Go!") // Output: Hello, Go!
    ```

- **Type Assertion**:
  - Extracts the underlying value from an interface variable.
  - Syntax: `value, ok := interfaceVariable.(ConcreteType)`
  - Example:
    ```go
    var i interface{} = "Hello"
    str, ok := i.(string)
    if ok {
        fmt.Println("String value:", str)
    }
    ```

---

### **Structs vs Interfaces**
| Feature            | Struct                          | Interface                    |
|--------------------|---------------------------------|-----------------------------|
| **Definition**     | Groups fields into a single type. | Defines behavior via methods. |
| **Use Case**       | For defining data models.        | For achieving polymorphism. |
| **Inheritance**    | Embedding for pseudo-inheritance. | Implicit implementation.    |


# Unit 4

## **Packages Used in Go**  

A **package** in Go is a collection of related source files that provide reusable functionality. Go’s standard library includes many built-in packages, but developers can also create custom packages.  

### **Key Packages in Go**  
1. **`fmt`**  
   - Provides formatted I/O operations.  
   - Example:  
     ```go
     import "fmt"

     func main() {
         fmt.Println("Hello, Go!")
     }
     ```

2. **`os`**  
   - Facilitates interaction with the operating system, including file and directory operations.  
   - Example:  
     ```go
     import "os"

     func main() {
         file, err := os.Create("example.txt")
         if err != nil {
             panic(err)
         }
         defer file.Close()
         file.WriteString("Hello, file!")
     }
     ```

3. **`http` (from `net/http`)**  
   - Provides support for building HTTP servers and clients.  
   - Example (HTTP server):  
     ```go
     import (
         "fmt"
         "net/http"
     )

     func handler(w http.ResponseWriter, r *http.Request) {
         fmt.Fprintln(w, "Welcome to Go HTTP Server")
     }

     func main() {
         http.HandleFunc("/", handler)
         http.ListenAndServe(":8080", nil)
     }
     ```

4. **`io` and `io/ioutil`**  
   - Handle I/O operations for reading and writing files, streams, etc.  
   - Example:  
     ```go
     import (
         "io/ioutil"
         "log"
     )

     func main() {
         data, err := ioutil.ReadFile("example.txt")
         if err != nil {
             log.Fatal(err)
         }
         log.Println(string(data))
     }
     ```

5. **`time`**  
   - Manages and formats time values.  
   - Example:  
     ```go
     import "time"

     func main() {
         fmt.Println("Current time:", time.Now())
     }
     ```

6. **`encoding/json`**  
   - Provides functions for working with JSON data.  
   - Example:  
     ```go
     import (
         "encoding/json"
         "fmt"
     )

     type User struct {
         Name string `json:"name"`
         Age  int    `json:"age"`
     }

     func main() {
         jsonData := `{"name": "Alice", "age": 30}`
         var user User
         json.Unmarshal([]byte(jsonData), &user)
         fmt.Println(user.Name, user.Age)
     }
     ```

---

## **Asynchronous HTTP Requests and Examples**  

Go’s `net/http` package supports asynchronous (non-blocking) HTTP requests using **goroutines** and **channels**.  

### **Making Asynchronous HTTP Requests**  
1. **GET Request** (Asynchronous):  
   - Use goroutines to execute HTTP requests concurrently.  
   - Example:  
     ```go
     import (
         "fmt"
         "net/http"
         "sync"
     )

     func fetchURL(wg *sync.WaitGroup, url string) {
         defer wg.Done()
         resp, err := http.Get(url)
         if err != nil {
             fmt.Println("Error fetching:", url, err)
             return
         }
         defer resp.Body.Close()
         fmt.Println("Fetched:", url, "Status Code:", resp.StatusCode)
     }

     func main() {
         var wg sync.WaitGroup
         urls := []string{
             "https://www.google.com",
             "https://www.github.com",
             "https://www.stackoverflow.com",
         }

         for _, url := range urls {
             wg.Add(1)
             go fetchURL(&wg, url)
         }
         wg.Wait()
     }
     ```

2. **POST Request** (Asynchronous):  
   - Example:  
     ```go
     import (
         "bytes"
         "fmt"
         "net/http"
         "sync"
     )

     func postRequest(wg *sync.WaitGroup, url string, data []byte) {
         defer wg.Done()
         resp, err := http.Post(url, "application/json", bytes.NewBuffer(data))
         if err != nil {
             fmt.Println("Error posting:", url, err)
             return
         }
         defer resp.Body.Close()
         fmt.Println("Posted to:", url, "Status Code:", resp.StatusCode)
     }

     func main() {
         var wg sync.WaitGroup
         url := "https://jsonplaceholder.typicode.com/posts"
         jsonData := []byte(`{"title":"foo","body":"bar","userId":1}`)

         wg.Add(1)
         go postRequest(&wg, url, jsonData)
         wg.Wait()
     }
     ```

---

## **Setting Up a Server Using Go**  

Go’s `net/http` package simplifies server creation.  

### **Basic HTTP Server**  
- A simple HTTP server responds to requests at specific endpoints.  
- Example:  
  ```go
  import (
      "fmt"
      "net/http"
  )

  func homeHandler(w http.ResponseWriter, r *http.Request) {
      fmt.Fprintln(w, "Welcome to the Home Page")
  }

  func aboutHandler(w http.ResponseWriter, r *http.Request) {
      fmt.Fprintln(w, "This is the About Page")
  }

  func main() {
      http.HandleFunc("/", homeHandler)
      http.HandleFunc("/about", aboutHandler)
      fmt.Println("Server is running at http://localhost:8080")
      http.ListenAndServe(":8080", nil)
  }
  ```

### **Advanced Features**  
1. **Serving Static Files**:  
   - Example:  
     ```go
     import "net/http"

     func main() {
         http.Handle("/static/", http.StripPrefix("/static/", http.FileServer(http.Dir("static"))))
         http.ListenAndServe(":8080", nil)
     }
     ```

2. **Middleware**:  
   - Adding layers of functionality like logging or authentication.  
   - Example:  
     ```go
     func loggingMiddleware(next http.Handler) http.Handler {
         return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
             fmt.Println("Request received:", r.URL.Path)
             next.ServeHTTP(w, r)
         })
     }

     func main() {
         mux := http.NewServeMux()
         mux.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
             fmt.Fprintln(w, "Hello, Go!")
         })

         http.ListenAndServe(":8080", loggingMiddleware(mux))
     }
     ```

---

## **CRUD Examples**  

CRUD operations (**Create, Read, Update, Delete**) are fundamental to any application that interacts with a database or data storage. Here’s how to implement them using Go’s `net/http` package and in-memory data structures.  

### **Example: Simple CRUD with an In-Memory Data Store**  
```go
package main

import (
    "encoding/json"
    "fmt"
    "net/http"
    "strconv"
    "sync"
)

type Item struct {
    ID    int    `json:"id"`
    Name  string `json:"name"`
    Price float64 `json:"price"`
}

var (
    store = make(map[int]Item) // In-memory store
    mutex sync.Mutex           // Ensures safe concurrent access
    nextID = 1
)

// Create
func createItem(w http.ResponseWriter, r *http.Request) {
    var newItem Item
    json.NewDecoder(r.Body).Decode(&newItem)

    mutex.Lock()
    newItem.ID = nextID
    store[nextID] = newItem
    nextID++
    mutex.Unlock()

    w.WriteHeader(http.StatusCreated)
    json.NewEncoder(w).Encode(newItem)
}

// Read
func getItems(w http.ResponseWriter, r *http.Request) {
    mutex.Lock()
    items := make([]Item, 0, len(store))
    for _, item := range store {
        items = append(items, item)
    }
    mutex.Unlock()

    json.NewEncoder(w).Encode(items)
}

// Update
func updateItem(w http.ResponseWriter, r *http.Request) {
    id, _ := strconv.Atoi(r.URL.Query().Get("id"))
    var updatedItem Item
    json.NewDecoder(r.Body).Decode(&updatedItem)

    mutex.Lock()
    if _, exists := store[id]; exists {
        updatedItem.ID = id
        store[id] = updatedItem
        w.WriteHeader(http.StatusOK)
        json.NewEncoder(w).Encode(updatedItem)
    } else {
        w.WriteHeader(http.StatusNotFound)
        fmt.Fprintln(w, "Item not found")
    }
    mutex.Unlock()
}

// Delete
func deleteItem(w http.ResponseWriter, r *http.Request) {
    id, _ := strconv.Atoi(r.URL.Query().Get("id"))

    mutex.Lock()
    if _, exists := store[id]; exists {
        delete(store, id)
        w.WriteHeader(http.StatusNoContent)
    } else {
        w.WriteHeader(http.StatusNotFound)
        fmt.Fprintln(w, "Item not found")
    }
    mutex.Unlock()
}

func main() {
    http.HandleFunc("/items", getItems)             // GET
    http.HandleFunc("/items/create", createItem)    // POST
    http.HandleFunc("/items/update", updateItem)    // PUT
    http.HandleFunc("/items/delete", deleteItem)    // DELETE

    fmt.Println("Server is running on http://localhost:

8080")
    http.ListenAndServe(":8080", nil)
}
```


# Unit 5

## **Buffered vs Unbuffered Channels in Go**  

Channels are used to facilitate communication between goroutines. The primary difference between **buffered** and **unbuffered** channels lies in how they handle data sending and receiving.

### **Unbuffered Channels**  
- **Definition**: Data transfer occurs directly between the sender and receiver. The sender is blocked until the receiver is ready, and vice versa.
- **Characteristics**:  
  - Synchronous communication.  
  - Requires both sender and receiver to be active simultaneously.  
  - Used when immediate handoff of data is required.  
- **Example**:  
  ```go
  package main

  import "fmt"

  func main() {
      ch := make(chan int) // Unbuffered channel

      go func() {
          ch <- 42 // Sender will block until the receiver is ready
          fmt.Println("Sent data to channel")
      }()

      value := <-ch // Receiver waits for sender
      fmt.Println("Received:", value)
  }
  ```
  **Expected Output**:
  ```
  Sent data to channel
  Received: 42
  ```

### **Buffered Channels**  
- **Definition**: Buffered channels allow the sender to send data even if the receiver isn’t ready, up to the channel’s buffer capacity.
- **Characteristics**:  
  - Asynchronous communication.  
  - Sender blocks only if the buffer is full.  
  - Receiver blocks only if the buffer is empty.  
- **Example**:  
  ```go
  package main

  import "fmt"

  func main() {
      ch := make(chan int, 2) // Buffered channel with capacity 2

      ch <- 10 // Sender does not block
      ch <- 20
      fmt.Println("Sent data to buffer")

      fmt.Println("Received:", <-ch) // Receiver gets data
      fmt.Println("Received:", <-ch)
  }
  ```
  **Expected Output**:
  ```
  Sent data to buffer
  Received: 10
  Received: 20
  ```

### **Key Differences**  
| **Feature**            | **Unbuffered Channel**         | **Buffered Channel**           |
|------------------------|--------------------------------|--------------------------------|
| **Blocking**            | Sender and receiver block.    | Sender blocks if buffer is full. Receiver blocks if buffer is empty. |
| **Synchronization**     | Synchronous communication.    | Asynchronous communication.    |
| **Buffering**           | No buffering.                 | Fixed capacity buffer.         |
| **Use Case**            | Immediate data exchange.       | When processing delays are acceptable. |

---

## **Creating a Package in Go**  

### **What is a Package?**  
A **package** in Go is a way to group related functions, types, and variables into a single reusable unit. All Go programs consist of at least one package (`main`).  

### **Steps to Create a Package**  
1. **Create a Directory**:  
   Each package resides in its own directory.  
   Example: Create a directory named `mypackage`.  

2. **Write the Code**:  
   Create a `.go` file in the package directory and start the file with `package <name>`.  
   Example:  
   ```go
   // mypackage/mymath.go
   package mypackage

   // Add adds two numbers
   func Add(a, b int) int {
       return a + b
   }

   // Subtract subtracts two numbers
   func Subtract(a, b int) int {
       return a - b
   }
   ```
   **Expected Output**: There is no direct output here; this is just the code for creating the package.

3. **Import and Use the Package**:  
   In the main program, import your package.  
   ```go
   package main

   import (
       "fmt"
       "path/to/mypackage" // Use the relative path or module name
   )

   func main() {
       fmt.Println(mypackage.Add(10, 20))       // Output: 30
       fmt.Println(mypackage.Subtract(20, 10)) // Output: 10
   }
   ```
   **Expected Output**:
   ```
   30
   10
   ```

4. **Compile and Run**:  
   Ensure that your Go module includes the package directory. Run `go mod init` and `go build` as needed.

---

## **Goroutines**  

### **What are Goroutines?**  
- **Definition**: A goroutine is a lightweight thread managed by the Go runtime.  
- **Key Features**:  
  - Goroutines are created using the `go` keyword.  
  - They are cheaper than system threads.  
  - The Go runtime uses a **scheduler** to manage goroutines.  
- **Example**:  
  ```go
  package main

  import (
      "fmt"
      "time"
  )

  func printMessage(msg string) {
      for i := 0; i < 5; i++ {
          fmt.Println(msg, i)
          time.Sleep(500 * time.Millisecond)
      }
  }

  func main() {
      go printMessage("Goroutine") // Start a goroutine
      printMessage("Main")        // Run in the main thread
  }
  ```
  **Expected Output**:
  ```
  Main 0
  Main 1
  Goroutine 0
  Main 2
  Goroutine 1
  Main 3
  Goroutine 2
  Main 4
  Goroutine 3
  Goroutine 4
  ```

---

## **Concurrency vs. Parallelism**  

### **Concurrency**  
- **Definition**: The ability to handle multiple tasks at the same time (logical concurrency), but not necessarily executing them simultaneously.  
- **Key Features**:  
  - Tasks switch contexts frequently.  
  - Best suited for tasks involving waiting (e.g., network requests).  

### **Parallelism**  
- **Definition**: The ability to execute multiple tasks simultaneously on multiple processors or cores.  
- **Key Features**:  
  - Requires multiple CPU cores.  
  - Ideal for computationally intensive tasks.  

### **Concurrency in Go**  
Go achieves concurrency through **goroutines** and **channels**.  
Example of concurrent execution:  
```go
package main

import (
    "fmt"
    "time"
)

func task(name string) {
    for i := 0; i < 3; i++ {
        fmt.Println(name, "task running", i)
        time.Sleep(500 * time.Millisecond)
    }
}

func main() {
    go task("Task1")
    go task("Task2")

    time.Sleep(2 * time.Second) // Wait for goroutines to finish
    fmt.Println("All tasks completed")
}
```
**Expected Output**:
```
Task1 task running 0
Task2 task running 0
Task1 task running 1
Task2 task running 1
Task1 task running 2
Task2 task running 2
All tasks completed
```

### **Parallelism in Go**  
Go enables parallelism by utilizing multiple CPU cores. Use the `runtime` package to control the number of threads.  
```go
package main

import (
    "fmt"
    "runtime"
    "sync"
)

func task(wg *sync.WaitGroup, id int) {
    defer wg.Done()
    fmt.Printf("Task %d running on core %d\n", id, runtime.NumCPU())
}

func main() {
    runtime.GOMAXPROCS(4) // Limit Go to 4 threads (if available)
    var wg sync.WaitGroup

    for i := 1; i <= 4; i++ {
        wg.Add(1)
        go task(&wg, i)
    }

    wg.Wait()
    fmt.Println("Parallel tasks completed")
}
```
**Expected Output**:
```
Task 1 running on core 4
Task 2 running on core 4
Task 3 running on core 4
Task 4 running on core 4
Parallel tasks completed
```

### **Concurrency vs Parallelism in Go**  
| **Aspect**             | **Concurrency**                         | **Parallelism**                         |
|------------------------|------------------------------------------|------------------------------------------|
| **Definition**          | Multiple tasks progress simultaneously (not necessarily at the same time). | Multiple tasks execute at the same time on multiple cores. |
| **Execution**           | Task switching.                        | True simultaneous execution.            |
| **Goroutines**          | Lightweight concurrency.               | Can run in parallel if multiple cores exist. |
| **Use Case**            | Network requests, I/O tasks.           | Heavy computations, data processing.    |

