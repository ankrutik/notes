#java 

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