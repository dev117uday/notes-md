---
description: Not Geo map
---

# Map in Java

## &#x20;Hash Map

### Available Methods

```java
.put()
.get()
.containsKey()
.containsValue()
.getOrDefault()
.forEach() // to iterate over
.keySet()  // for all keys
.values()  // for all values
.replace()
.replaceAll((key,value) -> value+10)
.putIfAbsent()
.remove()
```

### Declaring Hash Map

```java
Map<KeyType, ValueType> myMap = new HashMap<KeyType, ValueType>();
```

### Adding values

```java
myMap.put("key1", 1);
myMap.put("key2", 2);
```

### Getting values from Hash Map

```java
myMap.get("key1");
//return 1 (class Integer)

// Check whether the Key is in the Map or not
myMap.containsKey(varKey);

// Check whether the Value is in the Map or not
myMap.containsValue(varValue);
```

### Check if keys exists

```java
Map<String, String> num = new HashMap<>();
num.put("one", "first");
if (num.containsKey("one")) {
    System.out.println(num.get("one")); // => first
}
```

### get Or Default

```java
Map<Integer, String> map = new HashMap<>();
map.put(1, "First element");
map.get(1);  // => First element
map.get(2);  // => null
map.getOrDefault(2, "Default element");  // => Default element
```

### Iterating over hashMap

```java
map.forEach((key, value) -> 
   System.out.println("Key: "+key+ " :: Value: "+value));
```

**ONLY KEYS**

```java
for (String key : repMap.keySet()) {
    System.out.println(key);
}
```

**ONLY VALUES**

```java
for (Integer value : repMap.values()) {
    System.out.println(value);
}
```

### replace

If the key is present then the value is replaced by new-value. If the key is not present, does nothing

```java
Map<String, Integer> map = new HashMap<String, Integer>();
map.put("john", 20);
map.put("paul", 30);
map.put("peter", 40);
map.replace("peter",50); //{john=20, paul=30, peter=50}
map.replace("jack",60); //{john=20, paul=30, peter=50}
```

### replace All

```java
Map<String, Integer> map = new HashMap<String, Integer>();
map.put("john", 20);
map.put("paul", 30);
map.put("peter", 40);
map.replaceAll((key,value)->value+10);
//{john=30, paul=40, peter=50}
```

### put If Absent

```java
Map<String, Integer> map = new HashMap<String, Integer>();
map.put("john", 20);
map.put("paul", 30);
map.put("peter", 40);
map.putIfAbsent("kelly", 50);
//{john=20, paul=30, peter=40, kelly=50}
```

### remove

```java
map.remove("peter",40); 
// {john=30, paul=40}
```

## Linked Hash Map

`LinkedHashMap` class is Hash table and Linked list implementation of the Map interface, with predictable iteration order. It inherits `HashMap` class and implements the Map interface.

The important points about Java `LinkedHashMap` class are: A `LinkedHashMap` contains values based on the key. It contains only unique elements. It may have one null key and multiple null values. It is same as `HashMap` instead maintains insertion order.

```java
public static void main(String arg[])
{
    LinkedHashMap<String, String> lhm = new LinkedHashMap<String, String>();

    lhm.put("Ramesh", "Intermediate");
    lhm.put("Shiva", "B-Tech");
    lhm.put("Santosh", "B-Com");
    lhm.put("Asha", "Msc");
    lhm.put("Raghu", "M-Tech");

    Set set = lhm.entrySet();
    Iterator i = set.iterator();

    while (i.hasNext()) {
        Map.Entry me = (Map.Entry) i.next();
        System.out.println(me.getKey() + " : " + me.getValue());
    }

    System.out.println("The Key Contains : " + lhm.containsKey("Shiva"));
    System.out.println("The value to the corresponding to key : " + lhm.get("Asha"));
}
```

## Weakhashmap

**Weak References** : The objects that are referenced only by weak references are garbage collected eagerly; the GC won’t wait until it needs memory in that case.

```java
public class WeakHashMapTest {
    public static void main(String[] args) {

        Map hashMap= new HashMap();
        Map weakHashMap = new WeakHashMap();

        String keyHashMap = new String("keyHashMap");
        String keyWeakHashMap = new String("keyWeakHashMap");

        hashMap.put(keyHashMap, "Ankita");
        weakHashMap.put(keyWeakHashMap, "Atul");
        System.gc();

        System.out.println("Before: hash map value:"+hashMap.get("keyHashMap")+" and weak hash map
        value:"+weakHashMap.get("keyWeakHashMap"));
        keyHashMap = null;
        keyWeakHashMap = null;

        System.gc();
        System.out.println("After: hash map value:"+hashMap.get("keyHashMap")+" and weak hash map
        value:"+weakHashMap.get("keyWeakHashMap"));
    }
}
```

## Sorted Map

// not that useful

**Key points** :

* Sorted Map interface extends Map.&#x20;
* Entries are maintained in an ascending key order.&#x20;

**Methods of sorted Map** :

```java
Comparator comparator( )
Object firstKey( )
SortedMap headMap(Object end)
Object lastKey( )
SortedMap subMap(Object start, Object end)
SortedMap tailMap(Object start)
```

```java
public static void main(String args[]) {
    // Create a hash map
    TreeMap tm = new TreeMap();
    // Put elements to the map

    tm.put("Zara", new Double(3434.34));
    tm.put("Mahnaz", new Double(123.22));
    tm.put("Ayan", new Double(1378.00));
    tm.put("Daisy", new Double(99.22));
    tm.put("Qadir", new Double(-19.08));

    // Get a set of the entries
    Set set = tm.entrySet();
    // Get an iterator
    Iterator i = set.iterator();
    // Display elements

    while(i.hasNext()) {
        Map.Entry me = (Map.Entry)i.next();
        System.out.print(me.getKey() + ": ");
        System.out.println(me.getValue());
    }

    System.out.println();
    // Deposit 1000 into Zara's account
    double balance = ((Double)tm.get("Zara")).doubleValue();
    tm.put("Zara", new Double(balance + 1000));
    System.out.println("Zara's new balance: " + tm.get("Zara"));
}
```

## Hashtable

// not that useful

```java
import java.util.*;

public class Main {
    public static void main(String args[]) {
// create and populate hash table
        Hashtable<Integer, String> map = new Hashtable<Integer, String>();
        map.put(101, "C Language");
        map.put(102, "Domain");
        map.put(104, "Databases");
        System.out.println("Values before remove: " + map);
// Remove value for key 102
        map.remove(102);
        System.out.println("Values after remove: " + map);
    }
}
```

![](<../../.gitbook/assets/image (8).png>)
