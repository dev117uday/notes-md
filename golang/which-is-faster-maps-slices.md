---
description: 'which is faster, can you guess ?'
---

# Which is faster : Maps, slices

## Using slice

```go
package main

import (
    "runtime"
)

type data struct {
    i, j int
}

func main() {
    var N = 40000000
    var structure []data
    for i := 0; i < N; i++ {
        value := int(i)
        structure = append(structure, data{value, value})
    }
    runtime.GC()
    _ = structure[0]
}
```

## Using a map with pointers

```go
package main

import (
    "runtime"
)

func main() {
    var N = 40000000
    myMap := make(map[int]*int)
    for i := 0; i < N; i++ {
        value := int(i)
        myMap[value] = &value
    }
    runtime.GC()
    _ = myMap[0]
}
```

## Using a map without pointers

```go
package main

import (
    "runtime"
)

func main() {
    var N = 40000000
    myMap := make(map[int]int)
    for i := 0; i < N; i++ {
        value := int(i)
        myMap[value] = value
    }
    runtime.GC()
    _ = myMap[0]
}
```

## Splitting the map

The implementation of this subsection will split the map into a map of maps, which is also called **sharding**. The program of this subsection is saved as `mapSplit.go` and will be presented in two parts

```go
package main

import (
    "runtime"
)

func main() {
    var N = 40000000
    split := make([]map[int]int, 200)
    for i := range split {
        split[i] = make(map[int]int)
    }
    for i := 0; i < N; i++ {
        value := int(i)
        split[i%200][value] = value
    }
    runtime.GC()
    _ = split[0][0]
}
```

## Results

What will be important in the presented output is not the exact numbers but the time difference between the four different approaches.

```go
$ time go run main.go 

Using plain slices    

real    0m1.058s
user    0m1.319s
sys     0m0.301s

Using map with pointers

real    0m15.667s
user    0m27.961s
sys     0m1.722s

Using map without pointer

real    0m15.667s
user    0m27.961s
sys     0m1.722s

Spliting map

real    0m9.349s
user    0m8.636s
sys     0m0.826s
```

