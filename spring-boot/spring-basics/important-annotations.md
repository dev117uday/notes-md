# Important Annotations

### `@SpringBootTest & @Test`

```java
@SpringBootTest
public class CourseRepositoryTest {

	@Autowired
	private CourseRepository courseRepository;

	@Test
	public void saveCourse() {
		List<Course> courses = courseRepository.findAll();
		System.out.println("courses = " + courses);
	}
```

### `@Component`

* It is an annotation that allows Spring to automatically detect our custom beans
* Can only be annotate on a class
* `@Service` and `@Repository` are special cases of `@Component`.

### `@Service`

Service Components are the class file which contains @Service annotation. These class files are used to write business logic in a different layer, between `@RestController` class and `@Repository`

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

### `@Primary`

* There's another annotation called @Primary that we can use to decide which bean to inject when ambiguity is present regarding dependency injection.
* This annotation defines a preference when multiple beans of the same type are present.

### `@EnableConfigurationProperties`

```java
@EnableConfigurationProperties(SecretConfigProp.class)
```

To load config from Class, refer below annotation

### @ConfigurationProperties("secret")

````java
@ConfigurationProperties("secret")
public record SecretConfigProp(String username, String password, String authToken) {
}

```spring-boot-properties
secret.authToken:my_auth_token
secret.username:myusername

spring.config.import:optional:secrets.properties
```

```java-properties
secret.password=password
```
````

