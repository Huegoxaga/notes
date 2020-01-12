Data structure is a systematic way of organizing and accessing data.
Algorithm is a step-by-step procedure for performing some task in a finite amount of time.
Shorter running time is the major indication of a better data structure or algorithm.


Algorithm Analysis
It is used to tell if a data structure or Algorithm is good.
* Experimental studies, run methods, output current time before and after the operation, calculate and record the elapsed time for comparison. All irrelevant conditions are controlled.
  * Different elapsed time may obtained among identical tests due to background services of the testing device.
  * the biggest issue with experimental analysis is the Algorithm must be completed for testing.
* Counting Primitive Operations, an algorithm can be measured by counting the following primitive operations it has:
  * Assigning a value to a variables
  * Following an object reference
  * Performing an arithmetic operation
  * Comparing two numbers
  * Accessing a single element of an array by index
  * Method overhead
    * Calling a method - allocate memory for parameters and local variables
    * Returning from a method - store the address of where control returns after the method terminates.
* Asymptotic Analysis
  * Generally larger input run slower.
  * This method focus on studying the growth rate of primitive operation count related to the growth of input size.  
  * When convert operation count into running time. For inputs with the same sizes, running time may vary. However, the worst-case is usually taken as the running time for this input size. It is good for code improvement.
  * For logarithm function in computer science, the 2 in base 2 is often omitted. It looks similar to LOG with base 10.
  * The Big O math model is used to simplify operation count functions for comparison.
    * A function ``f(x)`` can be converted to the big-Oh of another function ``g(x)``. if the y value of ``f(x)`` is always smaller or equal than ``g(x)`` times a constant for all x value greater than certain constant.
      * Then the generalized big-Oh function can be used to represent the complexity of the algorithm.
      * The complexity here refers to the time complexity.
      * In terms of the complexity, ``O(1)<O(log(n))<O(n)<O(nlog(n))<O(n^2)<O(2^n)<O(n!)``.
      * ``O(1)`` Constant Time: means the number of operations has no thing to do with input size.
      * ``O(n)`` Linear Time: means the number of operations is linear input size.
      * ``O(log n)`` Logarithmic Time: means the input size is equals 2 to the power of the number of operations.
      * ``O(n log n)`` usually means a ``O(log n)`` algorithm has an ``O(n)`` as its inner loop or outer loop.
      * ``O(n^2)`` Quadratic Time: means the number of operations is equals the input size times itself.
      * When finding Big O, ``g(x)`` should be in its simplest form.
    * Big-Omega function is found if ``f(x)`` is greater or equal than ``g(x)`` time constant ``c``.
    * Big-Theta is found if ``f(x)`` can be in between a function ``g(x)`` times two different constant.


## Search Algorithm
* A search algorithm is a method of locating a specific item in a larger collection of data.
* This type of algorithm is referred to as "Brute Force" as potentially all elements need to be visited.

### Sequential Search Algorithm
* It use a loop to: sequentially step through an array.
* compare each element with the search value
* stop when the value is found or the end of the array is encountered.


## recursion
a method that calls itself is a recursive method.
It has a base case, the method will called itself until the base case is reached and solved.

## iteration
a method that called repeatedly in a loop.

## Sequential Search
It can be used with any array.
Search from one end to another end,
findFirst - return the index for the first found value, -1 if not found. on average O(n/2).
findAll - When X is found record the position and continue. At the end of the array return all the positions. If X is never found, return an empty list of position, O(n)
## Binary Search
It can only be used with sorted arrays, but is much faster than Sequential Search.
compare target value with the median values, the location the target in upper or lower section, then compare the target with the median of the lower or upper section until it is found.
```java
int binarySearch(int A[], int lower, int upper, int X){
  // check base case for missing X
  if (lower > upper)
    return -1;
  // check if X is at the middle
  int middle = (lower + upper)/2;
  if (A[middle] == X)
    return middle;
  // determine which segment to continue search in
  if (A[middle] < X)
    return binSearch(A, middle+1, upper, X);
  else
    return binSearch(A, lower, middle-1, X);
}
```
Worst case O(logn)

    Algorithm and Complexity

    Binary search is for sorted objects, it tests the value at the middle, then locate the correct half of the object and test its mid value step by step.
    if the mid position is not an integer, round down.
    check equality first

    bubble sort: compare each value(from left to right one by one) with its next value to the right. swap the bigger one to the right, so one biggest value in the object can be found. repeat the process n times for n is the number of the values in the object.
    def bubbleSort(arr):
        n = len(arr)
     
        # Traverse through all array elements
        for i in range(n):
     
            # Last i elements are already in place
            for j in range(0, n-i-1):
     
                # traverse the array from 0 to n-i-1
                # Swap if the element found is greater
                # than the next element
                if arr[j] > arr[j+1] :
                    arr[j], arr[j+1] = arr[j+1], arr[j]
    or
        for passnum in range(len(alist)-1,0,-1):
            for i in range(passnum):
                if alist[i]>alist[i+1]:
                    temp = alist[i]
                    alist[i] = alist[i+1]
                    alist[i+1] = temp


    Complexity
    Big O is the notation(read as on the order of) for the worst case performance of an algorithm. variable n is the number of elements of your objects.
    Examples:
    O(log(n): binary search.
    O(n^2): bubble sort.
    O(1): constant time not related to inputs
    for complexity level:
