# Spring Basics

Resources :&#x20;

* [Spring Constructor Injection: Why is it the recommended approach to Dependency Injection?](https://www.youtube.com/watch?v=aX-bgylmprA)

### Why framework ?

The aim of frameworks is to provide a common structure so that developers don't have to redo it from scratch and can reuse the code provided. In this way, frameworks allow us to cut out much of the work and save a lot of time. To summarise: there's no need to reinvent the wheel

#### Spring allows

* Inversion of control : from programmer to framework
  * automatically configures things in order
  * create object of required classes
* Aspect Oriented Programming
  * breaking code into different modules
  * reduces cross cutting concerns : **Dont Repeat Yourself**
    * example : security is crosscutting because it is applied in many methods in an application
    * example : logging, exception handling
    * It does so by advising the current code on how to handle situation.
  * https://www.geeksforgeeks.org/aspect-oriented-programming-and-aop-in-spring-framework/
* Dependency Injection
* Spring data projects

### What is dependency injection ?

Dependency injection is basically providing the objects that an object needs (its dependencies) instead of having it construct them itself.

### What is inversion of controller ?

Inversion of Control is a principle in software engineering which transfers the control of objects or portions of a program to a container or framework.

The advantages of this architecture are:

* decoupling the execution of a task from its implementation
* making it easier to switch between different implementations
* greater modularity of a program&#x20;
* greater ease in testing a program by isolating a component or mocking its dependencies, and allowing components to communicate through contracts

### What is Spring Bean ?

* Bean is a fancy word for object
* A spring bean is just an object that manages for you

Beans are generate at bean-factory, and then there is application context, which extends bean-factory and provides additional features

#### Types of Beans

* Singleton
  * 1 object in he entire application
  * Bean is singleton by default
* Prototype : new/different object whenever you ask for it
* Request : for getting new object each and every time new request enters the app
* Session : for one session
* Global Session : for life-cycle for global session

#### Bean Life-cycle

* Definition of beans
* instantiation
* populate property, constructor
* init method runs
* dependency injection
* pre destroy step
* destruction

### What is Application Context ?

* When we create spring bean, we need something to manage it.
* Application Context is there to&#x20;
  * instantiate
  * configure&#x20;
  * assemble
* Container for all beans

### Why dependency injection is done through constructors ?

* It gets difficult to keep track of objects that are passed at time of initialisation. There can be multiple dependency for an class, and those dependency might also dependent upon others.
* It gets difficult to manage the object life-cycles.

### Inspecting Beans managed for us by Spring boot

In main method

```java
ConfigurableApplicationContext app = 
                SpringApplication.run(SpringTokApplication.class, args);

Arrays.stream(app.getBeanDefinitionNames()).forEach(System.out::println);
```

* this will list all beans managed for us by spring boot. When we add the annotation of `@RestController` or `@Repository` , they implement the @Component annotation which indicates the framework that you have to manage this bean according to rules

### @Bean annotation on methods ?

Yes, bean still stands for object, but spring boot has a annotation for methods which for spring to manage it just like is manage other beans

### Types of dependency Injection&#x20;

3 ways to get dependency into a class&#x20;

* Constructor Injection : Best injection method
* Setter Injection : makes code too verbose
* Field Injection : against java convention, as outside entity is accessing private field, except for test-cases

**Constructor Injection**

```java
    private final VideoRepository videoRepository;

    @Autowired
    public VideoController(VideoRepository videoRepository) {
        this.videoRepository = videoRepository;
    }
```

**Field Injection**

```java
    @Autowired
    private VideoRepository videoRepository;
```

**Setter Injection**

```java
    private VideoRepository videoRepository;
    
    @Autowired
    public void setVideoRepository(VideoRepository videoRepository) {
        this.videoRepository = videoRepository;
    }
```
