# Spring Things

## Spring Scheduling

```java
// enable using 
@EnableScheduling
// on Main class

@Slf4j
@EnableAsync
public class SampleScheduler {

    @Async
    @Scheduled( cron = "* * * * * *" )
    // initialDelay = 1000
    // fixedDelay = 1000
    // fixedRateString = "PT02S"
    // cron stars : seconds, minutes, hours, day of month, month, day of week
    public void scheduler() throws InterruptedException {
        LocalDateTime current = LocalDateTime.now();
        DateTimeFormatter format = DateTimeFormatter.ofPattern("dd-MM-yyyy HH:mm:ss");
        String formattedDateTime = current.format(format);
        log.info("Scheduler time : " + formattedDateTime);

        // this will cause log print to delay 1 more second, new time 2 seconds
        Thread.sleep(1000);
    }

```

## Spring Validation

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Person {

    private final UUID id;

    @NotBlank
    @NotNull(message = "username should not be null")
    private final String name;

    @Email
    private String email;

    @Min(0)
    @Max(100)
    private int age;

    public Person(@JsonProperty("id") UUID id,
                  @JsonProperty("name") String name) {
        this.id = id;
        this.name = name;
    }

    public UUID getId() {
        return id;
    }

    public String getName() {
        return this.name;
    }
}
```

### To handle error

```java
@ResponseStatus(HttpStatus.BAD_REQUEST)
@ExceptionHandler(MethodArgumentNotValidException.class)
public Map<String, String> handleInvalidArgument(MethodArgumentNotValidException exception) {
    Map<String, String> errorMap = new HashMap<>();
    for (FieldError fieldErrors : exception.getBindingResult().getFieldErrors()) {
        errorMap.put(fieldErrors.getField(), fieldErrors.getDefaultMessage());
    }

    return errorMap;
}
```

### Defining on controller

```java
@PostMapping
public int addPerson( @Valid @NonNull @RequestBody Person person) {
    return personService.addPerson(person);
}
```

## Faker

To generate fake data

```java
<dependency>
        <groupId>com.github.javafaker</groupId>
        <artifactId>javafaker</artifactId>
        <version>1.0.2</version>
</dependency>



@Bean
public Faker faker() {
	return new Faker();
}

private final Faker faker;

@Override
public void run(String... args) throws Exception {

// create 100 rows of people in the database
List<Person> people = IntStream.rangeClosed(1, 100)
        .mapToObj(i -> new Person(
                faker.name().firstName(),
                faker.name().lastName(),
                faker.phoneNumber().cellPhone(),
                faker.internet().emailAddress(),
                new Address(
                        faker.address().streetAddress(),
                        faker.address().city()
                )
        )).toList();

repository.saveAll(people);
}

```

