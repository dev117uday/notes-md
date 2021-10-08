---
description: One umbrella
---

# Collections in Java

## Collections

The collections framework in `java.util` provides a number of generic classes for sets of data with functionality that can't be provided by regular arrays.

OR

The **Collection in Java** is a framework that provides an architecture to store and manipulate the group of objects.

Java Collections can achieve all the operations that you perform on a data such as searching, sorting, insertion, manipulation, and deletion.

![](../../.gitbook/assets/image%20%283%29.png)

A simple way to construct a List from individual data values is to use `java.utils.Arrays` method `Arrays.asList` :

```java
List<String> data = 
    Arrays.asList("ab", "bc", "cd", "ab", "bc", "cd");

List<String> list = new ArrayList<>(data); 
// will add data as is
Set<String> set1 = new HashSet<>(data); 
// will add data keeping only unique values

SortedSet<String> set2 = new TreeSet<>(data); 
// will add data keeping unique values and sorting
Set<String> set3 = new LinkedHashSet<>(data); 
// will add data keeping only unique values and
// preserving the original order
```

## Mapping Collections

```java
Map<String, Object> map1 = new HashMap<>(map);
SortedMap<String, Object> map2 = new TreeMap<>(map);
```

## Iterating over Collections

### Iterating over List

```text
List<String> names
= new ArrayList<>(Arrays.asList("Clementine", "Duran", "Mike"));

names.forEach(System.out::println);

// If we need parallelism use
names.parallelStream().forEach(System.out::println);

for (String name : names) {
    System.out.println(name);
}

for (int i = 0; i < names.size(); i++) {
    System.out.println(names.get(i));
}
```

#### Using Iterator

```java
//Creates ListIterator which supports both
//forward as well as backward traversel
ListIterator<String> listIterator = names.listIterator();

//Iterates list in forward direction
while(listIterator.hasNext()){
    System.out.println(listIterator.next());
}

//Iterates list in backward direction once reaches 
// the last element from above iterator in forward direction
while(listIterator.hasPrevious()){
    System.out.println(listIterator.previous());
}
```

### Iterating over Set

```java
Set<String> names = 
    new HashSet<>(Arrays.asList("Clementine", "Duran", "Mike"));

for (Iterator<String> iterator = names.iterator(); iterator.hasNext(); ) {
    System.out.println(iterator.next());
}

for (String name : names) {
    System.out.println(name);
}

Iterator iterator = names.iterator();
while (iterator.hasNext()) {
    System.out.println(iterator.next());
}
```

### Iterating over Maps

```java
Map<Integer,String> names = new HashMap<>();
names.put(1,"Clementine");
names.put(2,"Duran");
names.put(3,"Mike");


names.forEach((key, value) ->
        System.out.println("Key: " + key + " Value: " + value));

for (Map.Entry<Integer, String> entry : names.entrySet()) {
        System.out.println(entry.getKey());
        System.out.println(entry.getValue());
}

// Iterating over only keys
for (Integer key : names.keySet()) {
        System.out.println(key);
}

// Iterating over only values
for (String value : names.values()) {
        System.out.println(value);
}

Iterator entries = names.entrySet().iterator();
while (entries.hasNext()) {
        Map.Entry entry = (Map.Entry) entries.next();
        System.out.println(entry.getKey());
        System.out.println(entry.getValue());
}
```

## Immutable Empty Collections

```java
List<String> anEmptyList = Collections.emptyList();
Map<Integer, Date> anEmptyMap = Collections.emptyMap();
Set<Number> anEmptySet = Collections.emptySet();
```

