+ Stack vs heap:  
  + Stack is per thread, actual stack, pre-allocated (compile time), fast, limited
  + Heap is per application, on runtime, slower, limited by size of virtual memory
+ Optimistic vs pessimistic locking:  
  + Optimistic: compare and swap, do the change and then amend if possible or discard
  + Pessimistic: lock first, then change (synchronised blocks etc)
+ Types of locks:
  + Intrinsic? mutex, semephore
