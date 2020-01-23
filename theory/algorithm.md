# Algorithm
Data structure is a systematic way of organizing and accessing data.
Algorithm is a step-by-step procedure for performing some task in a finite amount of time.
Shorter running time is the major indication of a better data structure or algorithm.

## Recursion
a method that calls itself is a recursive method.
It has a base case, the method will called itself until the base case is reached and solved.

## Iteration
a method that called repeatedly in a loop.

## Algorithm Analysis
It is used to tell if a data structure or Algorithm is good.

* Experimental studies, run methods, output current time before and after the operation, calculate and record the elapsed time for comparison. All irrelevant conditions are controlled.
  * Different elapsed time may obtained among identical tests due to background services of the testing device.
  * the biggest issue with experimental analysis is the Algorithm must be completed for testing.
  * IDEs like NetBeans contains a profiler that will indicate the amount of time spent in each function and on what lines in a function.

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
  * A computational problem is a problem that is meant to be solved by an algorithm.
  * A computational problem is described by specifying the data to be input to the algorithm, and the output that should be produced by the algorithm
  * Each possible input is called an instance of the problem. For analysis the instance size ``N`` is only taken into consideration.
  * There are two types of complexity:
    * the time complexity is the computational complexity that describes the amount of time it takes to run an algorithm.
    * Space complexity is a measure of the amount of working storage an algorithm needs.

### Time Complexity
* Generally larger input run slower.
* This method focus on studying the growth rate of primitive operation count related to the growth of input size.  
* When convert operation count into running time. For inputs with the same sizes, running time may vary. However, the worst-case is usually taken as the running time for this input size. It is good for code improvement.
* For logarithm function in computer science, the 2 in base 2 is often omitted. It looks similar to LOG with base 10.
* The Big O math model is used to simplify operation count functions for comparison.
  * A function ``f(x)`` can be converted to the big-Oh of another function ``g(x)``. if the y value of ``f(x)`` is always smaller or equal than ``g(x)`` times a constant for all x value greater than certain constant.
    * Then the generalized big-Oh function can be used to represent the complexity of the algorithm.
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

### Sequential Search
* It use a loop to: sequentially step through an array.
* compare each element with the search value
* stop when the value is found or the end of the array is encountered.
* It can be used with any array.
* Sequential Search searches from one end to another end, it has the following two types.
  * findFirst return the index for the first found value, -1 if not found. Worst case ``O(n)``.
  * findAll - When X is found record the position and continue. At the end of the array return all the positions. If X is never found, return an empty list of position, for all cases ``O(n)``.

### Binary Search
* It can only be used with sorted arrays, but is much faster than Sequential Search.
* Steps for binary search:
  1. compare target value with the median values(    round down if the mid position is not an integer). check equality first, if not determine the location the target in either upper or lower section
  2. compare the target with the median of the lower or upper section until it is found.
* Example of Recursive Binary Search:
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
* Worst case ``O(logN)``.

## Sort
An array is sorted in ascending order if the array entries increase as indices increase.
### Bubble Sort
* Steps for bubble sort:
  1. compare each value(from left to right one by one) with its next value to the right.
  2. when a bigger value is found, always swap the bigger one to the right, so one biggest value in each iteration should be places the end.
  3. Exclude the value found in the previous iteration by shorten the length of the loop by one
  4. repeat the process n times for n is the number of input.
* The complexity of Bubble Sort is ``О(n^2)`` (worst case).
* Example:
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

### Selection Sort
* Steps for bubble sort:
  1. Reset the leftmost element as the temp max value.
  2. Comparing the temp max value with rest values in the array. If a bigger one is found, set it as the temp max value.
  3. After the comparison in one iteration, swap the max value to its proper location according to a count number that count the rank of the max value of each iteration.
* The time complexity of Selection Sort is ``О(n^2)``(worst case).
* Example:
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

### Insertion Sort
* Steps for insertion sort:
  1. From left to right, starting with the second element, compare it with the first if it is smaller or equals the first place it before the first element.
  2. For the third element, compare it with the second, then the first. It the third is smaller than or equals with any element, place it before it.
  3. repeat the process to the last element. In the end all elements are placed into the right location.
* The complexity of Insertion Sort is ``О(n^2)`` (worst case).
* Example:
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
      A[scan] = A[scan-1];scan --;
    }
    // Drop in the unsorted value
    A[scan] = unSortedValue;
    // Now A[0..index] is sorted
  }
    // Now A[0..N-1] is sorted, so entire array is sorted
  ```

### Merge Sort
* Steps for merge sort:
  1. treat the array as n arrays, each has a length of one.
  2. create n/2 arrays, the length is doubled.
  3. compare 1st and 2nd elements, place them into the first larger array in order, compare 3rd and 4th elements, place them into the second larger array in order...
  4. create n/4 arrays, merge the n/2 arrays into n/4 array.
  5. repeat the process until merging into n/n arrays which is one big sorted array.
* The complexity of Insertion Sort is ``O(n log(n))`` (worst case).
* Since each compared value is copied to the new array, the merge sort does require new temporary arrays.

### Quick Sort
* Steps for quick sort:
  1. Set a Pivot point(usually the middle point).
  2. Compare pivot point with rest of the array, move all smaller value to the left and greater values or equal value to the right. Then the pivot point has the sorted index location.(This step is called Partition).
  3. Do the same procedure for the left and right sublists. Get two more sorted points.
  4. Repeat until all sublists has a length of 1 or 0.
* The complexity of Insertion Sort is ``О(n^2)`` (worst case).
* Example:
```java
void doQuicksort(int A[ ], int start, int end)
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
