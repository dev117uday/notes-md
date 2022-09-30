# Factory DP

* Creational Design Pattern
* According to the requirement, the factory class with give you the Object

```java
interface Vehicle {
    public void numberOfTyres();
}

class Car implements Vehicle {
    @Override
    public void numberOfTyres() {
        System.out.println("Number of tyres : 4");
    }
}

class Bike implements Vehicle {
    @Override
    public void numberOfTyres() {
        System.out.println("Number of tyres : 2");
    }
}

public class Factory {
    public static Vehicle getVehicle(String vehicle) {
        if (vehicle.equalsIgnoreCase("car")) {
            return new Car();
        } else if (vehicle.equalsIgnoreCase("bike")) {
            return new Bike();
        }
        return null;
    }
}
```
