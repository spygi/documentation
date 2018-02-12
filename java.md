## Basics
+ Jtools: jstack(threads), jstat(monitoring), jmap(memory)
+ `transient` keyword: not serialized when sent over the network
+ Override vs overloading
+ `extend` and `implement`
+ Checked vs unchecked exceptions
+ ArrayList: dynamically resized (resizing cost), backed by an array, not thread safe. Good for iterating sequentially and getting elements.
+ LinkedList: double linked list, not thread safe. Good for inserting/deleting from the middle of the list.
+ Abstract classes vs interface:   
  + Can be extended by a single class (single inheritance) but needs not to implement all abstract methods (as long as it's also an abstract - multiple layers), can have some implementation.
  + Can be implemented by many classes but must implement all methods (single layer), can hold no state or implementation
  
[http://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html Primitive types]: : byte, short: 16bits, int: 32bits, long: 64bit, float: 32 not accurate, double: 64bits not accurate, boolean (you can't use 1 or 0 like in C or elsewhere), char: with ' ' single quotes
'''Gotchas''': : String is not one of them : Unboxing (Object -> primitive) can result in NPE in runtime (autoboxing is the opposite), [http://stackoverflow.com/questions/1811706/java-null-pointer-exception-when-unboxing-integer see this SO] :: Under the hood the [http://docs.oracle.com/javase/tutorial/java/data/autoboxing.html compiler converts the code]. : (Foo)null does not throw an exception but returns a null object of type Foo : Double & longs are written/read in 2 operations

[http://docs.oracle.com/javase/tutorial/reflect/member/fieldModifiers.html Field declaration]:
[http://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html Access identifiers/modifiers](aka visibility keywords, usually first by convention)
Field specific governing runtime behavior: transient (has to do with serialization), volatile
Static
Final
Annotations
[http://docs.oracle.com/javase/tutorial/reflect/member/methodModifiers.html Method declaration]:
Access identifiers
Static
Final
abstract
syncronised
native
strictf
annotations
[http://introcs.cs.princeton.edu/java/11precedence/ Operator precedence]
Static keyword: : For class attributes and methods. : Static fields are initialized when the class is first loaded: either referred or instantiated. : You can't access a nonstatic method or field from a static method(eg. main), because the static method doesn't have the instance. : Abstract static methods are not allowed (if you have 2 subclasses B and C, which of will get called with A.foo()?)
Final keyword: for constants
Annotations [http://docs.oracle.com/javase/tutorial/java/annotations/basics.html oracle] Used by the compiler. creating object, casting, in implements, in throws. Can have 0, 1 or more elements.
Signature of a method
Overload vs override:
Overload of arguments(change type and/or number of them)
Override a method from the super class
varargs with <i>...</i>
For-each loop: http://docs.oracle.com/javase/1.5.0/docs/guide/language/foreach.html Applicable to arrays too! Cleaner code, especially for nested loops. But hides the iterator so you can't remove or replace elements as you traverse them -> wouldn't that cause a ConcurrentModification Exception anyways? You also can't use it to iterate multiple collections.
Interface (implements ...) vs abstract (extends ...) class: : Both of them don't allow private methods. : Abstract class can have abstract (non implemented) methods but also implemented methods. : Interface is all unimplemented classes. : Doesn't require to write abstract everywhere
Single inheritance: x	but not x x
\	\
x x	y Circumvent it by using interfaces. Interfaces can be seen as callbacks as well (eg. sort() of a Comparable object calls the compareTo() method)

You can assign but not declare inside an if - statement
Java core
Iterable interface: Iterator itr = al.iterator(); while(itr.hasNext()) { Object element = itr.next(); ... }
Comparable interface: Total ordering (antisymmetry, transitivity, totality), throws if incompatible types
Unchecked exceptions are all subclasses of RuntimeException. Checked are the rest and they need to be caught or declared with <code>throws</code>. : The consensus is that checked exceptions should be avoided because they break encapsulation: : If you change the low-level code so that it throws a new exception, the higher level classes must re-throw it until the one that handles it : A lot of classes need to be changed for something that happened in a different layer for which they don't need to care.
Collections
[http://ria101.wordpress.com/2011/12/12/concurrenthashmap-avoid-a-common-misuse/ Concurrent Hashmap common mistake]
Memory model
Java is pass by value: : for primitives this is self-proven : for objects: the reference is passed as a value. Therefore you can change inner objects that the argument contains but not the original object itself.
A consequence is: : final List: allows modifying elements but compile-time error if modifying the List itself, Collections.unmodifiable offer truly immutable Lists.
Multi-threading
[http://www.ibm.com/developerworks/library/j-5things15/ Nice resource]

Volatile keyword, [http://www.javamex.com/tutorials/synchronization_volatile.shtml from this:] : The value of this variable will never be cached thread-locally: all reads and writes will go straight to "main memory"; : Access to the variable acts as though it is enclosed in a synchronized block, synchronized on itself. :: Difference with synchronised is that you can't have dead locks and volatile is allowed only on variables : A side effect is that operations on longs and doubles are atomic ``` myVolatile++; not thread safe ```
java.util.concurrent.atomic
Synchronised: method or <pre>{block(variable)}</pre> : A pattern I've read is: <pre> class Hello { static Hello instanceOfHello = ...; synchronised (instanceOfHello) { ... } </pre> : [http://www.ibm.com/developerworks/library/j-5things15/ This claims synchronized methods are more efficient than blocks]
ThreadLocal
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
Libraries
JUnit
Use the annotation @test to indicate it's a test. : The name of the method does not need to contain "test" for JUnit 4.
@After and @André Rouél for cleanup and preparation.
JSF
The handlers stuff: called from the .xhtml files to fetch data from the server on initial load. <pre> <![CDATA[ doodleJS.data.account = #{accountManagementHandler.accountJson}; ]]> </pre> (if you need to refetch data later on eg. after performing an operation on the server you can do so with a Jersey Resource)
Annotations: <br/> @RequestScoped <br/> @ManagedBean (you can give it another name with @ManagedBean( name = "mplampla" ) - happy debugging ) <br/> Similar @ManagedProperty( value = "#{localeHandler}" )
Tags : <c:if test=""> : <c:when test=""> ... <c:otherwise> : <f:subview rendered=""> : <ui:insert> # for the parent template : <ui:define> # for the child template : <ui:repeat value="" var=""> : <ui:include src="">
Code samples (a lot of conventions here) <pre> <c:if test="#{commonHandler.hasBackToMobileLink}"> # tests if - also ne not equal or eq <ui:insert name="backToMobile"> # insert inserts in the dom, define overwrites it if it exists already in the template </ui:insert> </c:if> <c:if test="#{[optional: not] thirdPartyLoginHandler.alreadyLoggedIn}"> # the ThirdPartyLoginHandler has a method .isAlreadyLoggedIn() </pre>
[http://www.tutorialspoint.com/jsf/jsf_managed_beans.htm TODO: Tutorial point]
Jersey
[https://jersey.java.net/documentation/1.18/jax-rs.html Specification]


## Concurrency
* Concurrency (many things at once) vs Parallelism (improve performance of one thing)
** Threads (by extending Thread or Thread(Runnable)) & ExecutorService vs ForkJoinPool & Parallel Streams
* Thread safety: volatile, synchronized, AtomicReferenceFieldUpdater->VarHandles (in Java 9, [example from Java Specialists]())

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
