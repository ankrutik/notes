# Switch Expressions
Tags: #java 

Java 12

```java
DayOfWeek day = DayOfWeek.FRIDAY;
int numOfLetters = switch (day) {
    case MONDAY, FRIDAY, SUNDAY -> 6;
    case TUESDAY                -> 7;
    case THURSDAY, SATURDAY     -> 8;
    case WEDNESDAY              -> 9;
};
```

- Evaluates to single value
- Replacement for complicated, nested if-else-operator or `?:`

# Links

# References