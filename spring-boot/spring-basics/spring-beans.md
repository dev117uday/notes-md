# Spring Beans

### Using XML as configuration

1. Add the dependency to `pom.xml`

```markup
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>5.3.16</version>
</dependency>
```

2\. Create a `spring.xml` in resources folder

```java
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
    http://www.springframework.org/schema/context
    http://www.springframework.org/schema/context/spring-context-3.0.xsd">

    <bean id="doctor" class="com.backend.springtok.entity.Doctor">
        <property name="qualification" value="MBBS"/>
        <property name="nurse" ref="nurse"/>
        <constructor-arg value="MBBS"/>
    </bean>

</beans>
```

3.1 Doctor as example

```java
package com.backend.springtok.entity;

public class Doctor implements Staff {

    private String qualification;
    private Nurse nurse;

    public Doctor(String qualification) {
        this.qualification = qualification;
    }

    public void assist() {
        System.out.println("doctor is assisting");
    }

    public String getQualification() {
        return qualification;
    }

    public void setQualification(String qualification) {
        this.qualification = qualification;
    }

    public Nurse getNurse() {
        return nurse;
    }

    public void setNurse(Nurse nurse) {
        this.nurse = nurse;
    }

    @Override
    public String toString() {
        return "Doctor{" +
                "qualification='" + qualification + '\'' +
                ", nurse=" + nurse +
                '}';
    }
}
```

3\. Create a application context

```java
ApplicationContext context = new ClassPathXmlApplicationContext("spring.xml");

// to create a bean
Doctor doctor = context.getBean(Doctor.class);
```

### Using Class based configuration

1. create a config bean class

```java
@Configuration
@ComponentScan( basePackages = "com.backend.springtok.entity")
public class BeanConfig {

    @Bean
    public NewDoctor getNewDoctor() {
        return new NewDoctor();
    }

}
```

2\. Create class to construct bean of

```java
@Scope(scopeName = "singleton")
// you can define the any other scope like prototype as well
public class NewDoctor implements Staff, BeanNameAware {

    private String qualification;

    public void assist() {
        System.out.println("new doctor is assisting");
    }

    public String getQualification() {
        return qualification;
    }

    public void setQualification(String qualification) {
        this.qualification = qualification;
    }

    @Override
    public String toString() {
        return "NewDoctor{" +
                "qualification='" + qualification + '\'' +
                '}';
    }

    @Override
    public void setBeanName(String s) {
        System.out.println("call for setBeanName");
    }

    @PostConstruct
    public void postConstruct(){
        System.out.println("post construct called");
    }
}
```

3\. Add this to your `spring.xml` under the beans tag

```markup
<context:component-scan base-package="com.backend.springtok"/>
```

4\. Create application context to initialise and manage beans

```java
ApplicationContext anotherContext = 
    new AnnotationConfigApplicationContext(BeanConfig.class);

var newDoctor = anotherContext.getBean(NewDoctor.class);
newDoctor.assist();
newDoctor.setQualification("MBBS++");
System.out.println(newDoctor);
```

Using the `javax.annotation.api` , we can annotate different methods at different bean life-cycle to execute some code. Example, in `NewDoctor` class in above example, we have `@PostContruct` method which is called after the bean is created by spring.

```java
    @PostConstruct
    public void postConstruct(){
        System.out.println("post construct called");
    }
```

### Creating a protoptye bean inside singleton class

If you declare a prototype bean inside a singleton class, and create 2 different instance of singleton, there prototype bean will also be the same

```java
// example : prototype

@Service
@Scope("prototype")
public class WeatherService {

    String time = LocalDateTime.now().toString();
    int temp = new Random().nextInt(60);

    public String getTodayTemp() {
        return time + " -> " + temp;
    }
}

// service : singleton

@Service
public class UserService {

    @Autowired
    WeatherService weatherService;

    @Autowired
    ApplicationContext context;

    @Autowired
    private ObjectFactory<WeatherService> wFactory;
    // use this to create seperate beans for each singleton instance

    public String getCurrentTemp() {
        return weatherService.getTodayTemp();
    }

    public String getCurrentTempDiff() {
        // not recommended
        // return context.getBean(WeatherService.class).getTodayTemp();
        return wFactory.getObject().getTodayTemp();
    }

}
```
