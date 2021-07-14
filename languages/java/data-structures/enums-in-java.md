---
description: 'They are weird, literally'
---

# Enums in Java

## Basics

### Declaring Enums

```java
public enum Season {
    WINTER,
    SPRING,
    SUMMER,
    FALL
}
```

You can also declare them inside another class. You cannot declare an Enum inside a method body or constructor. It cannot have duplicate values

### Usage

```java
class Main {
    public enum Season {
        WINTER, SPRING, SUMMER, FALL
    }

    public static void main(String[] args) {
        System.out.println("-------");
        display(Season.WINTER);
        System.out.println("-------");
        enumIterate();
        System.out.println("-------");
        enumSwitchExample(Season.SUMMER);
        System.out.println(Season.FALL == Season.WINTER);
        System.out.println(Season.SPRING == Season.SPRING);
        System.out.println("-------");
    }

    public static void display(Season s) {
        System.out.println(s.name());
    }

    public static void enumIterate() {
        for (Season s : Season.values()) {
            System.out.println(s.name());
        }
    }

    public static void enumSwitchExample(Season s) {
        switch (s) {
            case WINTER:
                System.out.println("It's pretty cold");
                break;
            case SPRING:
                System.out.println("It's warming up");
                break;
            case SUMMER:
                System.out.println("It's pretty hot");
                break;
            case FALL:
                System.out.println("It's cooling down");
                break;
        }
    }
}
```

### Enums with methods

```java
public enum MutableExample {
    A, B;

    private int count = 0;

    public void increment() {
        count++;
    }

    public void print() {
        System.out.println("The count of " + name() + 
            " is " + count);
    }
}
```

```java
class Main {
    public static void main(String[] args) {
        MutableExample a = MutableExample.A;
        a.increment();
        a.print();
        MutableExample b = MutableExample.B;
        b.print();
    }
}
```

Enum constants are technically mutable, so a setter could be added to change the internal structure of an enum constant. However, this is considered very bad practice and should be avoided. Best practice is to make

Enum fields immutable, with final :

```text
public enum Coin {
    PENNY(1), NICKEL(5), DIME(10), QUARTER(25);
    private final int value;
    Coin(int value){
        this.value = value;
    }
    ...
}
```

### EnumMap

```java
import java.util.*;

class Book {
    int id;
    String name, author, publisher;
    int quantity;

    public Book(int id, String name, String author, String publisher, int quantity) {
        this.id = id;
        this.name = name;
        this.author = author;
        this.publisher = publisher;
        this.quantity = quantity;
    }
}

public class Main {
    public static void main(String[] args) {
        EnumMap<Key, Book> map = new EnumMap<Key, Book>(Key.class);

        Book b1 = new Book(101, "Book 1", "Author 1", "P 1", 8);
        Book b2 = new Book(102, "Book 2", "Author 2", "p 2", 4);
        Book b3 = new Book(103, "Book 3", "Author", "p4", 6);

        map.put(Key.One, b1);
        map.put(Key.Two, b2);
        map.put(Key.Three, b3);

        for (Map.Entry<Key, Book> entry : map.entrySet()) {
            Book b = entry.getValue();
            System.out.println(b.id + " " + b.name + " " + b.author + " " + b.publisher + " " + b.quantity);
        }
    }

    public enum Key {
        One, Two, Three
    }
}
```

### EnumSet

```java
import java.util.*;

enum days {
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY
}

public class Main {
    public static void main(String[] args) {
        Set<days> set = EnumSet.of(days.TUESDAY, days.WEDNESDAY);
// Traversing elements
        Iterator<days> iter = set.iterator();
        while (iter.hasNext())
            System.out.println(iter.next());
    }
}
```

### Enum starting with number

Java does not allow the name of enum to start with number like 100A, 25K. In that case, we can append the code with \_ \(underscore\) or any allowed pattern and make check of it.

**Enum get very complicated**

