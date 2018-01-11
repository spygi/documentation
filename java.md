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
