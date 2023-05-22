---
description: better than jdbc !
---

# Spring Data JPA

### Configuration

```yaml
// FOR JPA
spring:
  datasource:
    url: jdbc:postgresql://[host]:[port]/[db name]
    username: username
    password: [password]

  jpa:
   hibernate.ddl-auto: update
   show-sql: true
   properties:
     hibernate:
       dialect: org.hibernate.dialect.PostgreSQLDialect
```

### Embedded

```java
@Embedded
private AnotherClass anotherClass;

// another class

@AttributeOverrides({
		@AttributeOverride(name = "something [in db]", 
		column = @Column(name = "something_field")),
})
public class AnotherClass {
	private String somethingField;
}
```

### OneToOne

```java
// example : class course one to one with courseMaterial
// course model
@OneToOne(mappedBy = "course")
private CourseMaterial courseMaterial;

// courseMaterial model
@OneToOne(
	cascade = CascadeType.ALL,
	fetch = FetchType.LAZY
)
@JoinColumn(
	name = "course_id",
	referencedColumnName = "courseId"
)
private Course course;
```

### `OneToMany` & `ManyToOne`

```java
// one teacher can teach many course
// one course can be taught by many teachers

// teacher class
@OneToMany(cascade = CascadeType.ALL)
@JoinColumn(name = "teacher_id", referencedColumnName = "teacherId")
private List<Course> courses;

// course class
@ManyToOne(cascade = CascadeType.ALL)
@JoinColumn(name = "teacher_id", referencedColumnName = "teacherId")
private Teacher teacher;
```

### `ManyToMany`

```java
// many students can take many courses

@ManyToMany(
	cascade = CascadeType.ALL
)
@JoinTable(
	name = "student_course_map", 
	joinColumns = @JoinColumn(
		name = "course_id", 
		referencedColumnName = "courseId"
	), 
	inverseJoinColumns = @JoinColumn(
		name = "student_id", 
		referencedColumnName = "studentId"
	)
)
private List<Student> students;
```

### `@Qualifier("")`

* You can mark a component with name, ex : `@Component("fakedao")` and when performing dependency injection, you can specifies which component to exactly inject, ex : `@Qualifier("fakedao")`

```java
@Autowired
public PersonService(@Qualifier("fakeDao") PersonDao personDao) {
    this.personDao = personDao;
}
```

### Repository Interface

```java
@Repository
public interface TRepository extends JpaRepository<T, Long> {

}
```

### Example Repository

```java
@Repository
public interface StudentRepository extends JpaRepository<Student, Long> {

	List<Student> findByFirstName(String firstName);

	// JPQL-native
	@Query(value = "select * from tbl_student s where s.email_address = ?1", nativeQuery = true)
	Student getStudentByEmailAddressNative(String emailId);

	// JPQL
	@Query("select s from Student s where s.emailId = ?1")
	Student findStudentByEmail(String emailId);

	// Native Named Param
	@Query (
		value = "select * from tbl_student s where s.email_address = :emailId",
		nativeQuery = true
	)
	Student getStudentByEmailAddressNativeNamed(@Param("emailId") String emailId);

	@Modifying
	@Transactional
	@Query (
		value = "update tbl_student set first_name = ?1 where email_address = ?2",
		nativeQuery = true
	)
	Integer updatStudentEmailIdByFirstName(String firstName, String emailId);
}
```

### Pagination and Sorting Repo

```java
@Repository
public interface PersonPageRepository extends PagingAndSortingRepository<Person, Integer> {
}


public Page<Person> findAll(@RequestParam int page, @RequestParam int size) {
    PageRequest pr = PageRequest.of(page,size);
    return repository.findAll(pr);
}

```
