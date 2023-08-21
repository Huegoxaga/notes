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

```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashmap = {}
        for i in range(len(nums)): # iterate whole list
            complement = target - nums[i]
            if complement in hashmap: # look back for solution
                return [i, hashmap[complement]]
            hashmap[nums[i]] = i # otherwise, put current value to the dictionary
```

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
    - N bit unsigned integar has range `[0, 2^n-1]`
    - N bit signed integar has range `[-2^(n-1), 2^(n-1)-1]`, as an extra bit is used to represent the sign

```py
class Solution:
    def reverse(self, x: int) -> int:
        x = int(str(x)[::-1]) if x >= 0 else int('-' + str(x)[:0:-1])
        return 0 if x < -2**31 or x > 2**31 - 1 else x
```

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

  ```py
  class Solution:
      def isPalindrome(self, x: int) -> bool:
          if x == 0:
              return True
          elif x < 0:
              return False
          else:
              # Convert x into int list
              numList = []
              while x > 0:
                  numList.append(x % 10)
                  x = x // 10
              # Test Palindrome
              for i in range(len(numList)):
                  if numList[i] != numList[(i+1)*(-1)]:
                      return False
          return True
  ```

  - Consider the input integer as string, reverse and compare it - `O(log_10(n))` where `log_10(n)` is the length of the string

```py
class Solution:
    def isPalindrome(self, x: int) -> bool:
        return str(x) == str(x)[::-1]
```

### 22. Generate Parentheses

- Input:
  - Given an integer `n`
- Output:
  - all combinations `n` pairs of well-formed parentheses
- Example:
  - Input: `n = 3`
  - Output: `["((()))","(()())","(())()","()(())","()()()"]`
- Solution:
  - If opening bracket is `1` and closing bracket is `-1`, the sum of valid parentheses is zero. Find all combinations of valid brackets in a binary tree
    - Sum can't go below `-1` as no valid pair can start with closing bracket
    - Optionally, use two counters for opening and closing brackets

```py
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        res = []
        def dfs(brackets, depth, bracket_strs):
            status = sum(brackets) # Get sum once at each node for speed
            if depth == n * 2: # n pairs has n * 2 chars
                if status==0: res.append(bracket_strs)
                return
            dfs(brackets+[1], depth+1, bracket_strs+'(')
            if status > 0: dfs(brackets+[-1], depth+1, bracket_strs+')') #No new closing bracket when all brackets are paired
        dfs([1], 1, '(')
        return res
```

### 28. Find the Index of the First Occurrence in a String

- Input: Given two strings `needle` and `haystack`
- Output:
  - return the index of the first occurrence of needle in haystack
  - return `-1` if needle is not part of haystack
- Assumption:
  - haystack and needle consist of only lowercase English characters
- Solution:
  - String Slicing - `Time: O(N*M)`, check string equality of `needle` with length `N` at nearly every possible indexs of string `haystack` with length `M`

```py
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        for i in range(len(haystack)-len(needle)+1): # The last possible index plus one for end of range
            if needle == haystack[i:i+len(needle)]: return i
        return -1
```

### 39. Combination Sum

- Input:
  - An array of distinct integers
  - a target integer
- Output:
  - a list of all unique combinations of the given list where the sum of this list equals the target
- Assumption:
  - The order of the combinations in the output doesn't matter
  - The same number may be chosen from candidates for an unlimited number of times
- Solution:

  - DFS (Backtracking) - `Time: O(N^T/M)` : `N` is the length of the given list, `T` is the target value, and `M` is the smallest element in the given list
    - Recursively check the combinations of `N` numbers at `T/M` depth
    - The worst case will keep repeating the smallest number and check if their sum is a solution
    - [Tree Diagram](media/39.png)

```py
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        def dfs(idx, path, cur):
            if cur > target: return # Exit when sum is too large
            if cur == target:  # Check if current equals the target value
                res.append(path) # Save the result
                return
            for i in range(idx, len(candidates)):
                dfs(i, path+[candidates[i]], cur+candidates[i]) # pass starting index, sum list, sum value
        dfs(0, [], 0)
        return res
```

- DP

### 40. Combination Sum II

- Input:
  - An array of integers (can have duplicates)
  - a target integer
- Output:
  - a list of all unique combinations of the given list where the sum of this list equals the target
  - The solution set must not contain duplicate combinations
    - e.g. from candidates `[1,2,2,3]`, if target is `3`, only one `[1, 2]` can in inserted into the result
- Assumption:
  - The order of the combinations in the output doesn't matter
  - Each member from the candidates can only be used once
- Solution:

  - DFS (Backtracking) - `Time: O(N^2)`, `N` branch times `N` depth
    - [Tree Diagram](media/40.png)

```py
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        candidates.sort() # Sort to find duplicate answers
        def dfs(idx, path, cur):
            if cur > target: return
            if cur == target:
                res.append(path)
                return
            for i in range(idx, len(candidates)):
                # if the node is not left-most at the current depth and it equals the previous candidate
                if i > idx and candidates[i] == candidates[i-1]:
                    continue # Skip duplicated result in the same
                dfs(i+1, path+[candidates[i]], cur+candidates[i])
        dfs(0, [], 0)
        return res
```

### 94. Binary Tree Inorder Traversal

- Input:
  - A given tree object, with the following structure

```py
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```

- Output:
  - list of nodes' value after a inorder traversal
- Solution
  - [Recursion](https://leetcode.com/problems/binary-tree-inorder-traversal/solutions/283746/all-dfs-traversals-preorder-inorder-postorder-in-python-in-1-line/) - `O(n)` - `T(n) = 2T(n/2)+1`

```py
class Solution:
    def inorderTraversal(self, root: TreeNode):
        return self.inorderTraversal(root.left) + [root.val] + self.inorderTraversal(root.right) if root else []
```

- Iteration I - `O(n)`
  - More efficient approach

```py
class Solution:
    def inorderTraversal(self, root: TreeNode):
        res, stack = [], []
        while root or stack:
            while root: # Put all left node in stack first
                stack.append(root)
                root = root.left
            node = stack.pop() # Check Most left child
            res.append(node.val) # Save value
            root = node.right # Save left child's right node root, so all of its left nodes can be pushed to end of stack in next whild root
            # Visit the parent of the left leave in next interation until stack is empty or no more right node
        return res
```

- [Iteration II](https://leetcode.com/problems/binary-tree-inorder-traversal/solutions/713539/python-3-all-iterative-traversals-inorder-preorder-postorder-similar-solutions/) - `O(n)`
  - More flexible for postorder and preorder tranversal

```py
class Solution:
    def inorderTraversal(self, root: TreeNode):
        res, stack = [], [(root, False)] # Use flag to track visit
        while stack: # Visit root node first
            node, visited = stack.pop() # Pop the last node in list
            if node: # Check if node has a value
                if visited: # Only save value to list if the node is visited in the else block in the previous interation
                    res.append(node.val)
                else:  # Push right node first so it will be popped last
                    stack.append((node.right, False)) # Save child node to be expanded further
                    stack.append((node, True)) # Mark the current node visited to save its value when it get popped next time
                    stack.append((node.left, False))
        return res
```

### 100. Same Tree

- Input:

  - Two trees with the following structure

  ```py
  class TreeNode:
      def __init__(self, val=0, left=None, right=None):
          self.val = val
          self.left = left
          self.right = right
  ```

- Output:
  - True if two trees are identical
- [Solution](https://leetcode.com/problems/same-tree/solutions/642761/easy-to-understand-faster-simple-recursive-iterative-dfs-python-solution/):

  - Recursion - `O(n)`

  ```py
  class Solution:
      def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
          if not p and not q:
              return True # Two none node is the same
          if not q or not p:
              return False # Only one none node is not the same
          if p.val != q.val:
              return False # Check if node value is equal
          return self.isSameTree(p.right, q.right) and self.isSameTree(p.left, q.left) # Split comparision and use 'and' operator for all results
  ```

  - Iteration - `O(n)`

  ```py
  class Solution:
      def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        stack = [(p, q)] # Access two trees in tuple
        while len(stack):
            first, second = stack.pop()
            if not first and not second: pass # Pass both none
            elif not first or not second: return False # One none one not none is False
            else: # If both has value
                if first.val != second.val: return False # False if not equal
                stack.append((first.left, second.left)) # Save both tree's left nodes in stack for comparision in next iteration
                stack.append((first.right, second.right)) # Save both tree's right nodes in stack
        return True # Only equal when all comparsion is passed
  ```

### 110. Balanced Binary Tree

- Input:

  - One binary tree with the following structure

  ```py
  class TreeNode:
      def __init__(self, val=0, left=None, right=None):
          self.val = val
          self.left = left
          self.right = right
  ```

- Output:
  - True if the binary tree is balanced
- Solution:
  - `O(n)`

```py

```

### 121. Best Time to Buy and Sell Stock

- Input:
  - A list of stock prices by day in order
- Output:
  - The max profit one can made from one transaction
    - Profit is measured in one share
    - 0 if no profit can be made
- Solution:

  - Brutal - `O(n^2)`
  - One pass comparision - `O(n)`
    - Track the min value along the way from left to right in one pass
    - For bigger values track the difference as max profit

  ```py
  class Solution:
      def maxProfit(self, prices: List[int]) -> int:
          min_price = float('inf')
          max_profit = 0
          for i in range(len(prices)):
              if prices[i] < min_price: # Track min
                  min_price = prices[i] # Save min
              elif prices[i] - min_price > max_profit: # Track max profit
                  max_profit = prices[i] - min_price # Save max profit
          return max_profit
  ```

### 122. Best Time to Buy and Sell Stock II

- Input:
  - A list of stock prices by day in order
- Output:
  - The max profit one can made from multiple transactions
    - One can buy and sell on the same day
    - 0 if no profit can be made
    - Only one share is available
- Solution:

  - One pass comparision - `O(n)`
    - Sum all the difference when price on next day is higher than the price on current day

  ```py
  class Solution:
      def maxProfit(self, prices: List[int]) -> int:
          current = prices[0]
          profit = 0
          for p in prices: # For all daily prices
              if p > current: # when the daily price is higher
                  profit+=p-current # sum up the profit
              current = p # make the daily price the next current price
          return profit
  ```

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
  - Two-pointer 1 - `O(n)`
    - Starting with the sum of left-most element and right-most element
    - if sum is greater than target, try the sum of the first and the second last element
    - if sum is smaller, try the sum of the second and the last element
    - repeat the pattern until the single solution is found
  - Two-pointer 2 - `O(n)`
    - Create two pointers where one points at the first index in the array and the other points at the second index
    - If the sum of the values at the pointers is less than the target, shift both pointers over one
    - If the values summed are greater, shift the first pointer left one
