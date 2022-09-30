# Singleton DP

* Creational Design Pattern
* Only one instance of the class should exist

**Example : Eager Initialization**

```java
public class Singleton {

    private static Singleton instance = new Singleton();

    private Singleton() {
    }

    public static Singleton getObject() {
        return instance;
    }

}
```

**Example : Lazy initialization**

```java
public class Singleton {

    private static Singleton instance = null;
    
    private Singleton() {}
    
    public static Singleton getObject(){ 
        if(instance == null) { 
            instance = new Singleton();  
        }  
        return instance;  
    } 

}
```
