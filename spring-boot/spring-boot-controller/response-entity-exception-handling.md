# Response Entity Exception Handling

* mark the class with `ControllerAdvice` and `ResponseStatus`
* The class should **extend** `ResponseEntityExceptionHandler`
* Annotate the member function with `@ExceptionHandler(T.class)` where T is the custom exception class
* Make sure to include `String message` and `Integer statusCode` in the custom exception.
* Example

```java
@ControllerAdvice
@ResponseStatus
public class RestResponseEntityExceptionHandler extends ResponseEntityExceptionHandler 
{

    @ExceptionHandler(DepartmentExceptions.class)
    public ResponseEntity<ErrorMessage> 
        departmentException(DepartmentExceptions exception) 
    {

        Integer exceptionStatus = exception.getStatusCode();

        if (exceptionStatus == 404) {
            ErrorMessage message =
                new ErrorMessage(HttpStatus.NOT_FOUND, exception.getMessage());
            
            return ResponseEntity.status(HttpStatus.CREATED).body(message);
        }
    }

}
```
