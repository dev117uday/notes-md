---
description: Easy to difficult
---

# Array in Java

## Array 101

```java
float array[]; /* and */ int foo()[] { ... } /* are discouraged */
float[] array; /* and */ int[] foo() { ... } /* are encouraged */
```

To find the length of array, just use : `arr.length;`

**ArrayType** : Type of the array. This can be primitive \( `int` , `long` , `byte` \) or Objects \( `String` , `MyObject` , etc\).

```java
int numbers = new int[3];
int numbers = { 1, 2, 3 };
int numbers = new int[] { 1, 2, 3 };
int[][] number = { { 1, 2 }, { 3, 4, 5 } };
int[][] number = new int[5][];
int[][] number = new int[5][5];

float[] boats = new float[5];
String[] theory = new String[] { "a", "b", "c" };
Object[] dArt = new Object[] { new Object(), 
    "We love Stack", new Integer(3) };
```

### Copying Array

```java
int[] a = { 4, 1, 3, 2 };
int[] b = a.clone(); 
// [4, 1, 3, 2]

int[] a = {4, 1, 3, 2};
int[] b = Arrays.copyOf(a, a.length); 
// [4, 1, 3, 2]

int[] a = { 4, 1, 3, 2 };
int[] b = new int[a.length];
System.arraycopy(a, 0, b, 0, a.length); 
// [4, 1, 3, 2]
```

## What is List

List is an interface, and the instances of List can be created by implementing various classes

```java
Integer[] initial = { 127, Integer.valueOf( 42 ) };
List toList = Arrays.asList( initial ); 
// Fixed size!

// Note: Works with all collections
Integer[] fromCollection = toList.toArray( 
    new Integer[toList.size()] );
```

```java
int[] array = new int[5];
Arrays.setAll(array, i -> i); 
// The array becomes { 0, 1, 2, 3, 4 }.
```

### Creating a List from an Array

```java
String[] stringArray = {"foo", "bar", "baz"};
List<String> stringList = Arrays.asList(stringArray);
```

## ArrayIndex Out Of Bounds Exception

```java
String[] people = new String[] { "Carol", "Andy" };

// An array will be created:
// people[0]: "Carol"
// people[1]: "Andy"
// Notice: no item on index 2. 
// Trying to access it triggers the exception:

System.out.println(people[2]); 
// throws an ArrayIndexOutOfBoundsException.
```

## Arrays to Stream

```java
String[] arr = new String[] {"str1", "str2", "str3"};
Stream<String> stream = Arrays.stream(arr);

int[] intArr = {1, 2, 3};
IntStream intStream = Arrays.stream(intArr);

Stream<Integer> intStream = Stream.of(1, 2, 3);
Stream<String> stringStream = Stream.of("1", "2", "3");
Stream<Double> doubleStream = Stream.of(
        new Double[]{1.0, 2.0});
```

## Array to String

```java
int[] arr = {1, 2, 3, 4, 5};
System.out.println(Arrays.toString(arr));

// [1, 2, 3, 4, 5]
```

```java
int[][] arr = {
{1, 2, 3},
{4, 5, 6},
{7, 8, 9}
};
System.out.println(Arrays.deepToString(arr));

// [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

## Sorting Arrays

```java
String[] names = {"John", "Steve", "Shane", "Adam", "Ben"};

// increasing order
Arrays.sort(names);

// decreasing order
Arrays.sort(names, 0, names.length, 
        Collections.reverseOrder());
```

## Common Array functions Java

```java
String[] strings = new String[] { "A", "B", "C" };
int[] ints = new int[] { 1, 2, 3, 4 };

// Using Arrays.binarySearch (for sorted arrays only)
int index = Arrays.binarySearch(strings, "A");
int index2 = Arrays.binarySearch(ints, 1);

// Using a Arrays.asList (for non-primitive arrays only)
int index = Arrays.asList(strings).indexOf("A");
int index2 = Arrays.asList(ints).indexOf(1);

// Using Stream
int index = IntStream.range(0, strings.length)
.filter(i -> "A".equals(strings[i]))
.findFirst()
.orElse(-1);
```

## How do you change the size of an array?

```java
String[] listOfCities = new String[3];
listOfCities[0] = "New York";
listOfCities[1] = "London";
listOfCities[2] = "Berlin";


String[] newArray = Arrays.copyOf(listOfCities, 
        listOfCities.length + 1);
newArray[listOfCities.length] = "Sydney";
```

## Remove an element from an array

### Using ArrayList

```java
String[] array = new String[]{"foo", "bar", "baz"};
List<String> list = new ArrayList<>(Arrays.asList(array));
list.remove("foo");

// Creates a new array with the same size 
// as the list and copies the list
// elements to it.

array = list.toArray(new String[list.size()]);
System.out.println(Arrays.toString(array)); 
//[bar, baz]
```

### Using arraycopy

```java
int[] array = new int[] { 1, 2, 3, 4 }; 
// Original array.
int[] result = new int[array.length - 1]; 
// Array which will contain the result.
int index = 1; 
// Remove the value "2".

// Copy the elements at the left of the index.
System.arraycopy(array, 0, result, 0, index);
// Copy the elements at the right of the index.
System.arraycopy(array, index + 1, result, 
        index, array.length - index - 1);
System.out.println(Arrays.toString(result)); //[1, 3, 4]
```

## Comparing arrays for equality

```java
int[] a = new int[]{1, 2, 3};
int[] b = new int[]{1, 2, 3};
System.out.println(a.equals(b)); 
// prints "false" because a and b refer 
// to different objects
System.out.println(Arrays.equals(a, b)); 
// prints "true" because the elements of a and b 
// have the same values
```

```java
int a[] = { 1, 2, 3 };
int b[] = { 1, 2, 3 };

Object[] aObject = { a }; 
// aObject contains one element
Object[] bObject = { b }; 
// bObject contains one element

System.out.println(Arrays.equals(aObject, bObject)); 
// false
System.out.println(Arrays.deepEquals(aObject, bObject));
// true
```

