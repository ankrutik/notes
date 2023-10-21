#java 

See `codenotes/java_notes/lambdas/LambdaBasics.java` 
# Design Decisions

|Function Type|Arguments?|Returns?|Method|More|
|---|---|---|---|---|
|Predicate|1|`boolean`|`test()`|
|BiPredicate|2|`boolean`|`test()`|
|Supplier|None|*Typed*|`get()`|
|Consumer|1, *Typed*|None|`accept()`|`forEach` of Collections that work on 1 element|
|BiConsumer|2, *Typed*|None|`accept()`|`forEach` of Collections that work on 2 elements|

# Functional Interface
- Functional Interface in java is an interface with just 1 abstract method.
	- Default and static methods are allowed apart from the single abstract method 

```java
interface I {
	void method1();
}

...

//pre-java-8
I pre_java_8_implementation = new I(){
	public void method1(){
		System.out.println("method1");
	}
};
pre_java_8_implementation.method1();

//post-java-8
I post_java8_1 = () -> {
	System.out.println("method1");
	System.out.println("multiline code");
};
post_java8_1.method1();

I post_java8_2 = () -> System.out.println("method1 single line");
post_java8_2.method1();
```

# Generics and Return Types
- When lambda body returns a value
	- no need for return statement when the body is a single statement
	- when you need multiple statements, a code block is needed

```java
interface GenericParameterWithReturn<T> {
    boolean process(T t);
}

// single statement, returns value
GenericParameterWithReturn<Integer> i1_1 = i -> i > 0;
System.out.println(i1_1.process(45));

// multiple statements, returns value
GenericParameterWithReturn<Integer> i1_2 = i -> {
	System.out.println("printing something");
	return i > 0;
};
System.out.println(i1_2.process(54));
```
# Predicates
- Lambda body should return Boolean
## java.util.function.Predicate
- Returns **Boolean** 
- Takes 1 argument which is typed
- Predefined functional interface with single abstract method 
	- `boolean test(T i)`
```java
Predicate <Integer> do = i -> i > 0;
do.test(45);
```

- #java/lambdas/best_practices When using, **add descriptive name to object** of Predicate **instead of the method**
```java
// Instead of
interface IFunctionalInterface1<T> {
	boolean isGreaterThanZero(T t);
}
...
IFunctionalInterface1 i = i -> i > 0;
i.isGreaterThanZero(45);

// Do this
Predicate<Integer> isGreaterThanZero = i -> i > 0;
isGreaterThanZero.test(45);
```

## java.util.function.BiPredicate
- Returns Boolean
- Takes 2 arguments which are typed
- Function/Lambda definition
	- left hand side will need to be in round brackets because 2 elements
```java
BiPredicate<String, Integer> isOfLength = (s, i) -> s.length() == i;
isOfLength.test("Jack", 4);
```

# Lambda definition as object
- Pass Lambda definition as object using Predicates, Suppliers, Consumers, etc.
- Vocabulary in example below
	- `s` and `i` are **scoped** for the lambda function
	- Predicate in function parameter is **typed** for other parameter
```java
public static <T> boolean check(T t, Predicate<T> lambda){
	return lambda.test(t);
}
...
System.out.println(check(45, i -> i > 0));
System.out.println(check(-1, i -> i < 0));
System.out.println("ABC goes to market", s -> s.contains("to"));
```

# Supplier
## java.util.function.Supplier
- Returns object that is Typed
- Takes no argument
```java
Supplier<LocalTime> currentTime = () -> LocalTime.now();
currentTime.get();
```

# Consumers
## java.util.function.Consumer
- Takes 1 argument
- Returns void
```java
Consumer<String> printCapital = s -> System.out.println(s.toUpperCase());
printCapital.accept("abc");
Consumer<String> capitalize = s -> s.toUpperCase();
capitalize.accept("def");
```
- Collections which work on single elements accept Consumers in their `forEach` methods
```java
List<String> surnames = new ArrayList<>();
Consumer<String> maintainCapitalSurnames = s -> surnames.add(s.toUpperCase());
maintainCapitalSurnames.accept("arekar");
maintainCapitalSurnames.accept("mangaonkar");
surnames.forEach(s -> System.out.println(s));
```

## java.util.function.BiConsumer
- Takes 2 arguments
- Returns void
```java
Map<String, String> pincodes = new HashMap<String, String>();
BiConsumer<String, String> mapTownToPin = (town, pin) -> pincodes.put(town, pin);
Consumer<String> printPinForTown = town -> System.out.println(pincodes.get(town));
mapTownToPin.accept("Mahim", "400016");
mapTownToPin.accept("Gundavli", "400093");
printPinForTown.accept("Mahim");
```
- Collections that work on 2 elements, accept BiConsumers in their `forEach` methods
```java
...
pincodes.forEach((town, pin) -> System.out.println(town + ": " + pin));
```