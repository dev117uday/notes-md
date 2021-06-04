# Immutable Class & Objects

## Immutable Class

```java
public final class Color {
    final private int red;
    final private int green;
    final private int blue;

    private void check(int red, int green, int blue) {
        if (red < 0 || red > 255 || green < 0 || green > 255 || blue < 0 || blue > 255) {
            throw new IllegalArgumentException();
        }
    }

    public Color(int red, int green, int blue) {
        check(red, green, blue);
        this.red = red;
        this.green = green;
        this.blue = blue;
    }

    public Color invert() {
        return new Color(255 - red, 255 - green, 255 - blue);
    }
}
```

## What is the advantage of immutability?

The advantage of immutability comes with concurrency. It is difficult to maintain correctness in mutable objects, as multiple threads could be trying to change the state of the same object, leading to some threads seeing a different state of the same object, depending on the timing of the reads and writes to the said object.

By having an immutable object, one can ensure that all threads that are looking at the object will be seeing the same state, as the state of an immutable object will not change.

## Rules to define immutable classes

The following rules define a simple strategy for creating immutable objects.

* Don't provide "setter" methods - methods that modify fields or objects referred to by fields. 
* Make all fields final and private.
* Don't allow subclasses to override methods. The simplest way to do this is to declare the class as final. A more sophisticated approach is to make the constructor private and construct instances in factory methods.
* If the instance fields include references to mutable objects, don't allow those objects to be changed.
* Don't provide methods that modify the mutable objects.
* Don't share references to the mutable objects. Never store references to external, mutable objects passed to the constructor; if necessary, create copies, and store references to the copies. Similarly, create copies of your internal mutable objects when necessary to avoid returning the originals in your methods.

## Immutable Object

An immutable object is an object whose state cannot be changed. An immutable class is a class whose instances are immutable by design, and implementation.

The standard recipe for an immutable class is as follows:

* All properties must be set in the constructor\(s\) or factory method\(s\). 
* There should be no setters. If it is necessary to include setters for interface compatibility reasons, they should either do nothing or throw an exception. 
* All properties should be declared as private and final.
* For all properties that are references to mutable types: the property should be initialized with a deep copy of the value passed via the constructor, and the property's getter should return a deep copy of the property value. 
* The class should be declared as final to prevent someone creating a mutable subclass of an immutable class. 

A couple of other things to note:

* Immutability does not prevent object from being nullable; e.g. null can be assigned to a String variable. 
* If an immutable classes properties are declared as final , instances are inherently thread-safe. This makes immutable classes a good building block for implementing multi-threaded applications.

