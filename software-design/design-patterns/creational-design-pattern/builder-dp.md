# Builder DP

* Creational Design Pattern
* Used when we have too many arguments or many optional arguments

```java
package builder;

public class Vehicle {
    // required parameter
    private String engine;
    private int wheel;

    // optional parameter
    private int airbags;

    public String getEngine() {
        return this.engine;
    }

    public int getWheel() {
        return this.wheel;
    }

    public int getAirbags() {
        return this.airbags;
    }

    private Vehicle(VehicleBuilder builder) {
        this.engine = builder.engine;
        this.wheel = builder.wheel;
        this.airbags = builder.airbags;
    }

    public static class VehicleBuilder {
        private String engine;
        private int wheel;

        private int airbags;

        public VehicleBuilder(String engine, int wheel) {
            this.engine = engine;
            this.wheel = wheel;
        }

        public VehicleBuilder setAirbags(int airbags) {
            this.airbags = airbags;
            return this;
        }

        public Vehicle build() {
            return new Vehicle(this);
        }
    }

    @Override
    public String toString() {
        return "Vehicle [airbags=" + airbags + ", engine=" + engine + ", wheel=" + wheel + "]";
    }
}
```
