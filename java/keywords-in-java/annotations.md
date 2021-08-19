---
description: Just another thing to confuse you
---

# Annotations

_An annotation is a marker which associates information with a program construct, but has no effect at run time._

Annotations may appear before types or declarations. It is possible for them to appear in a place where they could apply to both a type or a declaration. What exactly an annotation applies to is governed by the "meta-annotation" `@Target` . See "Defining annotation types" for more information.

### Defining annotation types

```java
@interface MyAnnotation {
    String param1();
    boolean param2();
    int[] param3(); // array parameter
}
```

**Default Values**

```java
@interface MyAnnotation {
    String param1() default "someValue";
    boolean param2() default true;
    int[] param3() default {};
}
```

## @Override

```java
public class Vehicle {
    public void drive() {
        System.out.println("I am driving");
    }
}

class Car extends Vehicle {
    // Fine
    @Override
    public void drive() {
        System.out.prinln("Brrrm, brrm");
    }
}

// Abstract Classes
abstract class Animal {
    public abstract void makeNoise();
}

class Dog extends Animal {
    // Fine
    @Override
    public void makeNoise() {
        System.out.prinln("Woof");
    }
}

// this will throw an error
class Logger1 {
    public void log(String logString) {
        System.out.prinln(logString);
    }
}

class Logger2 {
    // This will throw compile-time error. Logger2 is not a subclass of Logger1.
    // log method is not overriding anything
    @Override
    public void log(String logString) {
        System.out.println("Log 2" + logString);
    }
}
```

