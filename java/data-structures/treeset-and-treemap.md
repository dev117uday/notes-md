---
description: Plant a tree everywhere
---

# TreeSet and TreeMap

## TreeMap

### Initialize

```java
TreeMap<Integer, String> treeMap = new TreeMap<>();

treeMap.put(10, "ten");
treeMap.put(4, "four");
treeMap.put(1, "one");
treeSet.put(12, "twelve");
```

```java
System.out.println(treeMap.firstEntry()); 
// Prints 1=one
System.out.println(treeMap.lastEntry()); 
// Prints 12=twelve
System.out.println(treeMap.size()); 
// Prints 4, since there are 4 elemens in the map
System.out.println(treeMap.get(12)); 
// Prints twelve
System.out.println(treeMap.get(15)); 
// Prints null, since the key is not found in the map
```

### Iteration

```java
for (Entry<Integer, String> entry : treeMap.entrySet()) {
    System.out.print(entry + " "); //prints 1=one 4=four 10=ten 12=twelve
}

Iterator<Entry<Integer, String>> iter = treeMap.entrySet().iterator();
while (iter.hasNext()) {
    System.out.print(iter.next() + " "); //prints 1=one 4=four 10=ten 12=twelve
}
```

## TreeSet

### Initialization

```java
TreeSet treeSet = new TreeSet<>();

treeSet.add(10);
treeSet.add(4);
treeSet.add(1);
```

```java
System.out.println(treeSet.first()); 
// Prints 1
System.out.println(treeSet.last()); 
// Prints 12
System.out.println(treeSet.size()); 
// Prints 4, since there are 4 elemens in the set
System.out.println(treeSet.contains(12)); 
// Prints true
System.out.println(treeSet.contains(15)); 
// Prints false
```

### Iteration

```java
for (Integer i : treeSet) {
    System.out.print(i + " "); //prints 1 4 10 12
}

Iterator<Integer> iter = treeSet.iterator();
while (iter.hasNext()) {
    System.out.print(iter.next() + " "); //prints 1 4 10 12
}
```

## TreeMap/TreeSet of a custom Java type

Since `TreeMap` and `TreeSet` s maintain keys/elements according to their natural ordering. Therefor `TreeMap` keys and `TreeSet` elements have to comparable to one another. you will run into the following error

```text
Exception in thread "main" java.lang.ClassCastException: Person cannot be cast to
java.lang.Comparable
```

* One solution is to modify Object so it would implement the Comparable interface.
* Another solution is to provide the `TreeSet` with a `Comparator`

