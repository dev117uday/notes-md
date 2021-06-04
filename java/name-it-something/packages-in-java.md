---
description: like namespaces ?
---

# Packages in Java

```java
import package.name.Class;   // Import a single class
import package.name.*;   // Import the whole package
```

## Import a Class

```java
import java.util.Scanner;
import java.util.*;
```

## User-defined Packages

```java
//save by A.java  
package pack;

public class A {
    public void msg() {
        System.out.println("Hello");
    }
}
```

```java
//save by B.java  
package mypack;

import pack.*;

class B {
    public static void main(String args[]) {
        A obj = new A();
        obj.msg();
    }
}
```

