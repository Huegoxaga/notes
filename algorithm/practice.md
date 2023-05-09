# Practice Questions

## LeetCode

### 1. Two Sum

- Input:
  - An array of integers
  - A integer as target
- Output:
  - A list of the indices from the given list, the sum of two number equals the target
- Assumption:
  - Each set of input only has one solution
  - The number from the list can't add itself
  - The order of the solution list doesn't matter
- Solution:
  - Brute force with two nested loop - `O(n^2)`
  - Hashmap with elements in list as keys and their indices as values - `O(n)`
    - For each element in list, find its difference between itself and the target as complement. A solution is found when the complement exists in the keys and the complement is not the element itself
    - Instead of creating a hashmap (dictionary) and finding the complement in two full loop as a two-pass, the two steps can be done in one iteration
      - the only difference is one-pass can only pairing the complement before it in the list, two-pass can find solution from both sides in list
    - When the input list has duplicated values, this method still works as the last index is always saved, when the algorithm is looking at the key that is not saved in the hashmap it can still be paired with the other one with a different index

### 7. Reverse Integer

- Input:
  - A signed 32-bit integer
- Output:
  - A reversed input
  - the signs are kept the same
- Assumption:
  - Return `0` when the reversed integer is out of range
  - the environment does not allow you to store 64-bit integers
- Solution:
  - convert int to string, then check edge cases if its values are out of ranges - `O(log_10(n))` where `log_10(n)` is the length of the string

### 9. Palindrome Number

- Input:
  - An integer number
- Output:
  - Return true when the number is palindrome
    - Palindrome - An integer is a palindrome when it reads the same forward and backward
- Solution:
  - Construct a new reversed number and compare - `O(log_10(n))`
    - Edge cases:
      - return false when the number is negative
      - return true when it equals zero
    - One can only compare half of the number until midpoint
  - Consider the input integer as string, reverse and compare it - `O(log_10(n))` where `log_10(n)` is the length of the string

### 39. Combination Sum

- Input:
  - `candidates` - an array of distinct integers
  - a target integer
- Output:
  - a list of all unique combinations of the `candidates` where the sum of this list equals the target
- Assumption:
  - The order of the combinations in the output doesn't matter
  - The same number may be chosen from candidates an unlimited number of times
- Solution:
  - DFS (Backtracking) - `O(2^n)`, where n is the length of the input list
    - Recursively check the combinations of x numbers at xth depth
  - DP

### 167. Two Sum II

- Input:
  - A sorted array of integers in non-decreasing order
  - A integer as target
- Output:
  - A list of the indices from the given list, the sum of two number equals the target
  - All indices are added by one before returning (non zero based index)
- Assumption:
  - Each set of input only has one solution
  - The number from the list can't add itself
  - The order of the solution list doesn't matter
- Solution:
  - Brute force with two nested loop - `O(n^2)`
  - One-pass and two-pass with hashmap - `O(n)`
  - Binary search - `O(nlogn)`
    - iterate the array and perform binary search on the second element
    - for each iteration `O(n)`, there is a binary seach `O(logn)`
  - Two-pointer - `O(n)`
    - Starting with the sum of left-most element and right-most element
    - if sum is greater than target, try the sum of the first and the second last element
    - if sum is smaller, try the sum of the second and the last element
    - repeat the pattern until the single solution is found
  - Hashmap - `O(n)`
