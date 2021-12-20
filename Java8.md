# Java8-Features
This Repository contains sample Java programs for Java8 Features such as lambda expressions, functional interfaces, stream api, etc.

`ForEach() method`

`Lambda expressions`

`Stream API`

`Optional class`

`Collectors class`

`Base64 Encode Decode`

`StringJoiner(Java 8)`

`Java 8 Date/Time API (Java 8)`

`Method Parameter Reflection (Java 8)`

`Method references`

`Functional interfaces`

`Type Inference (Java 8)`

`Default methods`

`Static methods in interface`

`Parallel array sorting`

`Nashorn JavaScript Engine`

`Type and Repeating Annotations`

`IO Enhancements`

`Concurrency Enhancements`

`JDBC Enhancements etc.`


## Functional Programming

- Embraces creating immutable objects.
- More concise and readable code.
- Using functions/methods as first class citizens.

### Example:

`Function<String, String> addSomeString = (name) -> name.toUpperCase().concat(“default”);`  


## Imperative vs Declarative style of programming

### Imperative

- Focuses on how to perform the operations.
- Embraces Object mutability.
- This style of programming lists the step by step of instructions on how to achieve an objective.
- We write the code on what needs to be done in each step.
- Imperative style is used with classic object oriented programming.

### Declarative

- Focus on what is the result you want.
- Embraces Object immutability.
- Analogous to SQL.
- Use the functions that are already part of the library to achieve an objective.
- Functional programming uses the concept of declarative programming.

`int sum = IntStream.rangeClosed(0, 100).sum();`

### Lambda

- Lambda is equivalent to a function without a name.
- Anonymous function.
- Lambdas are not tied to any class like a regular method.
- Lambdas can be assigned to a variable and passed around.
- Lambdas is mainly used to implement Functional Interfaces (SAM) single abstract methods.

## Lambda expressions:

- Introduced in java 8.
- Used in functional programming.
- function which can be created without belonging to any class.
- lambda expressions commonly used to implement simple event listeners/callbacks or with java stream API.

## Functional interface:
- Exists since java 1.0
- Annotation is introduced as a part of JDK 1.8
- Interface that contains only one abstract method.
- They can have only one functionality to exhibit.
- A functional interface can have any no. of default methods.
- Examples: Runnable, ActionListener, Comparable, Comparator.
- Other examples: Consumer, Supplier, Function, Predicate.

`Consumer - BiConsumer`
`Predicate - BiPredicate`
`Function - BiFunction, UnaryOperator, BinaryOperator`

## Method Reference:

- Introduced as a part of Java8.

- Purpose is to simplify the implementation functional interface.

- Shortcuts for writing lambda expressions.

- Refer to a method in a class.

`ClassName::instance-methodName`
`ClassName::static-methodName`
`Instance::methodName`

### Using Lambda

`Function<String, String> f = (s) -> s.toUpperCase();`

### Using Method reference

`Function<String, String> f = String::toUpperCase;`

*Method Reference is not applicable for Predicates.*

- Constructor Reference

`ClassName::new`

*Can only be used in the context of functional interfaces.*

### Lambdas and Local variables

*Any variable declared inside a method is called a local variable.*

Lambda have some restrictions on using local variables:

- Not allowed to use the same local variable as the lambda parameter or inside the lambda body.
- Not allowed to reassign a value to a local variable.
- No restrictions on instance variables.

## Streams API

- Main purpose is to perform some operations on Collections.
- Parallel operations are easy to perform using streams api without having to spawn multiple threads.
- Stream api can also be used with arrays or any kind of I/O.

**Stream**: Stream is a sequence of elements which can be created out of a collection such as list or arrays or any kind of I/O resources etc.

`List<String> names = Arrays.asList(“hello”, “world”, “shivank”);`

`names.stream();`

- Stream operations can be done sequentially or parallel.

`names.parallelStream();`

- Stream operations are lazy, means no intermediate operations are invoked until the terminal operation is invoked.

### map() 
converts one type to another.

### flatMap()
converts one type to another same as map() but it is used in context of streams where each element in a stream represent multiple elements.

### reduce()
Used to reduce the content of the stream to a single value.

### limit(n)
limits the “n” no. of elements to be processed in the stream.

### skip(n)
skips the “n” no. of elements from the stream.

### anyMatch()
returns true if any one of the element matches the predicate.

### allMatch()
return true if all of the elements matches the predicate.

### noneMatch()
just opposite to allMatch(). Return true if none of the element matches the predicate.

### findFirst()
returns the first element in the stream.

### findAny()
returns the first encountered element in the stream.

### Short circuit functions:

*These functions does not have to iterate the whole stream to evaluate the result.*

`limit()` `findFirst()` `findAny()` `anyMatch()` `allMatch()` `noneMatch()`

## Factory Methods:

### of()
creates a stream of certain values passed to this method,

`Stream<String> stringStream = Stream.of(“adam”, “jim”, “julie”);`

### iterate()
used to create infinite streams. 

`Stream.iterate(1, x -> x\*2)`

### generate()
used to create infinite streams.

`Stream.generate(<Supplier>)`

## Numeric Streams:

- Primitive values in a stream.

`IntStream` `LongStream` `DoubleStream`

### Aggregate functions: 
`sum()` `min()` `max()` `average()`

### Boxing: 
Converting the primitive type to wrapper class type.
***Example:*** converting int to Integer.

### Unboxing:
reverse of boxing.

### mapToObj()
convert each element numeric stream to some object.

### mapToLong()
convert a numeric stream to Long stream.

### mapToDouble()
convert a numeric stream to a double stream.

## Stream Terminal Operations

- Terminal operations collects the data for you.

- Terminal operations start the whole stream pipeline.

- Example: forEach(), min(), max(), reduce(), collect(), etc.

### joining()
joining collector performs the string concatenation on the elements in the stream.

### mapping()

### maxBy(), minBy()
takes comparator as an input and returns Optional as an output.

### summingInt(), averagingInt()
this collector** returns the sum and average as a result.

### groupingBy()
It is equivalent to the groupBy() operation in SQL. Used to group the elements based on the property.

- Output of the groupingBy() is Map<K, V>

`groupingBy(classifier)`

`groupingBy(classifier, downstream)` 

`groupingBy(classifier, supplier, downstream).`

## partitioningBy()
- Also a kind of grouping by. 

- Accepts a predicate as input.

- Return type of the collector is going to be Map<K, V>. Key is boolean.

`partitioningBy(predicate)`

`partitioningBy(predicate, downstream)`

## Parallel Streams

- Splits the source of data into multiple parts.

- Process them parallely

- Combine the result.

`IntStream.rangeClosed(1, 1000).parallel().sum()`

## How Parallel Stream Works

- Parallel stream uses fork/join framework(introduced in java 7).

- No. of thread created == no. of processors available in the machine.

## Optional Class

- Introduced in Java 8 to represent a non-null value.

- Avoids Null pointer exception and unnecessary null checks.

## Java Date/Time libraries

- LocalDate, LocalTime, LocalDateTime are part of the java.time package.

- These new classes are created with inspiration from the joda time library.

- All new time libraries are immutable.

- Supported classes like Instant, Duration, Period, etc.

## Reflection:

- Reflection is a programming language ability to inspect and dynamically call methods, classes, etc.

- So we can inspect the source code dynamically at runtime.

- Because of object-oriented design(polymorphism) we may not know the classes and methods at compile time.

- We can get the class using getClass() method.
