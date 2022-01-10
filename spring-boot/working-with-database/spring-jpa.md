# Spring JPA

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
