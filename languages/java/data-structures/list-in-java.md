---
description: Just like shopping list
---

# List in Java

![Class Diagram \(click to zoom\)](../../../.gitbook/assets/image%20%284%29.png)

[read more here](https://docs.oracle.com/javase/8/docs/api/java/util/List.html)

**imports**

```java
import java.util.List;
import java.util.ArrayList;
```

## Array List

Array List is one of the inbuilt data structures in Java. It is a dynamic array \(where the size of the data structure not needed to be declared first\) for storing elements \(Objects\).

### Creating a List

```java
List<String> strings;
List<Double> doubles;
```

If you try to add something to the lists above you will get a `NullPointerException`, because strings and doubles, both equal **null!**

```java
List<T> myArrayList = new ArrayList<>();
List<T> myLinkedList = new LinkedList<>();
```

### Positional Access Operations

```text
add(T type)
add(int index, T type)
remove(Object o)
remove(int index)
get(int index)
set(int index, E element)
int indexOf(Object o)
int lastIndexOf(Object o)
```

### Iterating over the List

```java
public void printEachElement(List<String> list){
    for(String s : list){
        System.out.println(s);
    }
}
```

### To add an element

```java
myArrayList.add(element);
myArrayList.add(index, element); 
//index of the element should be an int (starting from 0)
```

### To remove

```java
myArrayList.remove(element);
myArrayList.remove(index); 
//index of the element should be an int (starting from 0)
```

* Removing elements from list B that are present in the list A

```java
numbersB.removeAll(numbersA);
    System.out.println("B cleared: " + numbersB);
```

