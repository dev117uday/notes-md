---
description: 'Aspect Oriented Programming : to avoid cross cutting concerns'
---

# Spring A.O.P

**AOP is a programming paradigm that aims to increase modularity by allowing the separation of cross-cutting concerns.** It does this by adding additional behaviour to existing code without modifying the code itself.

What are cross cutting concerns

* let's say you want to log a message or perform execution on certain functionality like authentication before the execution of methods of same class, instead of declaring the functionality again and again for each methods.

#### Example

```java
// dependencies

<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjrt</artifactId>
    <version>1.9.19</version>
</dependency>

<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjweaver</artifactId>
    <version>1.9.19</version>
</dependency>

// definition

public void checkout(String status) {
    System.out.println("checkout method of shopping cart called");
}

public int quantity() {
    return 2;
}

// call

ShoppingCart cart = context.getBean(ShoppingCart.class);
cart.checkout("cancelled");

// aspectj config

@Configuration
@ComponentScan(basePackages = "demo")
@EnableAspectJAutoProxy
public class BeanConfig {
}

// another class

@Aspect
@Component
public class LoggingAspect {

    // logging will not match if parameters not match
    // to match add .. in brackets

    // before execution
    @Before("execution(* demo.ShoppingCart.checkout(..))")
    public void beforeLogger(JoinPoint jp) {
        System.out.println(jp.getSignature());
        String arg = jp.getArgs()[0].toString();
        System.out.println("Before Loggers " + arg);
    }

    // after execution
    @After("execution(* *.*.checkout(..))")
    public void afterLogger() {
        System.out.println("After Loggers");
    }

    @Pointcut("execution(* demo.ShoppingCart.quantity(..))")
    public void afterReturningPointCut() {
    }

    @AfterReturning(pointcut = "afterReturningPointCut()", returning = "retVal")
    public void afterReturning(String retVal) {
        System.out.println("after returning " + retVal);
    }

}

@Aspect
@Component
public class AuthenticationAspect {

    @Pointcut("within(demo..*)")
    public void authenticatingPointCut() {
    }

    @Pointcut("within(demo..*)")
    public void authorizingPointCut() {
    }

    @Before("authenticatingPointCut() || authorizingPointCut()")
    public void authenticate() {
        System.out.println("authenticating the request");
    }
}


```

