#java 

See `codenotes/java_notes/lambdas/LambdaBasics.java` 
# Design Decisions

- Functional Interface -> Lambdas -> Method References
	- In order of simplifying
- For single statement lambdas
	- the method called inside the lambda will impact which Lambda type is used
		- number of parameters
		- presence of return
			- maybe method has a side effect on the object like `Collections.sort()`
		- type of return
- Check semantics of method name

Think about:
- Semantics of the Function type and what you want to do
- See what method you are going to use
	- does it return?
	- how many parameters does it take?

|What?|Function Type|Arguments?|Returns?|Method|More|
|---|---|---|---|---|---|
|Check 1 argument?|Predicate|1|`boolean`|`test()`|
|Check 2 arguments?|BiPredicate|2|`boolean`|`test()`|
|Only get?|Supplier|None|*Typed*|`get()`|
|Only give 1?|Consumer|1, *Typed*|None|`accept()`|`forEach` of Collections that work on 1 element|
|Only give 2?|BiConsumer|2, *Typed*|None|`accept()`|`forEach` of Collections that work on 2 elements|
|Give something, get another?|Function|1, *Typed*|1, *Typed*|`apply()`||
|Give 2 different things, get another?|BiFunction|2, *Typed*|1, *Typed*|`apply()`||
|Give 1 and get all same type?|UnaryOperator|1, *Typed*|1, *Typed*|`apply()`|Argument and return types same, defined once|
|Give 2 and get all same type?|BinaryOperator|2, *Typed*|1, *Typed*|`apply()`|2 Arguments and Return types same, defined once|

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

- #java/lambdas/bestpractices When using, **add descriptive name to object** of Predicate **instead of the method**
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

# Functions
## java.util.function.Function
- Takes 1 argument
- Returns
- Type the argument and return separately

```java
Function<String, Integer> length = s -> s.length();
length.apply("What is the length of this string?");
```

## java.util.function.BiFunction
- Take 2 arguments
- Returns
- Type the 2 arguments and return separately
```java
BiFunction<String, String, Boolean> contains = (x, y) -> x.contains(y);
contains.apply("Stream", "ream");
```

# Operators
## java.util.function.UnaryOperator
- Take 1 argument
- Returns
- Type of argument and return will be same, specific just 1 Type
```java
UnaryOperator<String> capitalizeOp = s -> s.toUpperCase();
capitalizeOp.apply("abc");
```

## java.util.function.BinaryOperator
- Takes 2 arguments
- Returns
- Type of 2 arguments and return will be same, specify just 1 Type
```java
BinaryOperator<String> concatBiOp = (x, y) -> x + y;
concatBiOp.apply("AC", "DC");
```

# Local variables referenced in lambda are Effectively Final
- Reassigning values to variables can be blocked by declaring them explicitly  `final`
- Once a local, non-final variable is used in a lambda, the variable becomes "Effectively Final"
	- the compiler will not allow you to reassign value to it
		- inside or outside the lambda
		- before or after definition of or call to the lambda
	- such local variables need to be maintained as final by not reassigning value
- From scope perspective, these variables are effectively final within a method with respect to the lambda defined in that method.
- Lambdas take snapshot of local variables and must not be changed.
```java
// localVariable will be used in lambda
        int localVariable = 4;

// following statement will not work, reassigning value before lambda definition 
// localVariable+=5;

Predicate<Integer> checkSomething = x -> {
	// following will not work, reassigning value inside lambda definition
	// localVariable++;
	return x + localVariable > 0;
};

// following statement will not work, reassigning value after lambda definition
//localVariable+=2;

System.out.println(checkSomething.test(6));
// following statement will not work, reassigning value after lambda call
//localVariable+=2;
```

# Method References
Regular way of writing lambdas
```java
String localName = "Krutik";
Predicate<String> localNameContains_withoutMethodRef = s -> localName.contains(s);
```
Lambda can be rewritten using method references when it contains 
- a single statement 
- or call to a single method
```java
String localName = "Krutik";
Predicate<String> localNameContains = localName::contains;
```
Note the following:
- local variables can be used
- method of type of local variable is mentioned without arguments
- argument to the method in the statement is implied to be the argument to the lambda

If a lambda parameter is simply passed to another method inside lambda body, then we can remove redundancy of referring to lambda parameter. 
## Bound
- Instances, or local variables referred to in the lambda body, are known at compile time
- Here, the methods are bound to the variable on which the method is called
```java
String localName = "Krutik";
Predicate<String> localNameContains = localName::contains;
System.out.println(localNameContains.test("r"));
BiPredicate<String, Integer> nameStartsWithOffSet = localName::startsWith;
System.out.println(nameStartsWithOffSet.test("ru", 1));
```
- What happens in case of Method overloading?
	- The method that will be called on the variable inside the lambda will match the number and type of parameters to the lambda.
	- In above `nameStartsWithOffSet` example, 
		- `String.startsWith` has 2 versions
			- `(String prefix)`
			- `(String prefix, int offset)`
		- `nameStartsWithOffSet` is a `BiPredicate` which takes 2 inputs
		- Call to `localName::startsWith` will be resolved to the `startsWith` version with 2 arguments

## Unbound
- We are not using any local variables in the lambda body.
	- Instances are not know at compile time.
- Method name is specified with Class instead of Object
- First parameter to lambda is considered as object on which to call the method
- Second parameter to lambda, if any, is considered as object to pass to method call
```java
Function<String, String> upperCase1 = String::toUpperCase;
// means Function<String, String> upperCase1 = s -> s.toUpperCase();
upperCase1.apply("case");
BiFunction<String, String, String> concat1 = String::concat;
// means BiFunction<String, String, String> concat1 = (x, y) -> x.concat(y);
concat1.apply("ABC", "DEF");
```

## Static methods
- Called on Class and not instance
```java
Consumer<List<String>> sort1 = Collections::sort;
List<String> listOfString = new ArrayList(Arrays.asList("h", "a", "n"));
sort1.accept(listOfString);
System.out.println(listOfString);
```

## Constructor
- Called on the Class with `new` method
- Need to use lambda types that return objects

```java
Supplier<StringBuilder> needAStringBuilder = StringBuilder::new;
// Supplier<StringBuilder> randomize = () -> new StringBuilder();
System.out.println(needAStringBuilder.get());

Function<Integer, List<String>> sizedList = ArrayList::new;
sizedList.apply(4);
```
