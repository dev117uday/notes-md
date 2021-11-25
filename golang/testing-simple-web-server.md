---
description: Testing web server 101
---

# Testing simple web server

## Testing web server in Golang

* create a file with name `<anything>_test.go`, these files are ignore by compiler
* write a func matching `func TestXxx(*testing.T)`  where Xxx does not start with a lowercase letter. The function name serves to identify the test routine.
* To run the test : `go test`

## Testing

* inorder to test the handler, we call it by passing http.ResponseWriter and \*http.Request
* to create a new Request

```go
req, err := http.NewRequest(
    http.MethodGet,                 // defining method of HTTP request
    "http://localhost:8080/",       // Url to hit
    nil,                            // Body (taking nil right now)
)

// checking for any errors            
if err != nil {
    t.Fatalf("Could not create a request %v", err)
}
```

## To record the response from the writer

```go
rec := httptest.NewRecorder()
```

## To verify

```go
// calling the function
helloWorldEndPoint(rec, req)

// checking status code
if rec.Code != http.StatusOK {
    t.Errorf("accepted status 200, got %v", rec.Code)
}

// checking the msg returned
if !strings.Contains(rec.Body.String(), "hello world") {
    t.Errorf("unexpected body in response %q", rec.Body.String())
}
```

## Full code server.go

```go
package main

import (
    "fmt"
    "log"
    "net/http"
)

func main() {

    http.HandleFunc("/", helloWorldEndPoint)
    fmt.Println("Server :  http://localhost:8080")
    log.Fatal(http.ListenAndServe(":8080", nil))

}

func helloWorldEndPoint(writer http.ResponseWriter, request *http.Request) {

    fmt.Fprintf(writer, "hello world")

}
```

## Full code main_test.go

```go
package main

import (
    "net/http"
    "net/http/httptest"
    "strings"
    "testing"
)

func TestHandler(t *testing.T) {

    req, err := http.NewRequest(
        http.MethodGet,
        "http://localhost:8080/",
        nil,
    )

    if err != nil {
        t.Fatalf("Could not create a request %v", err)
    }

    rec := httptest.NewRecorder()
    helloWorldEndPoint(rec, req)

    if rec.Code != http.StatusOK {
        t.Errorf("accepted status 200, got %v", rec.Code)
    }

    if !strings.Contains(rec.Body.String(), "hello world") {
        t.Errorf("unexpected body in response %q", rec.Body.String())
    }

}
```

