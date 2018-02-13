+ Stack vs heap:  
  + Stack is per thread, actual stack, pre-allocated (compile time), fast, limited
  + Heap is per application, on runtime, slower, limited by size of virtual memory
  
## Concurrency, threads, locks
+ Concurrency (many things at once) vs Parallelism (improve performance of one thing)
+ Visibility and Atomicity: locking guarantees both while volatile variables only visibility.
+ Optimistic vs pessimistic locking:  
  + Optimistic: compare and swap, do the change and then amend if possible or discard
  + Pessimistic: lock first, then change (synchronised blocks etc)
+ Types of locks:
  + Intrinsic? mutex, semephore
