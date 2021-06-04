---
description: Just like society
---

# Comparators

**Sorting an Object array** : In order to sort an object array, all elements must implement either `Comparable` or `Comparator` interface to define the order of the sorting.

Consider we have a task of sorting objects that are instances of the following class:

```java
public class User {
    public final Long id;
    public final String username;

    public User(Long id, String username) {
        this.id = id;
        this.username = username;
    }

    @Override
    public String toString() {
        return String.format("%s:%d", username, id);
    }
}
```

In order to use `Collections.sort(List list)` we need to modify the User class to implement the Comparable interface. For example

```java
public class User implements Comparable<User> {
    public final Long id;
    public final String username;

    public User(Long id, String username) {
        this.id = id;
        this.username = username;
    }

    @Override
    public String toString() {
        return String.format("%s:%d", username, id);
    }

    @Override
    /** The natural ordering for 'User' objects is by the 'id' field. */
    public int compareTo(User o) {
        return id.compareTo(o.id);
    }
}
```

Consider the following to use this implementation

```java
List<User> users = Lists.newArrayList(
    new User(33L, "A"),
    new User(25L, "B"),
    new User(28L, "")
);

Collections.sort(users);
System.out.print(users);
// [B:25, C:28, A:33]
```

You can also compare the `username`

```java
Collections.sort(users, (l, r) -> l.username.compareTo(r.username));
```

