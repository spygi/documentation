## Basics/Syntax
+ Jtools: jstack(threads), jstat(monitoring), jmap(memory)
+ `transient` keyword: not serialized when sent over the network
+ Override (method from superclass) vs overloading (of arguments: change type and/or number of them)
+ Checked vs unchecked exceptions
+ Abstract classes vs interface:   
  + Abstract class: Can be `extended` by a single class (single inheritance) but needs not to implement all abstract methods (as long as it's also an abstract - multiple layers), can have some implementation.
  + Interface: Can be `implemented` by many classes but must implement all methods (single layer), can hold no state or implementation
  + Both: neither can contain private methods
+ [Primitive types](http://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html Primitive types): byte, short: 16bits, int: 32bits, long: 64bit, float: 32 not accurate, double: 64bits not accurate, boolean (you can't use 1 or 0 like in C or elsewhere), char: with ' ' single quotes (String is not one of them)
+ Unboxing (Object -> primitive) can result in NPE in runtime (autoboxing is the opposite): Under the hood the [ compiler converts the code](http://docs.oracle.com/javase/tutorial/java/data/autoboxing.html)
+ (Foo)null does not throw an exception but returns a null object of type Foo
+ [Field declaration](http://docs.oracle.com/javase/tutorial/reflect/member/fieldModifiers.html)  
  1. [Access identifiers](http://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html): aka visibility keywords, usually first by convention)
  1. Field specific governing runtime behavior: transient (has to do with serialization), volatile
  1. Static
  1. Final
  1. Annotations
+ [Method declaration](http://docs.oracle.com/javase/tutorial/reflect/member/methodModifiers.html)  
  1. Access identifiers
  1. Static
  1. Final
  1. abstract
  1. syncronised
  1. native
  1. strictf
  1. annotations
+ [Operator precedence](http://introcs.cs.princeton.edu/java/11precedence/)
Static keyword: : For class attributes and methods. : Static fields are initialized when the class is first loaded: either referred or instantiated. : You can't access a nonstatic method or field from a static method(eg. main), because the static method doesn't have the instance. : Abstract static methods are not allowed (if you have 2 subclasses B and C, which of will get called with A.foo()?)
+ Final keyword: for constants
+ [Annotations](http://docs.oracle.com/javase/tutorial/java/annotations/basics.html) Used by the compiler. creating object, casting, in implements, in throws. Can have 0, 1 or more elements.
+ varargs with <i>...</i>
+ For-each loop: http://docs.oracle.com/javase/1.5.0/docs/guide/language/foreach.html Applicable to arrays too! Cleaner code, especially for nested loops. But hides the iterator so you can't remove or replace elements as you traverse them -> wouldn't that cause a ConcurrentModification Exception anyways? You also can't use it to iterate multiple collections.

+ Checked vs unchecked Unchecked exceptions are all subclasses of RuntimeException. Checked are the rest and they need to be caught or declared with <code>throws</code>. : The consensus is that checked exceptions should be avoided because they break encapsulation: : If you change the low-level code so that it throws a new exception, the higher level classes must re-throw it until the one that handles it : A lot of classes need to be changed for something that happened in a different layer for which they don't need to care.
Collections
[http://ria101.wordpress.com/2011/12/12/concurrenthashmap-avoid-a-common-misuse/ Concurrent Hashmap common mistake]

## Specifics
+ ArrayList: dynamically resized (resizing cost), backed by an array, not thread safe. Good for iterating sequentially and getting elements.
+ LinkedList: double linked list, not thread safe. Good for inserting/deleting from the middle of the list.
+ Iterable interface: Iterator itr = al.iterator(); while(itr.hasNext()) { Object element = itr.next(); ... }
+ Comparable interface: Total ordering (antisymmetry, transitivity, totality), throws if incompatible types

## Memory model
Java is pass by value: : for primitives this is self-proven : for objects: the reference is passed as a value. Therefore you can change inner objects that the argument contains but not the original object itself.
A consequence is: : final List: allows modifying elements but compile-time error if modifying the List itself, Collections.unmodifiable offer truly immutable Lists.

## Multi-threading
[5 things](http://www.ibm.com/developerworks/library/j-5things15/)

Interview Questions
[http://norvig.com/java-iaq.html iaq]
[http://www.allapplabs.com/interview_questions/java_interview_questions.htm#q3 interview questions]
[https://www.udemy.com/blog/java-interview-questions/ udemy]
[http://www.techinterviews.com/master-list-of-java-interview-questions master list]
testing enums with == or equals: http://stackoverflow.com/a/2937561/2259743
Installation
JRE is to run Java programs, the runtime, the java applet. What the end-user needs. Most browsers are compatible with Java 7 64bit architecture, Chrome not (yet)
The JDK is what you need to write programs in java, provides the javac compiler and java command, it's part of the SDK.
The SDK contains besides the JDK also an application server (eg Tomcat) plus other stuff to program in Java.
[http://askubuntu.com/questions/21131/how-to-correctly-remove-openjdk-openjre-and-set-sunjdk-sunjre-as-default remove openjdk and set sun's Java as the default]
[http://www.devsniper.com/ubuntu-12-04-install-sun-jdk-6-7/ the guide I used in Doodle while in Ubuntu]

## Concurrency
+ Thread creation/running: by extending Thread or Thread(Runnable), ExecutorService, ForkJoinPool, Parallel Streams
+ Thread safety  
  + volatile variables [source](http://www.javamex.com/tutorials/synchronization_volatile.shtml): The value of this variable will never be cached thread-locally: all reads and writes will go straight to "main memory"; : Access to the variable acts as though it is enclosed in a synchronized block, synchronized on itself. [Note 1](https://stackoverflow.com/a/3038233/2259743): volatile ensures atomicity of double & longs writes and reads even though they (without volatile) happen in 2 operations. Note 2: `myVolatile++;` is a compound action therefore not thread safe.  
    + [volatile static makes sense](https://stackoverflow.com/questions/2423622/volatile-vs-static-in-java)
  + synchronized: can be on a method (locking on this) or block of code
  Difference? [Synchronized methods seem to generate less bytecode](http://www.ibm.com/developerworks/library/j-5things15/) therefore more efficient? [However](https://docs.oracle.com/javase/tutorial/essential/concurrency/syncmeth.html): when one thread is executing a synchronized method for an object, all other threads that invoke synchronized methods for the same object block (suspend execution) until the first thread is done with the object. I guess synchronized static methods can be heavily penaltied by that? Visibility: when a synchronized method exits, it automatically establishes a happens-before relationship with any subsequent invocation of a synchronized method for the same object.  
    + Locks are re-entrant meaning the thread that already has the lock can re-enter the synchronized code (but not another thread).
  + AtomicReferenceFieldUpdater->VarHandles (in Java 9)
  + java.util.concurrent.atomic for AtomicInteger etc.
  + ThreadLocal is in a sense the opposite of volatile: each thread maintains a local

## Streams
** @FunctionalInterface annotation (interface with only one abstract method - excluding those inhereted by Object), 
useful for lambdas etc.

* `::` is a method reference. The method can be static or not.
* Lambda body variants: 
`a -> a.startsWith(" ")`, `(a, b) -> System.out.println(a + b)`, `(int a, int b) -> System.out.println(a + b)`, 
```java
a -> { 
  // do something else 
  return a';
}
```
* intermediate vs terminal operations

[Cheat sheet](http://files.zeroturnaround.com/pdf/zt_java8_streams_cheat_sheet.pdf)
https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html#package.description
http://winterbe.com/posts/2014/07/31/java8-stream-tutorial-examples/
