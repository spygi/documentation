## Algorithms
### Design techniques
From CtCI:  
- Examplify: write specific examples of the problem and derive a general rule
- Pattern matching: a variation of a known algo 
- Simplify and generalize (?)
- Base case and build: start from n = 1 and build next solutions from it. Good for recursive or dynamic problems ("find all permutations" etc).
- Brainstorm: with data structures or algorithms (if you know already the desired complexity of the solution)

TODO: gather also from chapter 11 of Algorithms in a nutshell

#### Tips
+ Consider sorting arrays firstin the beginning.
+ Time vs space tradeoff: you can improve time by using up more space and vice versa.
+ [Recursive solutions can be expressed iteratively](https://stackoverflow.com/questions/2093618/can-all-iterative-algorithms-be-expressed-recursively) and vice versa: if <-> while
+ Runner up pointer technique, for example in palindromes, rotated lists, segregating arrays
+ Parallelism: https://github.com/heineman/algorithms-nutshell-2ed/blob/master/JavaCode/src/algs/model/array/MultiThreadQuickSort.java


### Terminology
+ Space complexity: memory needed at *any* point in time. Unlike time complexity this is not the total/cumulative used by the algorithm.
  + Usually we care for *auxiliary space* complexity which means to ignore input storage (otherwise we would start with O(n) and upwards) [SO question](https://stackoverflow.com/questions/30220305/how-to-calculate-the-space-complexity-of-function)
  + Allocations (e.g. of an array of size n) count for the complexity
  + Recursion depth matters because variables stay in the stack. Specifically the space used is equal to "the deepest level of recursion" multiplied by "the size of the stack frame for each level". Note that for example in the fibonacci algorithm (`return fibonacci(i-1) + fibonaci(i-2);`) the first part is evaluated completely before the second, therefore we never get deeper than n levels of recursion.
+ Cases can be worst, average or best.
+ Analysis can be asymptotic or amortized.  
  + Complexity f(n) is usually expressed in terms of big O-notation (upper bound - takes at most f(n) time/space). Other notations are lower bound Ω, tight-bound Θ (both lower and upper bound - takes at least and at most f(n) time/space) or little-o (stricter than big-O). From smaller to bigger - O(1): constant, O(logn): logarithmic, O(sqrt(n)) or generally n^d where 0<d<1: less common, O(n): linear, O(nlogn): quasilinear, O(n^2): quadratic, O(n^3): cubic, O(n^k): polynomial, O(2^n): exponential, O(n!): factorial
  + Amortized: is the "average" cost over a number of operations because worst case can be too pessimistic, for more see [amortized analysis wiki](https://en.wikipedia.org/wiki/Amortized_analysis). An example for datastructures can be the cost of resizing an array list, a cost that is taken once every n insertions which could be considered amortized O(1) among all insertions.    


## Data structures
- Primitive types
- Arrays/Strings
- Lists
- Stacks and queues
- Heap: main property parent nodes are smaller or greater than children
- Trees: Binary and Binary Search Tree
- Hash Table 
- Graphs

|name|properties|Java|custom implementation|
|-|-|-|-|
|arrays||Arrays, ArrayList||
|strings||String, StringBuilder/Buffer||
|stack| LIFO, think of a stack of plates| Deque interface is preferred over Stack|single list (pointing down/back) or (resizing) Array|
|queue| FIFO| LinkedList or other implementations of Queue interface | implementation again with single list|

### How to choosing an appropriate structure
Check what operations/complexity we are requiring  
+ insertion (at both ends and middle)
+ deletion (is it different from insertion?)
+ lookup/search
+ existence (is there at all?)?
+ resizing?
+ access (knowing the index)

### Abstract Data Types
Some more Data types for reference

|name|properties|Java|custom implementation|
|-|-|-|-|
|bag|unordered set, can contain duplicates | - | |
|set|unordered, no duplicates|Set||
[etc](https://en.wikipedia.org/wiki/Abstract_data_type). Things to consider when implementing one or choosing: underflow, overflow, permits null items?

### Trees & Graphs - WIP
+ Trees are special cases of graphs.

+ Binary tree: each node has at most two children (a special case of k-ary tree for k=2)
+ Binary *search* tree: left child <= current node <= right child
+ Balanced tree: a binary tree with the minimum depth
+ Perfect full (complete) binary tree: all leaves are at the bottom and all non-leaf nodes have 2 children.
+ Trie: character


## Math/combinatorics
+ The difference between combinations and permutations is that in the latter the order of the *selected* items does matter [source](https://gmatclub.com/forum/permutations-and-combinations-simplified-150835.html)


## Resources
+ Complexitities and analysis http://www.leda-tutorial.org/en/official/ch02s02s03.html
+ [Complexities graph](http://bigocheatsheet.com/)
+ Algorithms in a nutshell, Edition 1 and [2nd in PDF](https://doc.lagout.org/science/0_Computer%20Science/2_Algorithms/Algorithms%20in%20a%20Nutshell%20%282nd%20ed.%29%20%5BHeineman%2C%20Pollice%20%26%20Selkow%202015-11-25%5D%20%28draft%29.pdf), [Github repo](https://github.com/heineman/algorithms-nutshell-2ed), check Java/Python code folders
+ [Clevercoder](https://clevercoder.net/2017/09/04/toptal-passed-interview/) and [here](https://clevercoder.net/2017/09/24/technical-interviews-prepare/)
+ [Toptal](https://www.toptal.com/algorithms/interview-questions)
+ [Interviewbit](https://www.interviewbit.com/dashboard/)
+ [Programcreek](https://www.programcreek.com/2012/11/top-10-algorithms-for-coding-interview/)
+ Codility
+ Algorithms in a nutshell version 2: https://doc.lagout.org/science/0_Computer%20Science/2_Algorithms/Algorithms%20in%20a%20Nutshell%20%282nd%20ed.%29%20%5BHeineman%2C%20Pollice%20%26%20Selkow%202015-11-25%5D%20%28draft%29.pdf
