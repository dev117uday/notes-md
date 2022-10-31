---
description: Important things to know
---

# Data & Data Types

## Constants

```java
final int someConstant = 10;
```

## Data Types

![Data types in Java](<../.gitbook/assets/image (1) (1).png>)

* These are Java's primitive datatypes
* you can use `+` operator on datatypes smaller than int otherwise anything that gets promoted to `Integer`.
* To get max and min value of data type : &#x20;

```java
int high = Integer.MAX_VALUE;
int low = Integer.MIN_VALUE;
```

## Strings

### Important functions

* `equalsIgnoreCase`
* `toLowerCase`
* To check Strings in Java don't use "==" instead use :&#x20;
  * `str1.equals(str2)`
* `charAt(0)`
* `String.contains()`
* `s.indexOf('i')`
* `split(";")`
* `join()`
* `toString()`  Dont use with strings
* **String** is a final and **immutable** class
* To **create** a **mutable string** in **java**, **Java** has two **classes**&#x20;
  * StringBuffer and&#x20;
  * **StringBuilder**

```java
String s = "this is an example";
String a = s.substring(11); 
// a will hold the string starting at character 11 
// until the end ("example")
```

```java
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

![Strings on Heap vs Pool](<../.gitbook/assets/image (2) (1).png>)

### String intern()

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

## Big Decimal

**imports :**

```java
import java.math.BigDecimal;
import java.math.BigInteger;
```

### Big Decimal objects are immutable

```java
BigDecimal a = new BigDecimal("42.23");
BigDecimal b = new BigDecimal("10.001");
a.add(b); // a will still be 42.23
BigDecimal c = a.add(b); // c will be 52.231
```

### Creating Big Decimals

```java
BigDecimal a = new BigDecimal(5);
```

### Comparing

```java
a.compareTo(new BigDecimal(0));
// a is greater, returns 1
a.compareTo(new BigDecimal(5));
// a is equal, returns 0
a.compareTo(new BigDecimal(10));
// a is less, returns -1
```

### Operations

```java
Addition: add() method
Subtraction: subtract() method
Multiplication: multiply() method
Division: divide() method
```

```java
BigDecimal a = new BigDecimal("5");
BigDecimal b = new BigDecimal("7");

//Equivalent to result = a + b
BigDecimal result = a.add(b);

//Equivalent to result = a - b
BigDecimal result = a.subtract(b);

//Equivalent to result = a * b
BigDecimal result = a.multiply(b);

//Equivalent to result = a / b
BigDecimal result = a.divide(b);

//Equivalent to result = a % b
BigDecimal result = a.remainder(b);

//Equivalent to result = a^10
BigDecimal result = a.pow(10);

//Equivalent to result = MAX(a,b)
BigDecimal result = a.max(b);

//Equivalent to result = MIN(a,b)
BigDecimal result = a.min(b);

BigDecimal a = new BigDecimal("5234.49843776");
// Moves the decimal point to 2 places left of 
// current position
BigDecimal result = a.movePointLeft(2);
// Result : 52.3449843776

BigDecimal a = new BigDecimal("5234.49843776");
// Moves the decimal point to 3 places right of 
// current position
BigDecimal result = a.movePointRight(3);
System.out.println(result);
// Result : 5234498.43776
```

### String.Format

```java
BigDecimal accountBalance = new BigDecimal("10000.00");
System.out.println(String.format("Account balance : %f",
accountBalance));
```

### Best Practises

```java
//Bad example:
BigDecimal bad0 = new BigDecimal(0);
BigDecimal bad1 = new BigDecimal(1);
BigDecimal bad10 = new BigDecimal(10);

//Good Example:
BigDecimal good0 = BigDecimal.ZERO;
BigDecimal good1 = BigDecimal.ONE;
BigDecimal good10 = BigDecimal.TEN;
```

## Big Integer

### Initialisation

```java
BigInteger value1 = new BigInteger("10");
BigInteger value2 = new BigInteger("10");
```

* To convert long or int values to Big Integer use:

```java
long longValue = Long.MAX_VALUE;
BigInteger valueFromLong = BigInteger.valueOf(longValue);
```

* To convert a numeric String to Big Integer use:

```java
String decimalString = "-1";
BigInteger valueFromDecimalString = 
    new BigInteger(decimalString);
```

* There are predefined constants for common values:
* `BigInteger.ZERO` — value of "0".&#x20;
* `BigInteger.ONE` — value of "1".
* `BigInteger.TEN` — value of "10".

### Operations

```java
BigInteger value1 = new BigInteger("10");
BigInteger value2 = new BigInteger("10");

BigInteger sum = value1.add(value2);
BigInteger sub = value1.subtract(value2);
BigInteger div = value1.divide(value2);
BigInteger mul = value1.multiply(value2);

BigInteger value1 = new BigInteger("10");
BigInteger power = value1.pow(3);

BigInteger power = value1.remainder(value2);

System.out.println(value1.gcd(value2));
System.out.println(value1.max(value2));

System.out.println(value1.min(value2));
```

### Comparing

```java
BigInteger one = BigInteger.valueOf(1);
BigInteger two = BigInteger.valueOf(2);

if(one.equals(two)){
    System.out.println("Equal");
}
else{
    System.out.println("Not Equal");
}
```

In general, do not use use the == operator to compare Big Integers

* `==` operator: compares references; i.e. whether two values refer to the same object&#x20;
* `equals()` method: compares the content of two Big Integers.

```java
BigInteger reallyBig = BigInteger.valueOf(10);
BigInteger reallyBig1 = BigInteger.valueOf(100);

if(reallyBig.compareTo(reallyBig1) == 0){
    //code when both are equal.
}
```
