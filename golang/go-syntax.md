# Go Syntax

## Short Notes

* Named return

```go
func add(x , y int) (p int) {
  p = x+y            
  // Notice you dont have to use := to initialise p 
  // because it's already declared in the return
  return
}
```

func main\(\){ fmt.Println\("Sum is : ",add\(3,4\)\) }

```go
- Data Types
```go
byte        alias for uint8
rune        alias for int32
```

```go
uint     unsigned, either 32 or 64 bits
int      signed, either 32 or 64 bits
uintptr  unsigned integer large enough to store the uninterpreted bits of a pointer value
```

* If Short Hand

```go
func funcPow( x,n,limit float64 ) float64 {
    if v:= math.Pow(x,n);
    v < limit {
        return v
    }
    return limit
}
```

* Defer

  ```go
  func main() {
    defer fmt.Println("world")
    fmt.Println("hello")
  }
  ```

  Defer : A defer statement defers the execution of a function until the surrounding function returns. The deferred call's arguments are evaluated immediately, but the function call is not executed until the surrounding function returns.

* Sprint

  ```go
  func funcSqrt( x float64 ) string {
    if x < 0 {
        return funcSqrt(-x) + "i"
    }
    return fmt.Sprint(math.Sqrt(x))
  }
  ```

* Switch

  ```go
  func main() {
    fmt.Print("Go runs on ")
    switch os := runtime.GOOS; os {
    case "darwin":
        fmt.Println("OS X.")
    case "linux":
        fmt.Println("Linux.")
    default:
        // freebsd, openbsd,
        // plan9, windows...
        fmt.Printf("%s.\n", os)
    }
  }
  ```

* Switch Operations

  ```go
  func main() {
    fmt.Println("When's Saturday?")
    today := time.Now().Weekday()
    fmt.Print(time.Saturday,"\n",today,"\n")
    switch time.Saturday {
    case today + 0:
        fmt.Println("Today.")
    case today + 1:
        fmt.Println("Tomorrow.")
    case today + 2:
        fmt.Println("In two days.")
    default:
        fmt.Println("Too far away.")
    }
  }
  ```

* tagless switch

  ```go
  switch {
  case t.Hour() < 12:
    fmt.Println("Good morning!")
  case t.Hour() < 17:
    fmt.Println("Good afternoon.")
  default:
    fmt.Println("Good evening.")
  }
  ```

* Function Closure Go functions may be closures. A closure is a function value that references variables from outside its body. The function may access and assign to the referenced variables; in this sense the function is "bound" to the variables. hence the function becomes static in some sense and its lifetime is that of the variable it gets binded to. also the internal variable of the func also lives as long as the binded variable

```go
package main

import "fmt"

func adder() func(int) int {
    sum := 0
    return func(x int) int {
        sum += x
        return sum
    }
}

func main() {
    pos, neg := adder(), adder()
    for i := 0; i < 10; i++ {
        fmt.Println(
            pos(i),
            neg(-2*i),
        )
    }
}
```

### panic and recover

Earlier, we created a function that called the panic function to cause a runtime error. We can handle a runtime panic with the built-in recover function. recover stops the panic and returns the value that was passed to the call to panic . We might be tempted to recover from a panic like this:

```go
package main
import "fmt"
func main() {
    panic("PANIC")
    str := recover() // this will never happen
    fmt.Println(str)
}
```

But the call to recover will never happen in this case, because the call to panic imme‐ diately stops execution of the function. Instead, we have to pair it with defer :

```go
package main
import "fmt"
func main() {
    defer func() {
        str := recover()
        fmt.Println(str)
    }()
    panic("PANIC")
}
```

