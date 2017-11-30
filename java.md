## Concurrency
* Concurrency (many things at once) vs Parallelism (improve performance of one thing)
** Threads (by extending Thread or Thread(Runnable)) & ExecutorService vs ForkJoinPool & Parallel Streams
* Thread safety: volatile, synchronized, AtomicReferenceFieldUpdater->VarHandles (in Java 9, [example from Java Specialists]())

## Version specifics
* 8
** @FunctionalInterface annotation (interface with only one abstract method - excluding those inhereted by Object), 
useful for lambdas etc.
** Using Consumer.java you can pass a function as an argument! Consumer is a FunctionalInterface btw.
