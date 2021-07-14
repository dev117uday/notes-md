---
description: builders
---

# Constructors

## Default Constructor

```java
public class TestClass {
    private String test;

    public TestClass() {
    }
}
```

The "default" for constructors is that they do not have any arguments.The visibility of the default constructor is the same as the visibility of the class. Thus a class defined package- privately has a package-private default constructor

## Normal Constructor

```java
public class TestClass {
    private String test;
    public TestClass() {
    }
    public TestClass(String arg) {
    }
}
```

You can have more than one constructor

```java
class Parent {
    private String name;
    private int age;

    public Parent() {
    } // necessary because we call super() without arguments

    public Parent(String tName, int tAge) {
        name = tName;
        age = tAge;
    }

    public void printer() {
        System.out.println("Name : " + this.name + " Age : " + this.age);
    }
}

// This does not even compile, because name and age are private,
// making them invisible even to the child class.
class Child extends Parent {
    public Child() {
        super("uday2", 10);
    }
}

class Main {
    public static void main(String[] args) {
        Parent p = new Parent("uday", 42);
        Child c = new Child();
        p.printer();
        c.printer();
    }
}
```

