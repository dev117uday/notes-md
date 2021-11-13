# Controller in Spring Boot

### `@Controller`

A simple version to annotate a class as controller

* You need to annotate `@ResponseBody` in front of the return type of member function.

```java
@Controller
@RequestMapping("books")
public class SimpleBookController {
    @GetMapping("/{id}", produces = "application/json")
    public @ResponseBody Book getBook(@PathVariable int id) {

    }
}
```

### `@RestController`

Is a specialised version of the controller. It includes the `@Controller` and `@ResponseBody` annotation.

* No need to annotate return type with `@ResponseBody`

```java
@RestController
@RequestMapping("books-rest")
public class SimpleBookRestController {
    
    @GetMapping("/{id}", produces = "application/json")
    public Book getBook(@PathVariable int id) {

    }
}
```

### `@RequestMapping`

Helps the server to route requests to the controller classes specified in string parameter

```java
@RequestMapping(
  value = "/ex/foos", 
  method = RequestMethod.GET, 
  produces = "application/json"
)
```

* Fallback for all requests that didn't match

```java
@RequestMapping(value = "*", method = RequestMethod.GET)
```

### `@RequestBody`

@RequestBody annotation maps the `HttpRequest` body to a transfer or domain object, enabling automatic de-serialisation. Spring automatically de-serialises the JSON into a Java type

```java
@GetMapping("/{id}", produces = "application/json")
public @ResponseBody Book getBook(@PathVariable int id) 
{

}
```

### `@PathVariable`

Used endpoint that identifies an entity with a primary key:

```java
@GetMapping("/api/{id}")
public String getEmployeesById(@PathVariable String id) 
{

}
```

### `@PathVariable`

Can be used to handle template variables in the request URI mapping

```java
@GetMapping("/api/employees/{id}")
@ResponseBody
public String getEmployeesById(@PathVariable("id") String id) {
    return "ID: " + id;
}

-- Multiple PathVariable

@GetMapping("/api/employees/{id}/{name}")
@ResponseBody
public String getEmployeesByIdAndName(
    @PathVariable String id, @PathVariable String name) 
{

}

-- Capture PathVariable in MapString

@GetMapping("/api/employeeswithmapvariable/{id}/{name}")
@ResponseBody
public String getEmployeesById(
    @PathVariable Map<String, String> pathVarsMap) 
{

}

    
-- when PathVariable isnt required 

@GetMapping(value = { "employees/", "employees/{id}" })
@ResponseBody
public String getEmployeesById(@PathVariable(required = false) String id) 
{

}
```

### `@RequestParam`

```java
@PostMapping("/api/foos")
@ResponseBody
public String addFoo(@RequestParam(name = "id") String fooId, @RequestParam String name) 
{ 

}

http://localhost:8080/api/foos?id=1&name=uday

-- Multiple RequestParam 
@GetMapping("/api/foos")
@ResponseBody
public String getFoos(@RequestParam List<String> id) {

}

http://localhost:8080/api/foos?id=1,2,3
```

### HTTP Mapping

```java
-- @GetMapping("/get")

public @ResponseBody ResponseEntity<String> get() {
    return new ResponseEntity<String>("GET Response", HttpStatus.OK);
}

-- @PostMapping
@PostMapping("/post")
public @ResponseBody ResponseEntity<String> post() {
    return new ResponseEntity<String>("POST Response", HttpStatus.OK);
}

-- @PutMapping
@PutMapping("/put")
public @ResponseBody ResponseEntity<String> put() {
    return new ResponseEntity<String>("PUT Response", HttpStatus.OK);
}
-- @DeleteMapping
@DeleteMapping("/delete")
public @ResponseBody ResponseEntity<String> delete() {
    return new ResponseEntity<String>("DELETE Response", HttpStatus.OK);
}

-- @PatchMapping
@PatchMapping("/patch")
public @ResponseBody ResponseEntity<String> patch() {
    return new ResponseEntity<String>("PATCH Response", HttpStatus.OK);
}
```

### `@ResponseEntity`

`ResponseEntity` represents the whole HTTP response: status code, headers, and body. As a result, we can use it to fully configure the HTTP response.

* mention the return type of a function as `ResponseEntity<T>`, cannot be null
* takes
  * `HTTPStatusCode`
  * Object to be returned

```java
@GetMapping("/hello")
ResponseEntity<String> hello() {
    return new ResponseEntity<>("Hello World!", HttpStatus.OK);
}
```
