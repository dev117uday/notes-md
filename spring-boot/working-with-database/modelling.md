# Modelling

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
