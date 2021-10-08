---
description: Its sweet
---

# Competitive Programming in Go

## Things to refer

### Min/Max Int and Uint

```go
const MaxUint = ^uint(0)
const MinUint = 0

const MaxInt = int(^uint(0) >> 1)
const MinInt = -MaxInt - 1
```

### 2d-vector-input.go

```go
package main

import (
    "fmt"
)

func main() {

    var cols, rows = 0, 0
    fmt.Print("Enter the number of cols : ")
    _, _ = fmt.Scan(&cols)
    fmt.Print("Enter the number of rows : ")
    _, _ = fmt.Scan(&rows)

    var twodslices = make([][]int, rows)
    var i int
    for i = range twodslices {
        twodslices[i] = make([]int, cols)
    }

    for i := 0; i < rows; i++ {
        for j:=0; j<cols; j++ {
            fmt.Scan(&twodslices[i][j])
        }
    }
    fmt.Println(twodslices)
}
```

### custom-vector-input.go

```go
package main

import (
    "fmt"
)

func main() {
    numberOfStrings := 0
    var vector []string
    _, _ = fmt.Scanln(&numberOfStrings)

    {
        var number string
        for i := 0; i < numberOfStrings; i++ {
            _, _ = fmt.Scanln(&number)
            vector = append(vector, number)
        }
    }

}
```

### integer-input.go

```go
package main

import "fmt"

func main() {
    var number int32
    _, _ = fmt.Scanf("%d", &number)
    fmt.Println(number)
}
```

### map-slice.go

```go
package main

import "fmt"

func main() {

    var elements = make([]map[string]string,1)
    elements[0] = map[string]string {
        "uday" : "uday",
    }

    fmt.Println(elements[0]["uday"])


}
```

### string-input.go

```go
package main

import (
    "bufio"
    "fmt"
    "os"
)

func main() {

    fmt.Print("Enter your full name : ")
    myString, _ := bufio.NewReader(os.Stdin).ReadString('\n')
    fmt.Print("myString : ", myString)

}
```

### vector-input-integer.go

```go
package main

import "fmt"

func main() {

    var number int
    _, _ = fmt.Scanln(&number)
    var vector = make([]int, number)
    for i := 0; i < number; i++ {
        _, _ = fmt.Scan(&vector[i])
    }
    fmt.Println(vector)
}
```

