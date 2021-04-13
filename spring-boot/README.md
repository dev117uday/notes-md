# Spring Boot

### Start point

```java
@SpringBootApplication
public class DemoApplication
{
    public static void main(String[] args)
    {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

* Project folder :

  ```text
  api         # Controller
  model       # Database Class
  dao         # Data Access Object
  service     # Between Dao and api
  ```

* config file inside : `application.properties` inside the folder `resources`
* final executable binary inside : `target` with the name `<name>.<version>-SNAPSHOT.jar`
* dependencies inside : `pom.xml`

## Annotations

`@AutoWired`

*  It allows Spring to resolve and inject collaborating beans into our bean.

## Bean


```java
@Bean
CommandLineRunner commandLineRunner(StudentRepository studentRepository) {
    return args -> {
        Student maria = new Student("uday","yadav","uday02yadav117@gmail.com",21);
        studentRepository.save(maria);
    };
}
```

## Controller

### Rest Controller

Class with to handle requests are marked as `@RestController` inside the api folder

* the path to request is declared inside a annotation : `@RequestMapping("api/v1/person")`
* classes and functions are set to `public`
* declare the service as `private` & `final`
* Constructor of controller class gets wired with service class by annotating : `@Autowired`
* All functions are annotated with HTTP method :

  ```text
  @PostMapping
  @DeleteMapping
  @PutMapping
  @GetMapping
  @PatchMapping
  ```

* they are available under : `import org.springframework.web.bind.annotation;`
* return type of of functions depends on the type of data to return
* By adding the `@Valid` annotation, we indicate that the entity contains constraints that need to be evaluated.
* We added the `@NotNull` constraint here because null values are “valid” by default
* The `@RequestBody` annotation maps the **HTTPRequest** body to a transfer or domain object, enabling automatic **deserialization** of the inbound **HTTPRequest** body onto a Java object.
* Also use `@JsonProperty("id")` in the model class, ex : Person & Book
* `@GetMapping(path = "{id}")` map the function to path and then use
* `public T <function_name>(@PathVariable("id") UUID id) {}` to assign it to a variable
* `@RequestParam(required = false)` is used to Request Parameters, those that come after `?name=uday&email=uada@sds.com`

## Data Access Object

**Data Access Objects**

* create a interface implementing all the functions needed.
* Actual class implements a interface    
* create a repository with : `@Repository("<db>")`

## Service

* annotate with `@Service`
* create a member `private final` of Dao
* create a constructor
  * `@Autowired`
  * `@Qualifier\(""\) `
  * `public Tservice(@Qualifier("<db>") T t)`
* `@Transactional`

## Repository

* create a interface implementing all the functions needed.
* Actual class implements a interface    
* create a repository with : `@Repository("<db>")`

Using `JpaRepository`

```java
public interface StudentRepository extends JpaRepository<Student,Long> {
    // JpaRepository contains alot of functions
    // Like save,find and much more
}
```

To create a custom function to run a custom query, use something like this:

```java
    @Query("select s from Student s where s.email = ?1")
    Optional<Student> findStudentByEmail(String email);
```

# Model 

## Model Class

Read more about `Entity` [here](https://www.baeldung.com/jpa-entities)

*  `@Entity` : Entities in JPA are nothing but plain old java object representing data that can be persisted to the database. An entity represents a table stored in a database. Every instance of an entity represents a row in the table.

  ```text
  @Entity(name = "Student")
  ```

* `@Table` : In most cases, the name of the table in the database and the name of the entity will not be the same. If we do not use the `@Table` annotation, the name of the entity will be considered the name of the table.

  ```text
  @Table(
          name = "Student",
          uniqueConstraints = {
                  @UniqueConstraint(name = "student_email_unique", columnNames = "email")
          }
  )
  ```

* `@Id` : [The _@Id_ annotation](https://www.baeldung.com/hibernate-identifiers) defines the primary key. We can generate the identifiers in different ways which are specified by the `@GeneratedValue` annotation.

  ```text
      @Id
      @SequenceGenerator(
              name = "student_sequence",
              sequenceName = "student_sequence",
              allocationSize = 1
      )
      @GeneratedValue(
              strategy = GenerationType.SEQUENCE,
              generator = "student_sequence"
      )
  ```

* `@Column` : Just like the `@Table` annotation, we can use the `@Column` annotation to mention the details of a column in the table. The `@Column` annotation has many elements such as _name, length, nullable, and unique_.

  ```text
  @Column(name="STUDENT_NAME", length=50, nullable=false, unique=false, columnDefinition = "TEXT")
      private String name;
  ```

  * The _name_ element specifies the name of the column in the table.
  * The _length_ element specifies its length.
  * The _nullable_ element specifies whether the column is nullable or not, and the _unique_ element specifies whether the column is unique.

* `@Transient` : Sometimes, we may want to **make a field non-persistent.** We can use the _@Transient_ annotation to do so. It specifies that the field will not be persisted. For instance, we can calculate the age of a student from the date of birth.

  ```text
      @Transient
      private Integer age;
  ```

  * As a result, the field _age_ will not be persisted to the table.


# Interfaces

## JpaRepository

```java
JpaRepository<Student,Long>
```

* This is used interface is used because it has a lot of in built function
* To implement your own function, try this : 

```java
@Query("select s from Student s where s.email = ?1")
```
# Configuration

### Examples

```java
@Configuration
public class StudentConfig {

    @Bean
    CommandLineRunner commandLineRunner (StudentRepository studentRepository) {
        return args -> {
            Student s = new Student( "uday", LocalDate.of(2000,02,01),"uday@gmail.com");
            Student s1 = new Student( "uday", LocalDate.of(2000,02,01),"uday1@gmail.com");
            Student s2 = new Student( "uday", LocalDate.of(2000,02,01),"uday2@gmail.com");
            Student s3 = new Student( "uday", LocalDate.of(2000,02,01),"uday3@gmail.com");
            studentRepository.saveAll(List.of(s,s1,s2,s3));
        };
    }
}
```
