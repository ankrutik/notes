# Multiline Text Block
Tags: #java 

Introduced in Java 15

```java
String query = """
               SELECT "EMP_ID", "LAST_NAME" FROM "EMPLOYEE_TB"
               WHERE "CITY" = 'INDIANAPOLIS'
               ORDER BY "EMP_ID", "LAST_NAME";
               """;
```

Keep in mind:
- New line character will be normalised from CR (`\u000D`) and CRLF (`\u000D\u000A`) to LF (`\u000A`) by the Java compiler for uniformity
- Incidental white spaces
- Use `format()` and `replace()` instead of multiline text block concatenation

# Links

# References
https://openjdk.org/jeps/378