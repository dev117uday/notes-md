# Important Annotations

### `@Configuration`

Use `@Configuration` annotation on top of any class to declare that this class provides one or more **@Bean** methods and may be processed by the Spring container to generate bean definitions and service requests for those beans at runtime.

```java
@Configuration
public class AppConfig {
 
    @Bean(name="demoService")
    public DemoClass service() 
    {
        
    }
}

# somewhere else in code

DemoManager  obj = (DemoManager) context.getBean("demoService");
```



### `@ToString`

* options
  * exclude = "data\_member"

### `@SpringBootTest`

* persists data in db

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

