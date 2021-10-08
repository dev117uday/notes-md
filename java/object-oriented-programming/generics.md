# Generics

**Generics** are a facility of generic programming that extend Java's type system to allow a type or method to operate on objects of various types while providing compile-time type safety. In particular, the Java collections framework supports generics to specify the type of objects stored in a collection instance

```java
class Param<T> {
    private T value;

    public T getValue() {
        return value;
    }

    public void setValue(T value) {
        this.value = value;
    }
}

public class Program {

    public static void main(String[] args) {
        Param<Integer> parInt = new Param<Integer>();
        Param<String> parStr = new Param<String>();

        parInt.setValue(10);
        parStr.setValue("uday yadav");

        System.out.println("Int : " + parInt.getValue());
        System.out.println("Str : " + parStr.getValue());

    }
}
```

