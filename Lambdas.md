#java 

# Functional Interface
- Functional Interface in java is an interface with just 1 abstract method.
	- Default and static methods are allowed.

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