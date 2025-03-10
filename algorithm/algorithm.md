# Algorithm

- An algorithm is a step-by-step procedure for performing some task in a finite amount of time.
- Shorter running time is the major indication of a better data structure or algorithm.

## Basic Concepts

### Iteration

- A method that called repeatedly in a loop.
- Breadth-first search (BFS) is an iterative algorithm for searching a tree data structure for a node that satisfies a given property. It starts at the tree root and explores all nodes at the present depth prior to moving on to the nodes at the next depth level. Extra memory, usually a queue, is needed to keep track of the child nodes that were encountered but not yet explored
  - This approach ensures that nodes are processed level by level, which is the defining characteristic of BFS.
  - Here's a brief overview of how BFS works:
    1. Initialization: it starts by enqueuing the starting node into a queue and marking it as visited.
    2. Processing: While the queue is not empty:
       - Dequeue a node from the front of the queue.
       - Process this node (e.g., examine it or record its value).
       - Enqueue all of its unvisited neighbors, marking them as visited.
    3. Repeat: Continue this process until the queue is empty.

### Recursion

- A method that calls itself is a recursive method.
- It has a base case, the program will call the method recursively until the first base case is reached, then move on to the next top level method that hasn't been resolved
- Recursive methods can have the following types:
  - Linear Recursion - Each recursive method call itself once.
  - Binary Recursion - Each recursive method call itself twice.
  - Multiple Recursion - Each recursive method call itself more than twice.
- For binary and multiple recursion, the methods call itself as deep as possible than call the sibiling methods after all its recursive methods are called

#### Dynamic Programming

- Commonly referred to as DP
- It optimizes native recursive algorithm by saving the intermeditate result from recursive calls in a list in the memory, it reduces the complex of a recursive algorithm that would take exponential time further by pruning duplicated recursive calls when the result of a similar method call can be find in the result list
- DP techniques
  - Top-Down (Memoization)
    - Analyze from the end result, assume its known
    - Tracks result in a dictionary and check if a result key exists with hash map
  - Bottom-Up (Tabulation)
    - Pre-allocate an empty list to store all result and add intermediate results along the way, until the final result is shown at the end of the list
    - Analyze in timely order (from the base case up)

#### Backtracking

- It is a technique that build a solution incrementally and remove all the solutions that does not satisfy the constraints of the problem at any point of time
- the depth-first search (DFS) method is an implementation of backtracking
  - The goal is to explore all possible solutions to a problem
  - The dfs function is implemented as follows:
    1. The exit condition always goes first
    2. The code before recursive calls are executed from top to bottom until the exit condition is met
    3. Multiple recursive calls can be performed, they controls the traversal order of the data
    4. The lines after the recursive calls are executed after all above recursive methods are returned when base condition is met. They are doing backtracking from bottom to top
    5. The returned value pass data between the recursive method for decision making
  - It can be an iterative algorithm by using a stack, the stack can track the nodes that are visited by popping and to be visited by pushing

### Parallel

- An algorithm which can do multiple operations in a given time
- Concurrent is about multitasking and it does not necessarily run program in parallel
  - Asynchronous refers to run a peice of the program separately, its a way to express concurrency
- Foster’s Methodology - It states four stages of developing parallel programs
  - Partitioning - Decompose the large problem into many smaller problems
    - Domain (or Data) Decomposition
      - Example: Breaking up our matrix in our matrix multiplication problem
    - Functional Decomposition
      - Example: Breaking up the different tasks (operations) that need to be performed
  - Communication - Establish how to co-ordinate and share data between tasks or threads
    - May not always be required
  - Agglomeration or Aggregation - Optimization
    - Looking for any sequential tasks, or points where a task might be waiting
    - Looking for tasks that are doing a lot of communication, then merge then into one task if possible
  - Mapping - Assigning tasks to processors / threads
    - Minimize total execution time by
      - Assigning tasks to different processors, so they can execute concurrently
      - Assigning tasks to the same processors, when those tasks communicate between each other frequently
    - Doesn't apply if
      - It runs on a single core
      - It is controlled by a system with automated task scheduling

## Algorithm Analysis

It is used to tell if a data structure or Algorithm is good.

- `Greedy` is a term to describe an algorithm that is be short-sighted, heavily working on the current problem without seeing the whole picture
- Experimental studies, run methods, output current time before and after the operation, calculate and record the elapsed time for comparison. All irrelevant conditions are controlled.
  - Different elapsed time may obtained among identical tests due to background services of the testing device.
  - the biggest issue with experimental analysis is the Algorithm must be completed for testing.
  - IDEs like NetBeans contains a profiler that will indicate the amount of time spent in each function and on what lines in a function.
- Counting Primitive Operations, an algorithm can be measured by counting the following primitive operations it has:
  - Assigning a value to a variables
  - Following an object reference
  - Performing an arithmetic operation
  - Comparing two numbers
  - Accessing a single element of an array by index
  - Method overhead
    - Calling a method - allocate memory for parameters and local variables
    - Returning from a method - store the address of where control returns after the method terminates.
- Asymptotic Analysis
  - A computational problem is a problem that is meant to be solved by an algorithm.
  - A computational problem is described by specifying the data to be input to the algorithm, and the output that should be produced by the algorithm
  - Each possible input is called an instance of the problem. For analysis the instance size `N` is only taken into consideration.
  - There are two types of complexity:
    - the time complexity is the computational complexity that describes the amount of time it takes to run an algorithm.
    - Space complexity is a measure of the amount of working storage an algorithm needs.

### Performance Evaluation

- Throughput - Number of tasks completed / given amount of time
  - Expressed as the actions completed per unit of time
  - Example a processor can execute X number of tasks per second
- Latency - time / task (time per task)
  - Expressed in a unit of time
  - Example takes a task 50 milliseconds to complete

#### Time Complexity

- Generally larger input run slower.
- This method focus on studying the growth rate of primitive operation count related to the growth of input size.
- When convert operation count into running time. For inputs with the same sizes, running time may vary. However, the worst-case is usually taken as the running time for this input size. It is good for code improvement.
- For logarithm function in computer science, the 2 in base 2 is often omitted, written as `logx` or `lgx`. It looks similar to LOG with base 10
- The running time `T(n)` where `n` is the size of input, equals the sum of the product of the time cost of each statement (line of code) multiply by the number of times executed
- `T(n)` can be generalized by the following generalized, where `c` is the average execution time of all operations
  - the Big Oh by $$O(g(x))$$, if $$T(n)\leqslant c \cdot g(n)$$
  - the Big Omega by $$\Omega(g(x))$$, if $$T(n)\geqslant c \cdot g(n)$$
  - the Big Theta by $$\Theta(g(x))$$, if $$c_1\cdot g(n)\leqslant T(n)\leqslant c_2\cdot g(n)$$, which aim to provide an equivalent representation
  - the Small oh by $$o(g(x))$$, if $$T(n)\lt c \cdot g(n)$$
  - the Small Omega by $$\Omega(g(x))$$, if $$T(n)\gt c \cdot g(n)$$
- Comparsion of the order of growth
  - In terms of the complexity, `O(1)<O(log(n))<O(n)<O(nlog(n))<O(n^2)<O(2^n)<O(n!)`.
  - `O(1)` Constant Time: means the number of operations has no thing to do with input size.
  - `O(n)` Linear Time: means the number of operations is linear input size.
  - `O(log n)` Logarithmic Time: means the input size is equals 2 to the power of the number of operations.
  - `O(n log n)` usually means a `O(log n)` algorithm has an `O(n)` as its inner loop or outer loop.
  - `O(n^2)` Quadratic Time: means the number of operations is equals the input size times itself.
  - When finding Big O, `g(x)` should be in its simplest form.

#### Recursive Analysis

- Method of induction, e.g. find the big Oh of `T(n) = T(n - 1) + n`
  1. if `k` if the depth of recursion, for any step the function is `T(n-k) + n - k + 1`
  2. observe that there are `k` number of recursion, each execute `n` time
  3. at some point `n - k = 1`, so `k = n - 1`, both `k` and `n` are very close indefinitely
  4. for big O analysis `n = k`, so `T(n)` can be represented as `k` number of recursion multiply by `n` execution time, so $$c \cdot g(n) = c\cdot n^2$$
  5. let $$T(n) = c \cdot g(n)$$, and subsitute `T(n)` into the original function, obtain that $$T(n)=c(n-1)^2+n=cn^2-2cn+c+n$$
  6. since its big O $$T(n)\leqslant n^2$$, so `-2cn + c + n` must be equal or smaller than `0`, so $$c\leqslant \frac{1}{2-\frac{1}{n}}$$
  7. when n is very large `c` must be equal or smaller than `1/2`
  8. conclusion, the big O is `n` square where `c` must be equal or smaller than `1/2`
- Master Method, for $$T(n)=aT\left(\frac{n}{b}\right)+f(n)$$ where `𝑎 ≥ 0`, `𝑏 > 1` are constants and `f(n)` is an asymptotically positive function
  - An asymptotically positive function is one that is positive for all. sufficiently large n)
  - To find its generalized time, find $$X=n^{\log_b^a}$$, and `Y = f(n)`, then
    - If $$X\lt Y$$, $$f(n)=O(n^{\log_b^{a-\epsilon}})$$ for some constant `𝜖 > 0`, then $$T(n)=\Theta(n^{\log_b^{a}})$$
    - If $$X\approx Y$$, $$f(n)=\Theta(n^{\log_b^a}(\lg n)^k)$$ for some constant `𝑘 ≥ 0`, then $$T(n)=\Theta(n^{\log_b^a}(\lg n)^{k+1})$$
    - If $$X\gt Y$$, $$f(n)=\Omega(n^{\log_b^{a+\epsilon}})$$ for some constant `𝜖 > 0`, and `f(n)` satisfies the regularity condition, then $$T(n)=\Theta(f(n))$$
      - Regularity condition is $$af\left(\frac{n}{b} \right)\leqslant cf(n)$$, for some constant `c < 1` (as long as such constant c value can exist) and for all sufficiently large `n`

#### Parallel Computations

- Speedup is used to compare the increase in speed when program switched from sequential to parallel, it equals to $$\frac{t_s}{t_p}$$, `sequential execution time / parallel execution time with N workers`
  - When parallel shorten the execution time, the speedup is great than `1`
  - The optimal speedup happens when all of the code can be run in parallel, and it equals the number of processors
  - For the actual speedup calculation uses the above formula, input the actual value from measurement
    - Measurement should be an average of a large number of execution time
- Efficiency - `Actual Speedup / Number of Processors`
  - It shows how much advantage an additional core can bring to the program, in terms of percentage
- Amdahl’s Law - it predicts how much speed up can be achieved through parallelization, because based on the logic and purpose of the program, only a part of it can adopts parallelization
  - It states that the overall speedup equals $$\frac{t_s}{t_p}=\frac{t_s}{ft_s+(1-f)t_s/S}=\frac{n}{1+(n-1)f}$$
  - `f` means the percentage of the program that can be done in parallel
  - `S` is the corresponding speedup value for the parallel portion of the program
  - It proves that the larger the parallel portion is in the program the greater the program can benefit from using multi-cores
- The Cost of a computation is the sequential time divided by efficiency
- Gustafson's Law
  - It's another way of calculating speedup, it's more suitable for problem with larger size
  - The main idea is that the percentage of time taken to perform serial operations decreases as problem size increases
  - if `a(p)`, `b(p)` is the fraction of time taken for sequential and parallel processing in terms of problem size `p`
    - On a PARALLEL computer, `a(p) + b(p) = 1`
    - On a sequential computer, it would be `a(p) + n*b(p)` times slower, thus the speedup is also `a(p) + n*b(p)`
    - The speedup should increase with `n` greater compared to Amdahl's law

## Types of Algorithm

### Search Algorithm

- A search algorithm is a method of locating a specific item in a larger collection of data.
- This type of algorithm is referred to as "Brute Force" as potentially all elements need to be visited.

#### Sequential Search

- It use a loop to: sequentially step through an array.
- compare each element with the search value
- stop when the value is found or the end of the array is encountered.
- It can be used with any array.
- Sequential Search searches from one end to another end, it has the following two types.
  - findFirst return the index for the first found value, -1 if not found. Worst case `O(n)`.
  - findAll - When X is found record the position and continue. At the end of the array return all the positions. If X is never found, return an empty list of position, for all cases `O(n)`.

#### Binary Search

- It can only be used with sorted arrays, but is much faster than Sequential Search.
- The main idea is to eliminate half of the candidate in one iteration
- Worst case `O(logN)`
- Steps for binary search:
  1. compare target value with the median values(round down if the mid position is not an integer). check equality first, if not determine the location the target in either upper or lower section
     - Both round down or round up works
  2. compare the target with the median of the lower or upper section until it is found.
     - Eliminate lower or upper section entirely, including the tested mid value by assigning the new range to `mid -1` if to large or `mid + 1` if too small
- Example of Recursive Binary Search:

```java
int binarySearch(int A[], int lower, int upper, int X){
  // Exit when all elements are checked
  if (lower > upper)
    return -1;
  // Get mid point
  int middle = (lower + upper)/2;
  if (A[middle] == X)
    return middle;
  // determine which segment to continue search in
  if (A[middle] < X)
  // All values to the left of middle including the middle value itself are eliminated
    return binSearch(A, middle+1, upper, X);
  else
  // All values to the right of middle including the middle value itself are eliminated
    return binSearch(A, lower, middle-1, X);
}
```

#### Quick Select

- It is used to find the kth largest/smallest element
- Steps for Quickselect algorithm:
  - Choose a Pivot: Select a pivot element from the array
  - Partition: Reorder the array so that elements less than the pivot come before it, and elements greater than the pivot come after it
  - Recur: Depending on the position of the pivot, either the k-th smallest element is in the left partition, the right partition, or is the pivot itself
- Time complexity
  - `O(n)` Average case
  - `O(n^2)` Worst case
- Example:

```py
import random
def quickselect(arr, k):
    if len(arr) == 1:
        return arr[0]

    pivot = random.choice(arr)
    low = [x for x in arr if x < pivot]
    high = [x for x in arr if x > pivot]
    mid = [x for x in arr if x == pivot]

    if k < len(low):
        return quickselect(low, k)
    elif k < len(low) + len(mid):
        return mid[0]
    else:
        return quickselect(high, k - len(low) - len(mid))
```

### Sort

An array is sorted in ascending order if the array entries increase as indices increase.

- In-place means that the algorithm does not use extra space for manipulating the input but may require a small though non-constant extra space for its operation

#### Bubble Sort

- Steps for bubble sort:
  1. compare each value(from left to right one by one) with its next value to the right.
  2. when a bigger value is found, always swap the bigger one to the right, so one biggest value in each iteration should be places the end.
  3. Exclude the value found in the previous iteration by shorten the length of the loop by one
  4. repeat the process n times for n is the number of input.
- The complexity of Bubble Sort is `О(n^2)` (worst case).
- Example:

```java
for (int last=N-1; last>=1; last--){
  // Move the largest entry in A[0...last] to A[last]
  for (int index=0; index <= last-1; index++){     //swap adjacent elements if necessary
    if (A[index] > A[index+1]){
      int temp = A[index];
      A[index] = A[index+1];
      A[index + 1] = temp;
    }
  }
}
```

#### Selection Sort

- Steps for Selection sort:
  1. Reset the leftmost element as the temp max value.
  2. Comparing the temp max value with rest values in the array. If a bigger one is found, set it as the temp max value.
  3. After the comparison in one iteration, swap the max value to its proper location according to a count number that count the rank of the max value of each iteration.
- The time complexity of Selection Sort is `О(n^2)`(worst case).
- Example:

```java
for (last = N -1; last >= 1; last --)
{
  // Move the largest entry in A[0...last] to A[last]
  // Determine position of largest in A[0..last] and store
  // in maxIndex
  int maxIndex = 0;
  for (int index = 1; index <= last; index++)
  {
    if (A[index] > A[maxIndex])
    maxIndex = index;
  }
  // maxIndex is position of largest in A[0..last]
  // swap A[maxIndex] with A[last]
  int temp = A[maxIndex];
  A[maxIndex] = A[last];
  A[last] = temp;
}
```

#### Insertion Sort

- Steps for insertion sort:
  1. From left to right, starting with the second element, compare it with the first if it is smaller or equals to the first, place it before the first element.
  2. For the third element, compare it with the second, then the first. If the third is smaller than or equals with any element, place it before it.
  3. repeat the process to the last element. In the end all elements are placed into the right location.
- The complexity of Insertion Sort is `О(n^2)` (worst case).
- Example:

```java
//A[0..0] is sorted
for (index = 1; index <= N-1; index ++)
{
  // A[0..index-1] is sorted
  // insert A[index] at the right place in A[0..index]
  int unSortedValue = A[index];
  scan = index;
  while (scan > 0 && A[scan-1] > unSortedValue)
  {
    A[scan] = A[scan-1];
    scan --;
  }
  // Drop in the unsorted value
  A[scan] = unSortedValue;
  // Now A[0..index] is sorted
}
  // Now A[0..N-1] is sorted, so entire array is sorted
```

#### Merge Sort

- Steps for merge sort:
  1. cut the array with `n` elements in half recursively, until there are `n` array contains only one element
  2. compare elements in each array with the lowest current index, and place them in order in a larger array with doubled size
  3. repeat the process until merging into one big sorted array
- The complexity of Merge Sort is `O(nlog(n))` (worst case).
- Since each compared value is copied to the new array, the merge sort does require new temporary arrays.

#### Quick Sort

- Steps for quick sort:
  1. Set a Pivot point(usually the middle point).
  2. Compare pivot point with rest of the array, move all smaller value to the left and greater values or equal value to the right. Then the pivot point has the sorted index location.(This step is called Partition).
  3. Do the same procedure for the left and right sublists. Get two more sorted points.
  4. Repeat until all sublists has a length of 1 or 0.
- The complexity of Quick Sort is:
  - `O(nlogn)` (average case)
  - `О(n^2)` (worst case)
- Example:

```java
void doQuicksort(int A[], int start, int end)
{
  if (start < end)
  {
    // partition A[start..end]
    // and get the pivot point
    int pivotPoint = partition(A, start, end);
    // recursively do the first sublist
    doQuicksort(A, start, pivotPoint-1);
    // recursively do the second sublist
    doQuicksort(A, pivotPoint+1, end);
  }
}
int partition(int A[ ], int start, int end)
{
  // See implementation for improved midpoint selection
  int pivotValue = A[start];
  endOfLeftList = start;
  // At this point A[endOfLeftList] == pivotValue
  for (int scan = start + 1; scan <= end; scan ++)
  {
    if (A[scan] < pivotValue)
    {
      endOfLeftList++;
      swap(A, endOfLeftList, scan);
      // At this point A[endOfLeftList] < pivotValue
    }
  }
  // Move the pivotValue between the left and right sublists
  swap(A, start, endOfLeftList);
  return endOfLeftList;
}
```

#### Heap Sort

- The steps for Heap Sort:
  1. Build a max-heap from the input array (convert the array into a valid max-heap).
  2. Extract the maximum (root) element and move it to the end of the array.
  3. Reduce the heap size and heapify the root (bubble down) to maintain the max-heap property.
  4. Repeat step 2 and 3 until all elements are extracted
- Heap sort is an in-place sorting algorithm, it takes `O(1)` space
- The time complexity equals to the time for building the heap `O(n)` times the time for heapifying the tree `O(lgn)`
  - Building a heap takes `O(n)` time as it gets easier to heapify at the bottom

### Distance and Similarity Calculation

#### Euclidean Distance

- It Calculates the straight distance from one point to another using Pythagorean' theorem
- In a Euclidean space, find the square root of the sum of square of all difference along all axes
- It is a dissimilarity function

#### Manhattan Distance

- It calculates the sum of the distances along the axes, e.g. from point A to point B on a map is 4 block east and 2 block north, with a total of 6 blocks
- Find the sum of the absolute difference along all axes
- It is a dissimilarity function

#### Minkowski Distance

- It is a generalization of Euclidean and Manhattan distance
- The distance between point `t` and point `p` is $$d_{minkowski} =\left ( \sum_{i=1}^n|t_i-p_i|^m \right)^\frac{1}{m}$$, where $$t_n$$ is the value of `t` on `n` axis, same goes for $$p_n$$
  - When `m = 1` (L1 norm), the formula is calculating Manhattan distance
  - When `m = 2`(L2 norm), the formula is calculating Euclidean distance

#### Cosine Similarity

- It calculates how similar two vectors are, by geting the cosine value of the two vectors using the dot product formula, which is dividing the dot product by the product of their magnitude
- It is a similarity function

### Assignment Algorithm

- It is a problem in combinatorial optimization

#### Hungarian(Munkres Assignment) Algorithm

- It is used to find the smallest sum of elements from a square matrix, when only one element can be selected from each row and column
- Using brutal force will result a time complexity of `O(n!)`
- Hungarian Algorithm helps to speed up with a time complexity of `O(n^3)`
- Steps:
  1. Substract the smallest element of each row from all elements of each row
  2. Substract the smallest element of each column from all elements of each column
  3. Connect all the zeros using minimum numbers of lines, where `n` lines should be used for a `n X n` matrix
     - If lines used is smaller than `n`, substract all unconnected elements by the smallest one of them, then add the number to the intersection of the lines, then go back to step `3`, as a result the line number will increase by one, if `n` is still small repeat this additional step again
     - This additional step can be repeated as many as `n` times when `n` is initially `1`, and causing the final highest time complexity of this algorithm is equals `n`(line number) multiply by `n^2`(element scaning in this step), which is `O(n^3)`
  4. Find one zero in each row and column, and use the original element that located the zero's position to do the sum, then obtain the final result
- For solving problems involves non-square matrix, fit it with the smallest square matric and fill the missing elements with zeros, and discard the assignment for these position in the final step

### Path Finding Algorithms

- Algorithm that finds the shortest paths between nodes in a graph
- Eulerian circuits and Eulerian path focus on edges, and aim for covering all the edges
  - Eulerian circuits returns to the starting vertex and Eulerian path doesn't
- Hamiltonian circuits and Hamiltonian path focus on vertices, and aim for covering all the vertices
  - Hamiltonian circuits forms a circle and Hamiltonian path doesn't

#### Königsberg Bridge Problem

- It's about finding the unique path to cross all bridges when a group of islands are connected by multiple bridges
- Euler states that there will be an optimal solution only when there are zero or two island that is connected to an odd number of bridges. When there are two such bridges, the solution path starts at one of these bridges and ends at the other
  - This solution is proved by Carl Hierholzer
  - Such solution path is then called the Eulerian path
- An alternative form of the problem asks for a path that traverses all bridges and also has the same starting and ending point. Such a walk is called an Eulerian circuit or an Euler tour. Such a circuit exists if, and only if, the graph is connected, and there are no nodes of odd degree (connected to an odd number of bridges) at all.
  - All Eulerian circuits are also Eulerian paths, but not all Eulerian paths are Eulerian circuits

#### Dijkstra's Algorithm

- It finds the shortest time to get to all the next intermeditate nodes from the starting point to the destination, only the path that takes the shortest time to the next nodes will be adopted and will be used to reach further nodes
- When the length of all edge in a graph is the same, it is an unweighted graph, then Breath-first search algorithm can be used
- Dijkstra's Algorithm is a greedy expansion algorithm for weighted graph

#### `A*` Search Algorithm

- It is pronounced as "A-star" search algorithm
- It optimzes the Dijkstra's Algorithm by adding a heuristic function
  - The heuristic function returns an direct distance from the source to the destination, so the program can have a general sense of the general direction for searching
  - The `h` distance to the destination for each node that calculated from the heuristic function will be added to the actual distance traveled (`g`) to get to the node for path selection
    - The sum of `h` and `g` distance is the `f` distance for a node
- Open set or list refers to the nodes that will be evaluated or visited
- Closed set or list refers to the nodes that has been evaluated or visited
- Steps:
  1. Add the starting square (or node) to the open list
  2. Repeat the following:
     - A) Look for the node with lowest F cost on the open list
       - The node with lowest F is referred as the current node
     - B) Remove current node from open list, put it to the closed list
     - C) For each of the adjacent nodes to this current node (closed node)
       - If it is not walkable or if it is on the closed list, ignore it
       - If it isn't on the open list, add it to the open list. Make the current node the parent of this node. Record the F, G, and H costs of the node
       - If it is on the open list already, check to see if this path to that node is better, using G cost as the measure. A lower G cost means that this is a better path. If so, change the parent of the node to the current node, and recalculate the G and F scores of the node
         - The same scenario in Dijkstra's algorithm when an old path turns out to be better
         - If you are keeping your open list sorted by F score, you may need to resort the list to account for the change.
     - D) Stop when you:
       - Add the target square to the closed list, in which case the path has been found
       - Or, fail to find the target square, and the open list is empty. In this case, there is no path.
  3. Save the path. Working backwards from the destination node, adding each parent node to list until starting node is reached, the list of nodes represents the optimal path

#### The Travelling Salesman Problem

- It is a problem in combinatorial optimization

### Knapsack Problem

- It is a problem in combinatorial optimization
- The original problem is to maximize the value of items put in a knapsack that can only hold a certain amount of total weight, given each item has a specific weight and value

#### 0-1 Knapsack problem

- It solves a special scenario when there are only two options for each item in the defined list, ethier put it in the bag or leave it
- It is suitable to solve using dynamic programming
- A bottom-up solution is provided by drawing a table with all possible total weight for each columns and items for each row
  - For each column, the current total weight allowed is specified in the column header
  - For each row, only the item in current row and above can be used to fill the current weight
  - In each cell, find out the maximum value using the current weight and available items
  - When filling the cell, two values need to be calculated, the result if putting the current item or filling the current weight using the items from above row (directly using the value one cell above). For each of the above option, search for the possibility of add more items using the remaining weight for items in the above row and putting the max value in the current cell
- If the item index is `n`, total weight is `W`, values and weight for each item in array `v` and `w` (The array `v` and `w` are assumed to store all relevant values starting at index `1`), the example solutions for finding the max total value are shown below

  - The native recursive solution in Java that costs `O(2^n)`

  ```java
  int[] w = new int[] {1,2,3,4};
  int[] v = new int[] {2,4,7,8};
  int W = 15;
  int n = v.length;
  int knapsackRec(int n, int W) {
      if (n <= 0) {
          return 0;
      } else if (w[n - 1] > W) {
          return knapsackRec(n - 1, W);
      } else {
          return Math.max(knapsackRec(n - 1, W), v[n - 1]
            + knapsackRec(n - 1, W - w[n - 1]));
      }
  }
  ```

  - The recursive solution improved using dynamic programming that costs `O(nW)`

  ```java
  // Similar to the above code but using a temp 2D array to save and check the existing result
  int[] w = new int[] {1,2,3,4};
  int[] v = new int[] {2,4,7,8};
  int W = 15;
  int n = v.length;
  int[][] temp = new int[5][5];
  Arrays.fill(temp, -1);
  int knapsackRec(int n, int W) {
      int result;
      if (temp[n][W] != -1) return temp[n][W];
      if (n <= 0) {
          result = 0;
      } else if (w[n - 1] > W) {
          result = knapsackRec(n - 1, W);
      } else {
          result = Math.max(knapsackRec(n - 1, W), v[n - 1]
            + knapsackRec(n - 1, W - w[n - 1]));
      }
      temp[n][W] = result;
      return result;
  }
  ```

  - The bottom-up solution (as if one is drawing the `n` vs `W` table row by row) with dynamic programming that costs `O(nW)`

  ```java

    int[] wt = new int[] {1,2,3,4};
    int[] val = new int[] {2,4,7,8};
    int W = 15;
    int n = val.length;
    int knapsackBottomUp(int W, int n)
    {
      int i, w;
      int K[][] = new int[n + 1][W + 1];
      for (i = 0; i <= n; i++)
      {
        for (w = 0; w <= W; w++)
        {
          if (i == 0 || w == 0)
            K[i][w] = 0;
          else if (wt[i - 1] > w)
            K[i][w] = K[i - 1][w];
          else
            K[i][w] = Math.max(val[i - 1] + K[i - 1][w - wt[i - 1]], K[i - 1][w]);
        }
      }
      return K[n][W];
    }
  ```

  - To find the indices of item selected for the max value using filled table result

  ```java
  Set<Integer> getResultSet(int i, int j, int[][] m) {
      Set<Integer> result = new HashSet<>();
      if (i == 0) return result;
      if (m[i][j] > m[i - 1][j]) {
          result.add(i - 1); // Use the actual index of the item instead of the m table index
          result.addAll(getResultSet(i - 1, j - w[i - 1], m));
      } else {
          return getResultSet(i - 1, j, m);
      }
      return result;
  }
  ```

### Optimization

- Optimization refers to finding the action that provides the "best" result
- In mathematics, it means finding the independent value that minimize or maximize a function
- In optimization, the function is called cost, performance or fitness function
- Analytical Optimization and Gradian-based Optimization are some of the most popular ways to solve the optimization problems

#### Heuristic Optimization

- Heuristic Optimization is based on the Search Techniques
- They are inspired by the natural optimization
- Genetic Algorithm
  - It is an optimization algorithm that was developed by John Holland and his students at the University of Michigan in the early 1970
  - A function `f(x)` is created to solve a complex problem, it represents the adaptation of each individual value `x` to its environment
    - f is called fitness function
    - The goal is to max `f(x)`
  - The function can have multiple variables as a vector called phenotype, $$x=(x_1,x_2)$$
  - The binary representation of the phenotype is called the genotype and it works as chromosomes, $$C=\overline{c_1c_2}=\overline{BIN(x_1)BIN(x_2)}$$
  - The length of the binary number should be selected as the minimum number of digit to represent all possible solutions with a given quantization error. The number of counts in space is $$\left\lceil \frac{x_{max}-x_{min}}{\delta} \right\rceil+1$$, where `𝛿` is the minimum precision and $$\left\lceil \right\rceil$$ means round up. The precision for each binary count is $$\frac{x_{max}-x_{min}}{2^m-1}$$
    - When `x` is in range `[-5, 5]` if the solution needs to reach `0.1`, there will be $$\left\lceil \frac{5-(-5)}{0.1} \right\rceil +1=101$$ possible solutions. The binary number used to represent all solution needs to be 7 digits long. The gap between each binary representation is `(5-(-5))`
    - For the above example, if genotype is `0010000`, the solution it represented is `DEC(0010000)*0.079+(-5)=16*0.063-5=-3.992`， where `0.079` is the precision for a 7-digit binary count in range `[-5, 5]`
  - Every individual is called a Chromosome
  - The set of individual points is called Population
  - The GA runs as follow
    - Given a constant number of population `k`, randomly generate `k` vectors as the potential solutions
    - Calculate the fitness values of each vector and selection a pair by using the fitness value divide by total fitness value of the population as the probability distribution
    - Convert the vector input as the chromosome form $$\overline{c_1c_2}$$, and selecting a cutting point randomly and switch the parts
      - It is possible to cut the code from two or more points
      - Cross rate is the defined probability that the crossover operation will be perform on a pair of chromosomes
    - Use a small probability to and mutation to the two new chromosomes
      - This reduces the probability it stuck in a local maximum
    - Repeat the process to obtain other new pairs of chromosomes until the new population reaches `k`
    - Repeat the entire process generation by generation
      - It stops until it complete a set number of iterations or the fitness value reaches a predefine value
