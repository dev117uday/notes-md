---
description: This is a short summary of effective_go - 1
---

# Learning Go - 1

## Formatting

* use `gofmt` to format packages

## Commentary

* Go uses c like comments `//` or `/* */`
* **Every `Function/Struct/Variable` that you have to export, name it so that first letter is capital**

## Package name

* short, concise, evocative
* the package in `src/encoding/base64` is imported as `"encoding/base64"` but has name `base64`, not `encoding_base64` and not `encodingBase64`.

## Getters & Setters

* Go doesn't provide automatic support for **getters** and **setters**. There's nothing wrong with providing **getters** and **setters** yourself, and it's often appropriate to do so.
* ```go
  owner := obj.Owner()
  if owner != user {
      obj.SetOwner(user)
  }
  ```

## Naming

### Interface Naming

* By convention, one-method interfaces are named by the method name plus an -er suffix or similar modification to construct an agent noun: `Reader`, `Writer`, `Formatter`, `CloseNotifier` etc.

### Variable Naming

* Finally, the convention in Go is to use `MixedCaps` or `mixedCaps` rather than underscores to write multi word names

### Indentation

* ```go
  if i < f() {
      g()
  }

  if i < f()  // wrong!
  {           // wrong!
      g()
  }
  ```

## Control Structure

* There is no `do` or `while` loop, only a slightly generalised `for`; `switch` is much better
* **If**
* In Go a simple `if` looks like this:

```go
if x > 0 {
    return y
}
```

* Mandatory braces encourage writing simple `if` statements on multiple lines. It's good style to do so anyway, especially when the body contains a control statement such as a `return` or `break`. Since `if` and `switch` accept an initialisation statement, it's common to see one used to set up a local variable.

```go
if err := file.Chmod(0664); err != nil {
    log.Print(err)
    return err
}
```

## Re-declaration and Re-assignment

* The last example in the previous section demonstrates a detail of how the `:=` short declaration form works. The declaration that calls `os.Open` reads,

```go
f, err := os.Open(name)
```

* This statement declares two variables, `f` and `err`. A few lines later, the call to `f.Stat` reads,

```go
d, err := f.Stat()
```

​ which looks as if it declares `d` and `err`. Notice, though, that `err` appears in both statements. This duplication is legal: `err` is declared by the first statement, but only _re-assigned_ in the second. This means that the call to `f.Stat` uses the existing `err` variable declared above, and just gives it a new value.

* In a `:=` declaration a variable `v` may appear even if it has already been declared, provided:
  * this declaration is in the same scope as the existing declaration of `v` \(if `v` is already declared in an outer scope, the declaration will create a new variable §\),
  * the corresponding value in the initialisation is assignable to `v`, and
  * there is at least one other variable that is created by the declaration

## Range

* If you're looping over an array, slice, string, or map, or reading from a channel, a `range` clause can manage the loop.

```go
for key, value := range oldMap {
    newMap[key] = value
}
```

* If you only need the first item in the range \(the key or index\), drop the second:

```go
for key := range m {
    if key.expired() {
        delete(m, key)
    }
}
```

* If you only need the second item in the range \(the value\), use the _blank identifier_, an underscore, to discard the first:

```go
sum := 0
for _, value := range array {
    sum += value
}
```

## Switch in Golang

* Go's `switch` is more general than C's.
* It's therefore possible—and idiomatic—to write an `if`-`else`-`if`-`else` chain as a `switch`.

```go
func unhex(c byte) byte {
    switch {
    case '0' <= c && c <= '9':
        return c - '0'
    case 'a' <= c && c <= 'f':
        return c - 'a' + 10
    case 'A' <= c && c <= 'F':
        return c - 'A' + 10
    }
    return 0
}
```

* There is no automatic fall through, but cases can be presented in comma-separated lists.

```go
func shouldEscape(c byte) bool {
    switch c {
    case ' ', '?', '&', '=', '#', '+', '%':
        return true
    }
    return false
}
```

#### Type Switch

* A switch can also be used to discover the dynamic type of an interface variable

```go
var t interface{}
t = functionOfSomeType()
switch t := t.(type) {
default:
    fmt.Printf("unexpected type %T\n", t)     // %T prints whatever type t has
case bool:
    fmt.Printf("boolean %t\n", t)             // t has type bool
case int:
    fmt.Printf("integer %d\n", t)             // t has type int
case *bool:
    fmt.Printf("pointer to boolean %t\n", *t) // t has type *bool
case *int:
    fmt.Printf("pointer to integer %d\n", *t) // t has type *int
}
```

## Functions

### Multiple return values

```go
func squareRoot (num int) (n float, err error)
// or
func squareRoot (num int) (float, error)
// to return error if num < 0
```

// named return

## Defer

* Go's `defer` statement schedules a function call \(the _deferred_ function\) to be run immediately before the function exits.

```go
func fileContent (filename string) (string, error) {
    f, err := os.Open(filename)
    if err != nil {
        return "", err
    }
    // defer will run the function just before exiting the function fileContents
    defer f.Close()
    // something with return   
}
```

* Deferring a call to a function such as `Close` has two advantages. 
  * First, it guarantees that you will never forget to close the file, a mistake that's easy to make if you later edit the function to add a new return path. 
  * Second, it means that the close sits near the open, which is much clearer than placing it at the end of the function.
* For Example : 

```go
for i := 0; i < 5; i++ {
    defer fmt.Printf("%d ", i)
}
```

* Deferred functions are executed in LIFO order, so this code will cause `4 3 2 1 0` to be printed when the function returns
* A more plausible example is a simple way to trace function execution through the program. We could write a couple of simple tracing routines like this:

```go
func trace(s string)   { fmt.Println("entering:", s) }
func untrace(s string) { fmt.Println("leaving:", s) }

// Use them like this:
func a() {
    trace("a")
    defer untrace("a")
    // do something....
}
```

