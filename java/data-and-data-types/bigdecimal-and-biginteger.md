---
description: They are BIG
---

# BigDecimal and BigInteger

**imports :**

```java
import java.math.BigDecimal;
import java.math.BigInteger;
```

## Big Decimal

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
* `BigInteger.ZERO` — value of "0". 
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

* `==` operator: compares references; i.e. whether two values refer to the same object 
* `equals()` method: compares the content of two Big Integers.

```java
BigInteger reallyBig = BigInteger.valueOf(10);
BigInteger reallyBig1 = BigInteger.valueOf(100);

if(reallyBig.compareTo(reallyBig1) == 0){
    //code when both are equal.
}
```

