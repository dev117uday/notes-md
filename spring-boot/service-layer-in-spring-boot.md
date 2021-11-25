# Service Layer in Spring Boot

### `@Component`

* It is an annotation that allows Spring to automatically detect our custom beans
* Can only be annotate on a class
* `@Service` and `@Repository` are special cases of `@Component`.

### `@Bean`

_In Spring, the objects that form the backbone of your application and that are managed by the Spring IoC container are called beans. A bean is an object that is instantiated, assembled, and otherwise managed by a Spring IoC container._

### `@Service`

Service Components are the class file which contains @Service annotation. These class files are used to write business logic in a different layer, between `@RestController` class and `@Repository`&#x20;

### `@Repository`

@Repository annotates classes at the persistence layer, which will act as a database repository.

### `@Autowired`

* Enables automatic dependency injection. In other words, by declaring all the bean dependencies in a Spring configuration file, Spring container can auto wire relationships between collaborating beans. This is called Spring bean auto-wiring.

```java
@Component
public class FooService {  
    @Autowired
    private IDependency dependency;
}
```

### `@JsonProperty`

* To map the object data member to exact field of JSON when parsed.

### `@Qualifier("fakeDao")`

* You can mark a component with name, ex : `@Component("fakedao")` and when performing dependency injection, you can specifies which component to exactly inject, ex : `@Qualifier("fakedao")`

```java
@Autowired
public PersonService(@Qualifier("fakeDao") PersonDao personDao) {
    this.personDao = personDao;
}
```

### `@Primary`

* There's another annotation called @Primary that we can use to decide which bean to inject when ambiguity is present regarding dependency injection.
* This annotation defines a preference when multiple beans of the same type are present.
