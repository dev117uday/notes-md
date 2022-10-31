---
description: Get set Go
---

# Set in Java

![Class Diagram](<../../.gitbook/assets/image (5) (1).png>)

**import**

```java
import java.util.Set;
import java.util.HashSet;
```

## Set

Set have its implementation in various classes like `HashSet` , `TreeSet` , `LinkedHashSet` .

```java
// Hashset Random Sorting
Set<T> set = new HashSet<T>();

// TreeSet - By compareTo() or Comparator
TreeSet<T> sortedSet = new TreeSet<T>();

// LinkedHashSet - Insertion Order
LinkedHashSet<T> linkedhashset = new LinkedHashSet<T>();
```

### Creating a set

```java
Set<Integer> set = new HashSet<Integer>();
// Creates an empty Set of Integers

Set<Integer> linkedHashSet = new LinkedHashSet<Integer>(); 
//Creates a empty Set of Integers, with predictable iteration order
```

### Adding elements to a Set

```
set.add(12); 
set.add(13);
```

### Delete all the elements of a Set

```java
set.clear();
//Removes all objects from the collection.

set.remove(0); 
// Removes first occurrence of a specified object from the collection
```

### Check size

```
set.size(); 
//Returns the number of elements in the collection

set.isEmpty();
//Returns true if the set has no elements
```
