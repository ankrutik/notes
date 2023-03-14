# Records
Tags: #java 

Java 14 feature
Final classes with final members that have public accessors.
`final` modifier is implicitly applied.

Used for 
- plain data carriers
- contain data not meant to be altered 
- only the most fundamental methods such as constructors and accessors are enough

```java
record Rectangle(float length, float width) { }
```

Implicitly attached are:
- `private final` accessors for each component
- Public read accessor method for each component that has the same name and return type as each component. `Rectangle::length()` and `Rectangle::width()`
- `equals()` and `hashCode()` that checks record type and each component is equal
- `toString()` with representation for each component

Explicit constructors will not have parameter list. This is called a *compact constructor*.
```java
record HelloWorld(String message) {
    public HelloWorld {
        java.util.Objects.requireNonNull(message);
    }
}
```

# Links

# References
https://docs.oracle.com/en/java/javase/14/language/records.html

