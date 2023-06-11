# Pattern Matching
Tags: #java 

Introduced in Java 18

```java
static double getDoubleUsingSwitch(Object o) {
    return switch (o) {
        case Integer i -> i.doubleValue();
        case Float f -> f.doubleValue();
        case String s -> Double.parseDouble(s);
        default -> 0d;
    };
}
```

- Uses `switch` to replace multiple `if-elseif(o instanceof Type)` statements.

# Links

# References
https://openjdk.org/jeps/420