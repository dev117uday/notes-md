## Iota basic example

- The iota keyword represents successive integer constants 0, 1, 2,…
- It resets to 0 whenever the word const appears in the source code,
- and increments after each const specification.

```go
const (
    C0 = iota
    C1 = iota
    C2 = iota
)
fmt.Println(C0, C1, C2) // "0 1 2"
```

This can be simplified to

```go
const (
	C0 = iota
	C1
	C2
)
```

Here we rely on the fact that expressions are implicitly repeated in a paren­thesized const declaration – this indicates a repetition of the preceding expression and its type.

Start from one
To start a list of constants at 1 instead of 0, you can use iota in an arithmetic expression.

```
const (
    C1 = iota + 1
    C2
    C3
)
fmt.Println(C1, C2, C3) // "1 2 3"
```

Skip value
You can use the blank identifier to skip a value in a list of constants.

```
const (
    C1 = iota + 1
    _
    C3
    C4
)
fmt.Println(C1, C3, C4) // "1 3 4"
```

**Complete enum type with strings [best practice]**
Here’s an idiomatic way to implement an enumerated type:

- create a new integer type,
- list its values using iota,
- give the type a String function.
- type Direction int

```
const (
    North Direction = iota
    East
    South
    West
)

func (d Direction) String() string {
    return [...]string{"North", "East", "South", "West"}[d]
}
```


In use:

```
var d Direction = North
fmt.Print(d)
switch d {
case North:
    fmt.Println(" goes up.")
case South:
    fmt.Println(" goes down.")
default:
    fmt.Println(" stays put.")
}
// Output: North goes up.
```

#### Naming convention
The standard naming convention is to use mixed caps also for constants. For example, an exported constant is NorthWest, not NORTH_WEST.