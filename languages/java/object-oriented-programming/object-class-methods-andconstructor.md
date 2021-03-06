# Object Class Methods and Constructor

## hashCode\(\) method

The general contract of `hashCode` is:

* Whenever it is invoked on the same object more than once during an execution of a Java application, the `hashCode` method must consistently return the same integer, provided no information used in `equals` comparisons on the object is modified. This integer need not remain consistent from one execution of an application to another execution of the same application.
* If two objects are equal according to the `equals(Object)` method, then calling the `hashCode` method on each of the two objects must produce the same integer result.
* It is _not_ required that if two objects are unequal according to the [`equals(java.lang.Object)`](https://docs.oracle.com/javase/7/docs/api/java/lang/Object.html#equals%28java.lang.Object%29) method, then calling the `hashCode` method on each of the two objects must produce distinct integer results. However, the programmer should be aware that producing distinct integer results for unequal objects may improve the performance of hash tables.

## equals\(\) method

```java
public class Foo {
    int field1, field2;
    String field3;

    public Foo(int i, int j, String k) {
        field1 = i;
        field2 = j;
        field3 = k;
    }

    public static void main(String[] args) {
        Foo foo1 = new Foo(0, 0, "bar");
        Foo foo2 = new Foo(0, 0, "bar");
        System.out.println(foo1.equals(foo2)); // prints false
    }
}
```

Even though foo1 and foo2 are created with the same fields, they are pointing to two different objects in memory. The default `equals()` implementation therefore evaluates to `false`.

```java
public class Foo {
    int field1, field2;
    String field3;

    public Foo(int i, int j, String k) {
        field1 = i;
        field2 = j;
        field3 = k;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) {
            return true;
        }
        if (obj == null || getClass() != obj.getClass()) {
            return false;
        }
        Foo f = (Foo) obj;
        return field1 == f.field1 && field2 == f.field2
                && (field3 == null ? f.field3 == null : field3.equals(f.field3));
    }

    public static void main(String[] args) {
        Foo foo1 = new Foo(0, 0, "bar");
        Foo foo2 = new Foo(0, 0, "bar");
        System.out.println(foo1.equals(foo2)); // prints true
    }
}
```

## getClass\(\) method

```java
class hello {
    int number;
}
class Program {
    public static void main(String[] args) {
        hello obj = new hello();
        System.out.println(obj.getClass());
    }
}
// prints "class hello"
```

## clone\(\) method

The `clone()` method is used to create and return a copy of an object. This method arguable should be avoided as it is problematic and a copy constructor or some other approach for copying should be used in favour of `clone()`

For the method to be used all classes calling the method must implement the `Cloneable` interface.

The Cloneable interface itself is just a tag interface used to change the behaviour of the native `clone()` method which checks if the calling objects class implements Cloneable . If the caller does not implement this interface a `CloneNotSupportedException` will be thrown. The Object class itself does not implement this interface so a `CloneNotSupportedException` will be thrown if the calling object is of class Object .

```java
// A Java program to demonstrate shallow copy 
// using clone() 
import java.util.ArrayList; 

// An object reference of this class is 
// contained by Test2 
class Test 
{ 
    int x, y; 
} 

// Contains a reference of Test and implements 
// clone with shallow copy. 
class Test2 implements Cloneable 
{ 
    int a; 
    int b; 
    Test c = new Test(); 
    public Object clone() throws
                CloneNotSupportedException 
    { 
        return super.clone(); 
    } 
} 

// Driver class 
public class Main 
{ 
    public static void main(String args[]) throws
                        CloneNotSupportedException 
    { 
    Test2 t1 = new Test2(); 
    t1.a = 10; 
    t1.b = 20; 
    t1.c.x = 30; 
    t1.c.y = 40; 

    Test2 t2 = (Test2)t1.clone(); 

    // Creating a copy of object t1 and passing 
    // it to t2 
    t2.a = 100; 

    // Change in primitive type of t2 will not 
    // be reflected in t1 field 
    t2.c.x = 300; 

    // Change in object type field will be 
    // reflected in both t2 and t1(shallow copy) 
    System.out.println(t1.a + " " + t1.b + " " + 
                        t1.c.x + " " + t1.c.y); 
    System.out.println(t2.a + " " + t2.b + " " + 
                        t2.c.x + " " + t2.c.y); 
    } 
}
```

 

