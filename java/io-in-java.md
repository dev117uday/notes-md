---
description: IO is important
---

# IO in Java

## Output

Use `System.out.println` to print to the console

```java
System.out.println("Hello World");
System.out.print("Hello World");
```

### Using System.console to read password

```java
char[] password = System.console().readPassword();
```

## Input

import `Scanner` from :

```java
import java.util.Scanner;
```

### Simple Array input

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        System.out.println("hello World");
        Scanner scanner = new Scanner(System.in);
        int[] arr = new int[10];
        for (int i=0; i<10;i++) {
            arr[i] = scanner.nextInt();
        }
        for (int i=0; i<10;i++) {
            System.out.print(arr[i]+", ");
        }
    }
}
```

