---
description: Important things to know
---

# Data & Data Types

## Constants

```java
final int someConstant = 10;
```

## Data Types

![Data types in Java](../../.gitbook/assets/image%20%281%29.png)

* These are Java's primitive datatypes
* you can use `+` operator on datatypes smaller than int otherwise anything that gets promoted to `Integer`.
* To get max and min value of data type :  

```text
int high = Integer.MAX_VALUE;
int low = Integer.MIN_VALUE;
```

## Strings

### Important functions

* `equalsIgnoreCase`
* `toLowerCase`
* To check Strings in Java don't use "==" instead use : 
  * `str1.equals(str2)`
* `charAt(0)`
* `String.contains()`
* `s.indexOf('i')`
* `split(";")`
* `join()`
* `toString()`  Dont use with strings
* **String** is a final and **immutable** class
* To **create** a **mutable string** in **java**, **Java** has two **classes** 
  * StringBuffer and 
  * **StringBuilder**
* ```text
  String s = "this is an example";
  String a = s.substring(11); 
  // a will hold the string starting at character 11 
  // until the end ("example")
  ```
* ```text
  String s = "popcorn";
  System.out.println(s.replace('p','W'));
  ```

### String Builder

```java
StringBuilder sb = new StringBuilder();

sb.append("One=").append(one).append(", Color=red")

System.out.print(sb);

// Prints "One=1, Colour=red" 
// followed by an ASCII newline.
String result = sb.toString();
```

### Formatter

```java
int one = 1;
String color = "red";
Formatter f = new Formatter();
System.out.print(f.format("One=%d, colour=%s%n",
        one, color));
// Prints "One=1, Colour=red" 
// followed by the platform's line separator
```

### String Joiner

```java
StringJoiner sj = new StringJoiner(", ", "[", "]");
for (String s : new String[]{"A", "B", "C"}) {
    sj.add(s);
}
System.out.println(sj);
// Prints "[A, B, C]"
```

### String Tokenizer

```java
import java.util.StringTokenizer;
    public class Simple{
    public static void main(String args[]){
        StringTokenizer st = 
            new StringTokenizer("apple ball cat dog"," ");
        while (st.hasMoreTokens()) {
            System.out.println(st.nextToken());
        }
    }
}
```

### Strings on Heap & Pool

* created on heap, even literals

**Difference between string on heap and Pool**

![Strings on Heap vs Pool](../../.gitbook/assets/image%20%282%29.png)

### String intern\(\)

```java
public class InternExample{  
    public static void main(String args[]){  
        String s1=new String("hello");  
        String s2="hello";  
        String s3=s1.intern();
        // returns string from pool, 
        // now it will be same as s2  
        System.out.println(s1==s2);
        // false because reference variables are 
        // pointing to different instance  
        System.out.println(s2==s3);
        // true because reference variables are 
        // pointing to same instance  
    }
}
```

