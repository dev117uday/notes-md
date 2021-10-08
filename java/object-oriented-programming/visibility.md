---
description: controlling access to members of a class
---

# Visibility

## Private Visibility

private visibility allows a variable to only be accessed by its class. They are often used in conjunction with public getters and setters.

```java
class SomeClass {
    private int variable;

    public int getVariable() {
        return variable;
    }

    public void setVariable(int variable) {
        this.variable = variable;
    }
}

public class SomeOtherClass {
    public static void main(String[] args) {
        SomeClass sc = new SomeClass();
        // These statement won't compile because SomeClass#variable is private:
        sc.variable = 7;
        System.out.println(sc.variable);
        // Instead, you should use the public getter and setter:
        sc.setVariable(7);
        System.out.println(sc.getVariable());
    }
}
```

## Protected Visibility

Protected visibility causes means that this member is visible to its package, along with any of its subclasses.

```java
package com.stackexchange.docs;

public class MyClass {
    protected int variable; // This is the variable that we are trying to access

    public MyClass() {
        variable = 2;
    };
}
```

## Public Visibility

Visible to the class, package, and subclass

```java
public class Test{
    public int number = 2;
        public Test(){
    }
}

public class Other{
    public static void main(String[] args){
        Test t = new Test();
        System.out.println(t.number);
    }
}
```

