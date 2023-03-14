# Sealed classes and interfaces
Tags: #java

Prior to this spec, we could avoid a class from being extended by using the `final` keyword.

Using the sealed classes approach (Java 17), we can make superclasses widely accessible but limit its extensibility.

## Restrictions
- All permitted subclasses must be in the same module as the sealed classes.
- Every permitted subclass must explicitly extend the sealed class.
- Every permitted subclass must have either of the modifiers: 
	- `final`: closed for extension
	- `sealed`: open for extension by a few permitted classes
	- `non-sealed`: open for extension

## Sealed interfaces

```java
public sealed interface Service permits Car, Truck {
...
}
```

## Sealed classes

```java
public abstract sealed class Vehicle permits Car, Truck {
...
}
```

## Extension in permitted classes
```java
public non-sealed class Car extends Vehicle implements Service {
...
}
```
Note:
- `non-sealed` modifier
- This example extends a class as well as implements an interface

## with Records
[[Records]] are `final` by design so sealed classes/interfaces can be used with records without the need for specifying any modifier. 

# Links

# References
https://www.baeldung.com/java-sealed-classes-interfaces