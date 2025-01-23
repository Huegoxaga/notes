# Practice Questions

## Code Template

### Array / String

- One pointer, One pass

```py
ptr = startingIdx # init pointer to a const value
for i in range(n): # iterate the entire array in one pass
# the for loop can be replaced with a while loop with condition for pointer
  if condition:
    # Modify array in-place
    # Update pointer
  return ptr # return the expected answer
```

- Two pointers, One pass

```py
ptr1 = startingIdx1 # init pointer 1 to a const value
ptr2 = startingIdx2 # init pointer 2 to a const value
for i in range(n): # iterate the entire array in one pass
# the for loop can be replaced with a while loop with condition for pointers
  if condition1:
    # Modify array in-place
    # Update pointer 1
  else:
    # Modify array in-place
    # Update pointer 2
  return ptr1 # return the expected answer
```

- Hashmap/Hashset, One pass

```py
hashmap = {} # or set()
for i in range(n): # iterate the entire array
  if target in hashmap: # check existing key
    return result
  hashmap[key] = value # add new key-value pair or key for set
```

- Sliding Window

```py
# init variables for window size
for i in range(n): # iterate through the array
  while condition:
    if not condition:
      break
    # increase window size
return result
```

#### Search

- Binary Search - Use it on sorted array to achieve `O(logn)`

  - Iterative method

  ```py
  def binary_search(arr, target):
      left, right = 0, len(arr) - 1  # Initialize pointers
      while left <= right:
          mid = left + (right - left) // 2  # Calculate the middle index, avoids the potential overflow
          if arr[mid] == target:
              return mid  # Target found, return index
          elif arr[mid] < target:
              left = mid + 1  # Move the left pointer to mid + 1
          else:
              right = mid - 1  # Move the right pointer to mid - 1
      return -1  # Target not found, return -1
  ```

  - Recursive method

  ```py
  def binarySearch(nums, target, left, right):
    if left > right:
        return -1  # Target not found
    mid = (left + right) // 2
    if nums[mid] == target:
        return mid
    elif nums[mid] > target:
        return binarySearch(nums, target, left, mid - 1)
    else:
        return binarySearch(nums, target, mid + 1, right)
  ```

- Quickselect - Find nth max/min in a list by returning the nth element when it is selected as the pivot point
  - Average case: O(n)
  - Worst case: O(n^2)

```py
def findKthLargest(self, nums: List[int], k: int) -> int:
    res, greater, lesser = 0, [], []
    pivot = nums.pop()
    for x in nums:
        if x >= pivot:
            greater += [x]
        else:
            lesser += [x]
    if len(greater) + 1 == k:
        return pivot
    elif len(greater) + 1 > k: # if pivot is too left
        res = self.findKthLargest(greater, k)
    else: # if pivot is too right
        res = self.findKthLargest(lesser, k-len(greater)-1)
    return res
```

#### Sort

- Quick Sort
  - Average case: O(nlogn)

```py
def quicksort(arr):
    if len(arr) <= 1:
        return arr
    else:
        pivot = arr.pop()
        # Optionally, use Median of three (first, last, middle) as pivot point to avoid ineffeciency when array is partially sorted
        # pivot = sorted([arr[0], arr[len(arr) // 2], arr[-1]])[1]
        greater = [x for x in arr if x >= pivot]
        lesser = [x for x in arr if x < pivot]
        return quicksort(lesser) + [pivot] + quicksort(greater)
```

#### Heap

- find kth largest in a given list
  - Heap also sorts a list of lists/tuples by its first element, second element, etc. in the sublists/tuples

```py
def findKthLargest(nums, k):
    k_heap = [] # init new heap list
    for num in nums:
        if len(k_heap) < k: # add element until there are k of them
            heapq.heappush(k_heap, num)
        else: # add k+1th and remove extra
            heapq.heappushpop(k_heap, num)
    return k_heap[0] # return smallest of the k largest in heap
    # one liner solution - return heapq.nlargest(k, nums)[-1]
```

- find kth smallest in a given list

```py
def findKthSmallest(nums, k):
    k_heap = []  # Initialize a new heap list
    for num in nums:
        if len(k_heap) < k:  # Add elements until there are k of them
            heapq.heappush(k_heap, -num)  # Push the negative value
        else: # when size is k
            heapq.heappushpop(k_heap, -num)  # Add k+1th and remove the largest (negated)
    return -k_heap[0]  # Return the negated k largest, then negate it back for kth smallest
    # one liner solution -  return heapq.nsmallest(k, nums)[-1]
```

### Tree

- Binary tree dfs

```py
def dfs(node):
    if node is None:
        return baseResult  # Base case: return a predefined result for None nodes
    # Access current node and add logic
    # For example: process the current node value
    # changes = <some operation with node.value>
    leftResult = dfs(node.left)  # Recursive call on the left child
    rightResult = dfs(node.right)  # Recursive call on the right child
    # Backtracking goes here
    return leftResult + rightResult + changes  # Combine results from left and right
```

- Binary tree bfs level by level

```py
def bfs(root):
    if root is None:
        return []  # Return an empty list if the tree is empty
    queue = deque([root])  # Initialize the queue with the root node
    result = []  # This will store the results of the BFS
    while queue:
        current = queue.popleft()  # Dequeue the front node
        # Process the current node (e.g., add its value to the result)
        result.append(current.value)  # Modify this based on your needs
        # Enqueue left and right children if they exist
        if current.left: queue.append(current.left)
        if current.right: queue.append(current.right)
    return result  # Return the final result list
```

- Binary search tree in-order/sorted order

```py
result = init # Init variables
def inOrderTraversal(node):
    if not node: return
    inOrderTraversal(node.left)
    # Add processing logic here
    result += node.val
    inOrderTraversal(node.right)
inOrderTraversal(root)
return result
```

- Binary search tree insertion

```py
def insert_node(root, key):
    if root is None:
        return Node(key)
    elif key < root.key:
        root.left = insert_node(root.left, key)
    else:
        root.right = insert_node(root.right, key)
    return root
```

### Graph

#### Explore Paths

- Use dfs in a directed unweighted graph

```py
graph = defaultdict(list)
for start, end in edges: # build graph
    graph[start].append(end) # graph is recorded as {node1: [node2, node3], node2: [node4]}
visited, path, all_paths= set(), [], [] # init variables
def dfs(node):
        if node not in graph or not graph[node]: # Base case: leaf node reached
            all_paths.append(list(path))  # Save the current path
            return
        visited.add(node) # track visited node to prevent cycling
        path.append(node) # update current path
        for neighbor in graph[node]: # Explore neighbors
            if neighbor not in visited:
                dfs(neighbor) # continue explore if its a new node
        # backtrack after all neighbors are explored
        path.pop()
        visited.remove(node)
# Explore all paths starting from each node
for start_node in graph:
    dfs(start_node)
```

- Use bfs in a directed unweighted graph

```py
graph = defaultdict(list)
for start, end in edges: # Build graph
    graph[start].append(end) # Graph is recorded as {node1: [node2, node3], node2: [node4]}
all_paths = []
for start_node in graph: # Iterate all nodes in the graph
    queue = deque([(start_node, [start_node])])  # Init queue as: [(current node, current path)]
    while queue:
        current_node, path = queue.popleft() # Explore leftmost node
        if current_node not in graph or not graph[current_node]: # Save path if current node is a leaf node
            all_paths.append(path.copy()) # Optionally, use list(path) to copy
        else: # If current node has child node
            for neighbor in graph[current_node]: # Iterate all children
                if neighbor not in path:  # Avoid cycles
                    queue.append((neighbor, path + [neighbor])) # Explore neighbors and update path
```

#### Cycle Detection

- BFS in undirected graphs

```py
from collections import defaultdict, deque
def is_cyclic_bfs(graph): # the given graph is represented as an adjacent list
    visited = set()
    for start_node in graph:
        if start_node not in visited: # for a start node in an unvisited component in the graph
            queue = deque([(start_node, -1)])  # (current_node, parent_node)
            visited.add(start_node)
            while queue:
                current, parent = queue.popleft()
                for neighbor in graph[current]:
                    if neighbor not in visited:
                        visited.add(neighbor)
                        queue.append((neighbor, current))
                    elif neighbor != parent:
                        return True  # Cycle detected
    return False
```

- DFS in undirected graphs

```py
def is_cyclic_dfs(graph):
  visited = set()
  def dfs(node, parent):
      visited.add(node)
      for neighbor in graph[node]:
          if neighbor not in visited:
              if dfs(neighbor, node):  # Recursive DFS call
                  return True
          elif neighbor != parent:
              return True  # Cycle detected
      return False
  for start_node in graph:
      if start_node not in visited:
          if dfs(start_node, -1): # for a start node in an unvisited component in the graph
              return True
  return False
```

- BFS (Kahn’s Algorithm) in directed graphs

```py
from collections import defaultdict, deque
def is_cyclic_directed_bfs(graph):
    in_degree = {node: 0 for node in graph}
    for node in graph:
        for neighbor in graph[node]:
            in_degree[neighbor] += 1
    queue = deque([node for node in graph if in_degree[node] == 0])
    count_visited = 0
    while queue:
        current = queue.popleft()
        count_visited += 1
        for neighbor in graph[current]:
            in_degree[neighbor] -= 1
            if in_degree[neighbor] == 0:
                queue.append(neighbor)
    return count_visited != len(graph)
```

- DFS in directed graphs
  - Use an additional set to track the current path

```py
def is_cyclic_directed_dfs(graph):
visited = set()
path = set()
def dfs(node):
    visited.add(node)
    path.add(node)
    for neighbor in graph[node]:
        if neighbor not in visited:
            if dfs(neighbor):  # Recursive DFS call
                return True
        elif neighbor in path:
            return True  # Cycle detected
    path.remove(node)  # Backtracking
    return False
for start_node in graph:
    if start_node not in visited:
        if dfs(start_node):
            return True
return False
```

#### Topological Sort

- BFS (Kahn’s Algorithm) in directed acyclic graphs (DAGs)

```py
from collections import deque, defaultdict
def topological_sort_bfs(vertices, edges):
    # Initialize in-degree and adjacency list
    in_degree = {i: 0 for i in range(vertices)}
    adjacency_list = defaultdict(list)
    # Build the graph
    for u, v in edges:
        adjacency_list[u].append(v)
        in_degree[v] += 1
    # Collect nodes with no incoming edges
    zero_in_degree = deque([node for node in range(vertices) if in_degree[node] == 0])
    topological_order = []
    while zero_in_degree:
        node = zero_in_degree.popleft()
        topological_order.append(node)
        # Reduce in-degree for neighbors
        for neighbor in adjacency_list[node]:
            in_degree[neighbor] -= 1
            if in_degree[neighbor] == 0:
                zero_in_degree.append(neighbor)
    # Check for a cycle
    if len(topological_order) == vertices:
        return topological_order
    else:
        raise ValueError("Graph contains a cycle and topological sort is not possible.")
# Example usage:
vertices = 6
edges = [(5, 2), (5, 0), (4, 0), (4, 1), (2, 3), (3, 1)]
print(topological_sort_bfs(vertices, edges))  # Output: [5, 4, 2, 3, 1, 0]
```

- DFS in directed acyclic graphs (DAGs)

```py
from collections import defaultdict
def topological_sort_dfs(vertices, edges):
    def dfs(node):
        visited[node] = True
        for neighbor in adjacency_list[node]:
            if not visited[neighbor]:
                dfs(neighbor)
        stack.append(node)
    adjacency_list = defaultdict(list)
    for u, v in edges:
        adjacency_list[u].append(v)
    visited = [False] * vertices
    stack = []
    for node in range(vertices):
        if not visited[node]:
            dfs(node)
    return stack[::-1]  # Reverse the stack for topological order
# Example usage:
vertices = 6
edges = [(5, 2), (5, 0), (4, 0), (4, 1), (2, 3), (3, 1)]
print(topological_sort_dfs(vertices, edges))  # Output: [5, 4, 2, 3, 1, 0]
```

#### Find Shortest Distance

- In distance calculation, graphs with unit weight are considered as all adjacent distance between nodes are 1
- Try to negate the weight for longest path calculation
- Use a previous node dictionary to store the best path when a path to the shortest distance is needed
- Topological Sort (DFS/BFS) and DP method in DAG
  - Time Complexity: `O(V+E)`

```py
from collections import defaultdict
def find_shortest_path_dag(num_nodes, edges, start):
    graph = defaultdict(list)
    for u, v, weight in edges:
        graph[u].append((v, weight))
    visited = [False] * num_nodes
    topo_order = []
    def dfs(node):
        visited[node] = True
        for neighbor, _ in graph[node]:
            if not visited[neighbor]:
                dfs(neighbor)
        topo_order.append(node)
    for node in range(num_nodes):
        if not visited[node]:
            dfs(node)
    topo_order.reverse()
    distances = [float('inf')] * num_nodes
    distances[start] = 0
    for node in topo_order:
        if distances[node] != float('inf'):  # Only process reachable nodes
            for neighbor, weight in graph[node]:
                distances[neighbor] = min(distances[neighbor], distances[node] + weight)
    return distances
```

- BFS in undirected graph with unit weight
  - Time Complexity: `O(V+E)`
  - BFS is not suitable for finding best path in weighted graphs

```py
from collections import deque
def shortest_distances(graph, start):
    distances = {node: float('inf') for node in graph}  # Initialize distances to infinity
    distances[start] = 0  # Distance to the start node is 0
    queue = deque([start])
    while queue:
        node = queue.popleft()
        for neighbor in graph[node]:
            if distances[neighbor] == float('inf'):  # If not visited
                distances[neighbor] = distances[node] + 1
                queue.append(neighbor)
    return distances
```

- Dijkstra's Algorithm in directed/undirected cyclic graphs with edge weights do not contain both signs
  - `O((V+E)logV)` where `logV` is the time to utilize the priority queue

```py
def dijkstra(graph, start):
    # Distance dictionary to keep track of the shortest distance from start node to every other node
    distances = {node: float('inf') for node in graph}
    distances[start] = 0  # Distance to the start node is 0
    # Priority queue to pick the node with the smallest distance
    priority_queue = [(0, start)]  # (distance, node)
    while priority_queue:
        current_distance, current_node = heapq.heappop(priority_queue)
        if current_distance > distances[current_node]:
            continue # If this distance is already larger than the known shortest distance, skip it
        for neighbor, weight in graph[current_node].items(): # Iterate over the neighbors of the current node
            distance = current_distance + weight
            # If a shorter path to the neighbor is found, update the distance and add it to the queue
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                heapq.heappush(priority_queue, (distance, neighbor))
    return distances
# Example graph represented as an adjacency list (node: {neighbor: weight})
graph = {
    'A': {'B': 1, 'C': 4},
    'B': {'A': 1, 'C': 2, 'D': 5},
    'C': {'A': 4, 'B': 2, 'D': 1},
    'D': {'B': 5, 'C': 1}
}
start_node = 'A'
shortest_paths = dijkstra(graph, start_node)
```

- Bellman Ford Calculation in a general graph
  - Time Complexity: `O(V*E)`

```py
def bellman_ford(graph, V, start):
    distances = {i: float('inf') for i in range(V)}
    distances[start] = 0
    # Relax all edges (V-1) times
    for _ in range(V - 1):
        for u, v, w in graph:
            if distances[u] != float('inf') and distances[u] + w < distances[v]:
                distances[v] = distances[u] + w
    negative_cycle_detected = False
    for u, v, w in graph:
        if distances[u] != float('inf') and distances[u] + w < distances[v]:
            negative_cycle_detected = True
            break
    return distances, negative_cycle_detected
```

### Linked List

- Iterate one singly linked list iteratively

```py
def iterate_linked_list(head):
    current = head  # Start from the head of the list
    while current:   # Continue until the end of the list
        print(current.value)  # Process the current node (e.g., print its value)
        current = current.next  # Move to the next node
```

- Iterate one singly linked list recursively

```py
def iterate_linked_list_recursive(node):
    if node is None:  # Base case: if the node is None, return
        return
    print(node.value)  # Process the current node (e.g., print its value)
    iterate_linked_list_recursive(node.next)  # Recursive call for the next node
```

- Iterate two singly linked list iteratively at the same time

```py
def iterate_two_linked_lists(head1, head2):
    current1 = head1  # Start from the head of the first list
    current2 = head2  # Start from the head of the second list
    while current1 or current2:
        if current1:
            print(f"List 1: {current1.val}")  # Process the current node from list 1
            current1 = current1.next  # Move to the next node in list 1
        if current2:
            print(f"List 2: {current2.val}")  # Process the current node from list 2
            current2 = current2.next  # Move to the next node in list 2
```

- Reverse doubly linked list

```py
def reverse_doubly_linked_list(head):
    current = head
    new_head = None  # This will become the new head of the reversed list
    while current:
        new_head = current  # Update new_head to the current node
        # Swap the next and prev pointers
        current.prev, current.next = current.next, current.prev
        current = current.prev  # Move to the next node (which is now previous)
    return new_head  # Return the new head of the reversed list
```

### Bit Manipulation

- Hamming weight
  - Bit Manipulation
  ```py
  def hammingWeight(self, n: int) -> int:
    count = 0
    while n:
        count += n & 1  # Increment count if the last bit is 1
        n >>= 1  # Right shift decimal number by 1 in its binary form to process the next bit
    return count
  ```
  - Brian Kernighan's Algorithm
  ```py
  def hammingWeight(self, n: int) -> int:
    count = 0
    while n: # As long as there is a one in its binary representation
        n &= (n - 1)  # Change the rightmost 1 bit to 0 bit of its binary representation
        count += 1
    return count
  ```
- print all `n` bits binary numbers in order

```py
# Recursive method
def print_n_bits(n):
    def print_01_codes(current, num_digits):
        if num_digits == 0:
            print(current)
            return
        print_01_codes(current + '0', num_digits - 1)
        print_01_codes(current + '1', num_digits - 1)
    print_01_codes('', n)
print_n_bits(2)

# Binary conversion method
def print_n_bits(n):
    for i in range(2**n):
        binary_str = bin(i)[2:] # from 0b0 to 0
        binary_str = (n - len(binary_str)) * '0' + binary_str # add leading 0s
        # Optionally use `binary_str.rjust(n,'0')` or `binary_str.zfill(n)`
        print(binary_str)

print_n_bits(3)
```

- add two number using signed 32-bits operations

```py
def getSum(self, a: int, b: int) -> int:
    # use signed 32-bit integer for this calculation
    MASK = 0xFFFFFFFF # the -1 of two's complement representation
    INT_MAX = 0x7FFFFFFF # max positive integer
    while b != 0:
        temp = (a ^ b) & MASK # add a and b without carrying, convert to binary without minus sign
        b = ((a & b) << 1) & MASK # save carrying for next loop, then convert to binary without minus sign with mask
        a = temp
    return a if a <= INT_MAX else ~(a ^ MASK) # convert back to binary with minus sign
```

### Math

- Check prime number

```py
def is_prime(n):
    if n <= 1:
        return False
    elif n <= 3:
        return True
    elif n % 2 == 0 or n % 3 == 0:
        return False
    i = 5
    while(i * i <= n):
        if n % i == 0 or n % (i + 2) == 0:
            return False
        i += 6 # prime number is usually a muliplier of 6 plus or minus 1
    return True
```

- Generate Pascal Triangle

```py
def generate_pascal(n):
    triangle = [[1] * (i + 1) for i in range(n)] # generate triange with right shape and fill it with 1
    for i in range(2, n):
        for j in range(1, i):
            triangle[i][j] = triangle[i - 1][j - 1] + triangle[i - 1][j]
    return triangle
```

### Dynamic Programming

- Memoization (Top-Down Approach)
  - One can start with a brutal force recursion, then optimize it by adding the memo variable

```py
memo = {}
def dp_memoization(n):
    # Base cases
    if n <= 0:
        return 0  # Example base case
    if n in memo:
        return memo[n]  # Return cached result
    # Recursive case
    result = dp_memoization(n - 1) + dp_memoization(n - 2)  # Example recurrence
    memo[n] = result  # Cache the result
    return result
```

- Tabulation (Bottom-Up Approach)
  - Iterative solution with pre-defined list

```py
def dp_tabulation(n):
    # Create a table to store results
    dp = [0] * n
    # Base cases
    dp[0], dp[1] = 0, 1  # Example base case
    # Fill the table
    for i in range(2, n):
        dp[i] = dp[i - 1] + dp[i - 2]  # Example recurrence
    return dp[n-1]  # Return the result for the input
```

### Class Implementation

```py
class ClassName:

    def __init__(self):
        # select the related data structure to store all required info
        pass

    def methodOne(self, input: int) -> None:
        # try to implement the remaining methods with given data declared in __init__
        pass
```

### Union Find

```py
class UnionFind:
    def __init__(self, n):
        # Initialize the parent and rank arrays
        self.parent = list(range(n))
        self.rank = [0] * n

    def find(self, x):
        # Find the root of x with path compression
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])  # Path compression
        return self.parent[x]

    def union(self, x, y):
        # Union by rank
        rootX = self.find(x)
        rootY = self.find(y)

        if rootX != rootY:
            # Attach the smaller tree under the larger one
            if self.rank[rootX] > self.rank[rootY]:
                self.parent[rootY] = rootX
            elif self.rank[rootX] < self.rank[rootY]:
                self.parent[rootX] = rootY
            else:
                self.parent[rootY] = rootX
                self.rank[rootX] += 1

    def connected(self, x, y):
        # Check if x and y are in the same set
        return self.find(x) == self.find(y)
```

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

    - [Two-pass Hash Table](https://leetcode.com/problems/two-sum/editorial/) - For each element in list, find its difference between itself and the target as complement. A solution is found when the complement exists in the keys and the complement is not the element itself

    ```py
    class Solution:
        def twoSum(self, nums: List[int], target: int) -> List[int]:
            hashmap = {}
            for i in range(len(nums)):
                hashmap[nums[i]] = i
            for i in range(len(nums)):
                complement = target - nums[i]
                if complement in hashmap and hashmap[complement] != i:
                    return [i, hashmap[complement]]
    ```

    - [One-pass Hash Table](https://leetcode.com/problems/two-sum/editorial/) - Instead of creating a hashmap (dictionary) and finding the complement in two full loop as a two-pass, the two steps can be done in one iteration
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

### 2. Add Two Numbers

- Input:
  - Two linked list head node `l1` and `l2`
- Output:
  - The sum of the two linked list as if each of them represent a number where each digits of the number are stored in each node reversely
- Assumption:
  - There is no leading zeros of a number stored in either linked list
- Solution:
  - While Loop - Add sum in new list
  ```py
  class Solution:
      def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
          tenth = 0 # track the carry over digit
          head = ListNode() # use head node for returning the list
          cur = head # use cur has reference for current tracking node
          while l1 or l2 or tenth > 0: # create new node if l1/l2 has digit or has carry over digit
              l = ListNode() # init new node
              l.val += tenth # add carry over digit if there is any
              tenth = 0 # reset
              if l1: # add l1 digit if there is any
                  l.val += l1.val
                  l1 = l1.next # advance to next node
              if l2: # add l2 digit if there is any
                  l.val += l2.val
                  l2 = l2.next # advance to next nodes
              tenth = l.val // 10 # store carry over digit
              l.val = l.val % 10 # keep single digit
              cur.next = l # update current tracking node's next node
              cur = cur.next # move pointer to next
          return head.next # ignore first empty node
  ```

### 3. Longest Substring Without Repeating Characters

- Input:
  - A string `s`
- Output:
  - The length of the longest substring without repeating characters
- Solution:
  - Sliding the window to the right while finding a larger window
  ```py
  class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        max_length = 1
        n = len(s)
        if not s: return 0
        for start in range(n):
            current = s[start:start+max_length] # update string with next starting point
            while start + max_length < n and len(current)  == len(set(current)):
                current += s[start+max_length] # update current substring
                if len(current) != len(set(current)): # check if updated substring will exit
                    break # no need to add length as the next one will fail
                max_length += 1
        return max_length
  ```
  - Track data in sliding window using a set
  ```py
  class Solution:
      def lengthOfLongestSubstring(self, s: str) -> int:
          n, maxLength, charSet, left = len(s), 0, set(), 0
          for right in range(n):
              if s[right] not in charSet:
                  charSet.add(s[right]) # Add right pointer to set if its new
                  maxLength = max(maxLength, right - left + 1) # save the largest window
              else:
                  while s[right] in charSet: # Keep removing left element until next right is not a duplicate
                      charSet.remove(s[left])
                      left += 1
                  charSet.add(s[right])
          return maxLength
  ```

### 6. Zigzag Conversion

- Input:
  - A string, `s`
  - An integer value, `rowNums`
- Output:
  - The reordered letter read from left to right. row by row
    - The letter will be ordered in a zig-zag order vertically from top to bottom where the row number equals to the input `rowNums`
- Example:
  - Input:
    - `s = "ABCDEFGHIJKLM"`
    - `rowNums = 4`
  - Reordered string is:
    ```
    A     G   M
    B   F H  L
    C E   I K
    D     J
    ```
  - Output:
    - `"AGMBFHLCEIKDJ"`
- Solution:
  - Track row number and add the letter to its corresponding rows
  ```py
  class Solution:
      def convert(self, s: str, numRows: int) -> str:
          res, row = [''] * numRows, 0
          if numRows == 1: return s # hande single row condition where row tracker never changes
          for c in s:
              res[row] += c # add char to corresponding row
              if row == 0: # Reset change value when reaching boundary
                  change = 1
              elif row == numRows - 1:
                  change = -1
              row += change # move row in zig-zag manner
          return ''.join(res)
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

  - Compare Splitted Digit in a List - Construct a new reversed number and compare - `O(log_10(n))`
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
              for i in range(int(len(numList)/2)):
                  if numList[i] != numList[(i+1)*(-1)]:
                      return False
          return True
  ```

  - String Solution - Consider the input integer as string, reverse and compare it - `O(log_10(n))` where `log_10(n)` is the length of the string

  ```py
  class Solution:
      def isPalindrome(self, x: int) -> bool:
          return str(x) == str(x)[::-1]
  ```

### 12. Integer to Roman

- Input:
  - The equivalent integer value of the input Roman number
- Output:
  - Roman numerals in a string
- Assumption:
  - Input number are in range `[1, 3999]`
- Solution

  - Divide from large char to small and replace `4`, `9` patterns

  ```py
  class Solution:
      def intToRoman(self, num: int) -> str:
          ROMAN_CHAR = {1: "I", 5: "V", 10: "X", 50: "L", 100: "C", 500: "D", 1000: "M"}
          raw_str = ""
          for base, value in list(ROMAN_CHAR.items())[::-1]: # Use base number from 1000 to 1 for division
              count = num // base # Use result from floor division to generate simple Roman string
              raw_str += value * count
              num -= count * base
          return raw_str.replace('VIIII','IX').replace('LXXXX','XC').replace('DCCCC','CM').replace('IIII','IV').replace('XXXX','XL').replace('CCCC','CD') # Match 9, 90, 900 first as they are longer
  ```

- Use translate dictionary that includes `4`, `9` chars in Roman numerals

  ```py
  class Solution:
      def intToRoman(self, num: int) -> str:
          # Creating Dictionary for Lookup
          ROMAN_CHAR = {1000: "M", 900: "CM", 500: "D", 400: "CD", 100: "C", 90: "XC", 50: "L", 40: "XL", 10: "X", 9: "IX", 5: "V", 4: "IV", 1: "I"}
          raw_str = ''
          for base, char in ROMAN_CHAR.items(): # Use base number from 1000 to 1 for division
              raw_str += char * (num // base) # Use result from floor division to generate Roman string from left to right
              num %= base # Use the remainder to generate remaining string
          return raw_str
  ```

  - [Reference Table Method](https://leetcode.com/problems/integer-to-roman/solutions/3421938/awesome-python-solution/)
    - All combination of numbers within range `1-3999` can be predicted with a table, from right to left

  ```py
  class Solution:
      def intToRoman(self, num: int) -> str:
          M=["","M","MM","MMM"] # index represents the number of thousands from 0 to 3000
          C=["","C","CC","CCC","CD","D","DC","DCC","DCCC","CM"] # index represents the number of hundreds from 0 to 900
          X=["","X","XX","XXX","XL","L","LX","LXX","LXXX","XC"] # index represents the number of tenth from 0 to 90
          I=["","I","II","III","IV","V","VI","VII","VIII","IX"] # index represents the number of ones from 0 to 9
          return M[num//1000]+C[num%1000//100]+X[num%1000%100//10]+I[num%1000%100%10] # Use remainders find the number of 1000, 100, 10, and 1
  ```

### 13. Roman to Integer

- Input:
  - Roman numerals in a string
- Output:
  - The equivalent integer value of the input Roman number
- Assumption:
  - Input Roman numerals are all valid
  - Input Roman numerals are in range `[1, 3999]`
- Solution:

  - Logic translate from right to left - `O(n)`
    - Since Roman numbers are written from large to small with exception for `4`, `9`, `40`, `90`, `400`, `900` etc. Translate the characters from right to left as long as the char value is growing. Otherviews, substract the values

  ```py
  class Solution:
      def romanToInt(self, s: str) -> int:
          ROMAN_CHAR = {"I": 1, "V": 5, "X": 10, "L": 50, "C": 100, "D": 500, "M": 1000}
          value = 0
          isSubstract = False
          for i in range(len(s)-1,-1,-1): # Always add the last char
              if i == len(s)-1: value += ROMAN_CHAR[s[i]]
              else: # For all other chars
                  if ROMAN_CHAR[s[i]] > ROMAN_CHAR[s[i+1]]: # If the char size is reducing
                      value += ROMAN_CHAR[s[i]] # add the current char value
                      isSubstract = False # Set the current operation type
                  elif ROMAN_CHAR[s[i]] < ROMAN_CHAR[s[i+1]]: # If the char size is growing
                      value -= ROMAN_CHAR[s[i]] # minus the current char value
                      isSubstract = True # Set the current operation type
                  else: # If the char is repeating, use the last operation type
                      if isSubstract: # If last operation is substraction, minus its value
                          value -= ROMAN_CHAR[s[i]]
                      else: # If last operation is adding, plus its value
                          value += ROMAN_CHAR[s[i]]
          return value # Code can be optimized as there is actually no duplicated minus char
  ```

  - Replace all six `4`, `9` patterns to regular order from big to small, then translate and sum up the values - `O(n)`

  ```py
  class Solution:
      def romanToInt(self, s: str) -> int:
          ROMAN_CHAR = {"I": 1, "V": 5, "X": 10, "L": 50, "C": 100, "D": 500, "M": 1000}
          return sum([ROMAN_CHAR[char] for char in s.replace("IV", "IIII").replace("IX", "VIIII").replace("XL", "XXXX").replace("XC", "LXXXX").replace("CD", "CCCC").replace("CM", "DCCCC")])
  ```

### 14. Longest Common Prefix

- Input:
  - An array of words
- Output
  - The longest common prefix amongst the list of words
- Solution:
  - Sort the array and compare the first and last
  ```py
  class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        strs.sort()
        first, last = strs[0], strs[-1]
        res = ""
        for i in range(min(len(first), len(last))):
            if first[i] == last[i]:
                res += first[i]
            else:
                break
        return res
  ```

### 15. 3Sum

- Input:
  - Given an array of integers
- Output:
  - Return all the triplets from element in the array which sum up to zero
  - The triplets must be distinct
- Assumption:
  - the order of the output and the order of the triplets does not matter
- Solution:
  - Sort list then find if two sum equals target if target is any number from left to right in the list
  ```py
  class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort() # Sort then use smallest integer from left as target
        res = set() # Use set to manage duplicated triples
        while len(nums) >= 3: # break list into target and a list with two pointer
            t = nums.pop(0)
            l, r = 0, len(nums) - 1
            while l < r:
                s = nums[l] + nums[r] + t # Find if sum of two pointed element and target is zero
                if s > 0:
                    r -= 1
                elif s < 0:
                    l += 1
                else:
                    res.add((t, nums[l], nums[r]))
                    r -= 1 # continue check pairs in between
                    l += 1
        return list(res)
  ```
  - Optimize previous solution by skipping duplicated target and left pointer after finding a triple
  ```py
  class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort() # Sort then use smallest integer from left as target
        res = []
        prev_t = None
        while len(nums) >= 3: # break list into target and a list with two pointer
            t = nums.pop(0)
            if prev_t == t:
                continue
            prev_t = t # update new target
            l, r = 0, len(nums) - 1
            while l < r:
                s = nums[l] + nums[r] + t # Find if sum of two pointed element and target is zero
                if s > 0:
                    r -= 1
                elif s < 0:
                    l += 1
                else:
                    res.append((t, nums[l], nums[r]))
                    prev_l = nums[l]
                    l += 1
                    r -= 1
                    while nums[l] == prev_l and l < r:
                        l += 1
        return res
  ```

### 17. Letter Combinations of a Phone Number

- Input:
  - A string containing digits from `[2, 9]`
- Output:
  - A list of letter combinations the digits can represent from the dialing pad
- Solution:
  - Use itertools method
    - `O(n*k^n)`
      - `n` is the length of the input string
      - `k` is the average number of letters each digit can represent
      - It takes `k^n` to find all combinations
      - Times `n` for the join operation of `n` letters for each combination
  ```py
  class Solution:
      def letterCombinations(self, digits: str) -> List[str]:
          digit_to_letters = {
              "2": "abc",
              "3": "def",
              "4": "ghi",
              "5": "jkl",
              "6": "mno",
              "7": "pqrs",
              "8": "tuv",
              "9": "wxyz",
          }
          if not digits:
              return []
          letter_groups = [digit_to_letters[digit] for digit in digits]
          return ["".join(combo) for combo in product(*letter_groups)]
  ```
  - Backtracking - `O(n*k^n)` and better space complexity
  ```py
  class Solution:
      def letterCombinations(self, digits: str) -> List[str]:
          number_to_chars = {
              "2": "abc",
              "3": "def",
              "4": "ghi",
              "5": "jkl",
              "6": "mno",
              "7": "pqrs",
              "8": "tuv",
              "9": "wxyz",
          }
          res = []
          def backtrack(depth, path):
              if depth == len(digits):
                  res.append(path)
                  return
              for c in number_to_chars[digits[depth]]:
                  backtrack(depth + 1, path + c)
          if digits:
              backtrack(0, "")
          return res
  ```

### 20. Valid Parentheses

- Input:
  - Given a string s containing just the characters '(', ')', '{', '}', '[' and ']'
- Output:
  - A boolean value indicating if the input string contains valid pairs
- Example:
  - Input: `"([)]"`
  - Output: `False`
- Solution:

  - Stack Method - Tracks opening brackets - `O(n)`

  ```py
  class Solution:
      def isValid(self, s: str) -> bool:
          pairs = {'(': ')', '{': '}', '[': ']'}
          open_brackets = [] # Tracks opening bracket
          for c in s:
              if c in pairs.keys(): # Find opening brackets, add it to open_brackets list
                  open_brackets.append(c)
              else: # Process closing brackets
                  if open_brackets: # Match closing bracket with it paired open bracket, added previously
                      if pairs[open_brackets[-1]] == c:
                          open_brackets.pop() # remove paired bracketed in open_brackets list
                      else: # If the current close bracket can't form a valid pair
                          return False
                  else: # If closing bracket are about to push to a empty list
                      return False
          if open_brackets: return False # if brackets list is not cleared, not all chars form valid pairs
          else: return True # if all check are passed
  ```

  - Stack Method - Tracks expected closing brackets

  ```py
  class Solution:
    def isValid(self, s: str) -> bool:
        pairs = {'(': ')', '{': '}', '[': ']'}
        closing_brackets = [] # Tracks expected closing bracket
        for c in s:
            if c in pairs.keys(): # Find opening brackets,
                closing_brackets.append(pairs[c]) # add corresponding closing_brackets to the list
            else: # Process closing brackets
                if closing_brackets: # If at least one closing bracket is expected
                    if closing_brackets[-1] == c: # If expected bracket matches current one
                        closing_brackets.pop() # remove last expected closing bracket
                    else:
                        return False
                else:
                    return False
        if closing_brackets: return False
        else: return True
  ```

  - [String Replacement Method](https://leetcode.com/problems/valid-parentheses/solutions/885074/python-solution-in-5-lines/) - `O(N^2)`
    - Keep replacing pairs of brackets to empty string until nothing left to replace
    - return `True` when the final string become empty

  ```py
  class Solution:
      def isValid(self, s: str) -> bool:
          while '()' in s or '[]'in s or '{}' in s:
              s = s.replace('()','').replace('[]','').replace('{}','')
          return False if len(s) !=0 else True
  ```

### 21. Merge Two Sorted List

- Input:
  - The head of two sorted (non-decreasing) linked list, with the following structure
  ```py
  class ListNode:
      def __init__(self, x):
          self.val = x
          self.next = None
  ```
- Output:
  - One merged sorted linked list
- Solution:
  - While loop iteration
  ```py
  class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        link = ListNode()
        head = link
        while list1 and list2:
            if list1.val < list2.val:
                link.next = ListNode(list1.val)
                list1 = list1.next
            else:
                link.next = ListNode(list2.val)
                list2 = list2.next
            link = link.next
        else: # Handle dangling list
            if list1:
                link.next = list1
            elif list2:
                link.next = list2
        return head.next
  ```
  - Recursive merge - Reconstruct list from right to left
  ```py
  class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        if list1 is None and list2 is None:
            return None # Base cases - stops when both list end
        elif list1 is None: # Base cases - adds trailing nodes
            return list2
        elif list2 is None:
            return list1
        if list1.val <= list2.val:
            list1.next = self.mergeTwoLists(list1.next, list2)
            return list1
        else:
            list2.next = self.mergeTwoLists(list1, list2.next)
            return list2
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

  - DFS in Binary Tree - If opening bracket is `1` and closing bracket is `-1`, the sum of valid parentheses is zero. Find all combinations of valid brackets in a binary tree
    - Sum can't go below `-1` as no valid pair can start with closing bracket
    - Optionally, use two counters for opening and closing brackets

  ```py
  class Solution:
      def generateParenthesis(self, n: int) -> List[str]:
          res = []
          def dfs(brackets, bracket_strs): # brackets tracks the number representation, bracket_strs tracks the string representation
              if len(brackets) == n * 2: # n pairs has n * 2 chars
                  if sum(brackets)==0: res.append(bracket_strs)
                  return
              dfs(brackets+[1], bracket_strs+'(')
              if sum(brackets) > 0: dfs(brackets+[-1], bracket_strs+')') # No new closing bracket when all brackets are paired
          dfs([1], '(')
          return res
  ```

  - [Pruned DFS Tree](https://leetcode.com/problems/generate-parentheses/solutions/2542620/python-java-w-explanation-faster-than-96-w-proof-easy-to-understand/) - To eliminate unnecesscery branch in the above tree when the number of left bracket is more than the number of pairs given, add a condition for the left branches

  ```py
  class Solution:
      def generateParenthesis(self, n: int) -> List[str]:
          def dfs(left, right, s):
            if len(s) == n * 2:
              res.append(s)
              return
            if left < n:
              dfs(left + 1, right, s + '(')
            if right < left:
              dfs(left, right + 1, s + ')')
          res = []
          dfs(0, 0, '')
          return res
  ```

### 26. Remove Duplicates from Sorted Array

- Input: A sorted array `nums`
- Output:
  - Remove all duplicated elements in `nums` in-place by keeping the result in the first part of the array
  - Return number of unique elements that should be kept
- Assumption:
  - `nums` is sorted in non-decreasing order
  - The remaining of the `nums` beyond the number of unique elements is not important
  - The input array cannot be empty
- Solution:
  - One pass for loop with one pointer from index 0:
  ```py
  class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        index = 0
        for i in range(len(nums) - 1):
            if nums[i] != nums[i+1]: # If the element is different from next
                nums[index] = nums[i] # Add the element to its correct location
                index += 1 # Move the index to search for next unique element
        nums[index] = nums[len(nums) - 1] # Add the last element as unique element
        return index + 1
  ```
  - [One pass for loop with one pointer from index 1](https://leetcode.com/problems/remove-duplicates-from-sorted-array/solutions/3676877/best-method-100-c-java-python-beginner-friendly)
  ```py
  class Solution:
      def removeDuplicates(self, nums: List[int]) -> int:
          index = 1
          for i in range(1, len(nums)):
              if nums[i] != nums[i - 1]:
                  nums[index] = nums[i]
                  index += 1
          # No need to handle last index as it starts from index 1 until the last
          return index
  ```

### 27. Remove Element

- Input: Given an array `nums` and a value `val`
- Output:
  - move all element that equals `val` to the end of the array in `nums` in-place
  - return the number of element that is not equal to `val`
- Assumption:
  - The remaining elements of `nums` are not important
  - The final order of `nums` is not important
- Solution:
  - [One Pointer Copier](https://leetcode.com/problems/remove-element/solutions/3670940/best-100-c-java-python-beginner-friendly)
  ```py
  class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        index = 0
        for i in range(len(nums)): # Foe each element in nums from left to right
            if nums[i] != val: # Copy element not equal to val to its correct index
                nums[index] = nums[i]
                index += 1 # Track the number of copied element by index
        return index
  ```
  - Two Pointers While Loop
  ```py
  class Solution:
      def removeElement(self, nums: List[int], val: int) -> int:
          last = len(nums) - 1 # Track position of the last wanted element by `last`
          first = 0 # Track number of wanted element by `first`
          while last >= first and last >= 0: # when moving last/first is completed and there is any more wanted val tracked by `last`
              if nums[last] == val: # Only move `last` to the front when it equals val
                  last -= 1
              elif nums[first] == val: # When `last` has wanted val and `first` is unwanted, swap them
                  nums[first], nums[last] = nums[last], val
                  first += 1 # track next wanted val
              else: # condition equals first and last both not equal val
                  first += 1 # track next wanted val
          return first # loop breaks after `first` is added by 1, which is also the count for wanted elements
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

  - Use `return haystack.find(needle)`

### 33. Search in Rotated Sorted Array

- Input:
  - a sorted array of distinct integers (increasing order) that is possibly rotated by unknown steps
  - a target number
- Output:
  - the index of the target of the input array, `-1` if not found
- Assumption:
  - Solution must take `O(logn)` time
- Solution:
  - Two binary search - search for pivot and then serach for target
  - Modified binary search
  ```py
  class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums) - 1 # use first element to determine the rotation property
        while l <= r:
            m = l + (r - l) // 2
            s, c = nums[l], nums[m] # get start value and mid value
            if target > c: # if target value is greater than mid value
                if s > c: # If tail is at the front
                    if target >= s:
                        r = m-1
                    else:
                        l = m+1
                else: # If tail is at the end
                    l = m+1
            elif target < c: # if target value is smaller than mid value
                if s > c: # If tail is at the front
                    r = m-1
                else: # If tail is at the end
                    if target < s:
                        l = m+1
                    else:
                        r = m-1
            else:
                return m
        return -1
  ```

### 35. Search Insert Position

- Input:
  - a sorted array of distinct integers (increasing order)
  - a target value
- Output:
  - The index of the target value or the index it should be if not exist in list
- Assumption:
  - Solution must have `O(log n)` runtime complexity
- Solution:
  - Iterative binary search
  ```py
  class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = left + (right - left) // 2
            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return left
  ```
  - Recursive binary search
  ```py
  class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        def binarySearch(nums, target, left, right):
            if left > right:
                return left
            mid = left + (right - left) // 2
            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                return binarySearch(nums, target, mid + 1, right)
            else:
                return binarySearch(nums, target, left, mid - 1)
        return binarySearch(nums, target, 0, len(nums) - 1)
        # remove the param nums and target from binarySearch method will speed up the time
  ```

### 36. Valid Sudoku

- Input:
  - A 2-D array representing sudoku game board
    - Numbers are stored as string
    - Empty space are represented by a period sign
- Output:
  - True if the board is valid
    - valid means no duplicated numbers in each row, column, and block
- Solution:
  - Track existence in arrays
  ```py
  class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        check_row = [[False] * 9 for _ in range(9)] # Init array for tracking number existence by row
        check_col = [[False] * 9 for _ in range(9)] # Init array for tracking number existence by column
        check_block = [[False] * 9 for _ in range(9)] # Init array for tracking number existence by 3x3 blocks
        for i in range(9):
            for j in range(9):
                if board[i][j] != '.':
                    check_idx = int(board[i][j]) - 1 # convert number to bool array index
                    block_idx = i//3 * 3 + j//3 # convert 9x9 index to block number from top-left to bottm-right
                    if check_row[i][check_idx] or check_col[j][check_idx] or check_block[block_idx][check_idx]:
                        return False # return false when number already existing by row, col, blocks
                    check_row[i][check_idx] = check_col[j][check_idx] = check_block[block_idx][check_idx] = True # update new numbers at its location
        return True
  ```
  - [Use a set of tuple to find duplicates](https://leetcode.com/problems/valid-sudoku/solutions/3277043/beats-96-78-short-7-line-python-solution-with-detailed-explanation)
    - Tuple `(int, str)` tracks repeated combanation of row numbers and placed number in that row
    - Tuple `(str, int)` tracks repeated combanation of col numbers and placed number in that col
    - Tuple `(int, int, str)` tracks repeated combanation of block location and placed number in that block
  ```py
  class Solution(object):
    def isValidSudoku(self, board):
        res = []
        for i in range(9):
            for j in range(9):
                element = board[i][j]
                if element != '.':
                    res += [(i, element), (j, element), (i // 3, j // 3, element)]
        return len(res) == len(set(res))
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

  - DFS (Backtracking) - Time: $$N^{\frac{T}{M}}$$ : `N` is the length of the given list, `T` is the target value, and `M` is the smallest element in the given list
    - Recursively check the combinations of `N` numbers at `T/M` depth
    - The worst case will keep repeating the smallest number and check if their sum is a solution
    - ![Tree Diagram](img/39.png)

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
    - ![Tree Diagram](img/40.png)

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

### 45. Jump Game II

- Input:
  - Given an integer array
  - Each element in the array represents the max jump distance
- Output:
  - The number of jump needed to reach the end
- Solution:
  - Selecting the longest jumps with a counter
  ```py
  class Solution:
      def jump(self, nums: List[int]) -> int:
          idx = 0
          count = 1 # Add default jump, then handle the first jump in loop
          if len(nums) == 1: return 0 # Handle edge case with zero jump
          while idx + nums[idx] < len(nums) - 1:
              next_jump = 0
              for i, v in enumerate(nums[idx + 1: idx + nums[idx] + 1]):
                  relative_jump = v - (nums[idx] - 1 - i)
                  if next_jump < relative_jump:
                      next_jump = relative_jump
                      next_idx = idx + i + 1
              idx = next_idx
              count += 1 # Add count when last jump is completed
          return count
  ```

### 46. Permutations

- Input:
  - An array of distinct integers
- Output:
  - return all the possible permutations
- Assumption:
  - The order of the answer does not matter
- Solution:
  - Backtracking
  ```py
  class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        res = []
        def backtracking(path, input):
            if not input:
                res.append(path)
                return
            for i in range(len(input)):
                backtracking(path + [input[i]], input[:i] + input[i+1:])
        backtracking([], nums)
        return res
  ```

### 48. Rotate Image

- Input:
  - given an 2D square matrix representing an image
- Output:
  - Return rotated matrix by 90 degree clockwise
- Assumption:
  - Matrix can only be replaced in-place. The allocation of another empty matrix is not allowed
- [Solution](https://leetcode.com/problems/rotate-image/solutions/18884/seven-short-solutions-1-to-7-lines/):
  - Double Flip - 90 degree clockwise rotation is equivalent to flip the rows from top to bottom and take the transpose
    - 90 degree counter-clockwise rotation is equivalent to flip the rows from left to right and take the transpose
  ```py
  class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        n = len(matrix)
        matrix.reverse() # rotate top down
        for i in range(n): # Transpose by swapping elements above the main diagonal
            for j in range(i+1, n):
                matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
  ```
  ```py
  class Solution:
      def rotate(self, A):
          A[:] = zip(*A[::-1]) # use [::-1] to flip, then use zip to transpose
  ```
  - Rotate the top-left quadrant - For every element in each quadrant, rotate it from `I` to `II`, `II` to `III`, `III` to `IV`, `IV` to `I`
  ```py
  class Solution:
      def rotate(self, A):
          n = len(A)
          for i in range(n//2):
              for j in range(n-n//2):
                  A[i][j], A[~j][i], A[~i][~j], A[j][~i] = A[~j][i], A[~i][~j], A[j][~i], A[i][j]
  ```

### 55. Jump Game

- Input:
  - Given an integer array
  - Each element in the array represents the max jump distance
- Output:
  - True if the end of the array can be reached, False if it can't
- Solution:
  - Selecting the longest jumps
  ```py
  class Solution:
    def canJump(self, nums: List[int]) -> bool:
        idx = 0 # track current index
        while idx + nums[idx] < len(nums) - 1: # While maximum jump length falls within the array
            next_jump = 0 # track the distance it can jump next
            starting_diff = nums[idx] - 1 # tracking gap between next starting point to max_jump_idx
            for i, v in enumerate(nums[idx + 1: idx + nums[idx] + 1]): # for all the possible location it can jump from
                relative_jump = v - (starting_diff - i) # get the relative jump distance from current starting point to max_jump_idx
                if next_jump < relative_jump: # find the max jump distance as next jump from last_idx
                    next_jump = relative_jump
                    next_idx = idx + i + 1 # update the starting point for next jump
            if next_jump == 0: return False # return false when max next jump is zero
            idx = next_idx
        return True
  ```
  - [Traveling Car Analogy](https://leetcode.com/problems/jump-game/solutions/4534808/super-simple-intuitive-8-line-python-solution-beats-99-92-of-users)
  ```py
  class Solution:
    def canJump(self, nums: List[int]) -> bool:
        gas = 0
        for n in nums:
            if gas < 0:
                return False
            elif n > gas:
                gas = n
            gas -= 1
        return True
  ```

### 56. Merge Intervals

- Input:
  - an array of intervals with `[start, end]` as its elements
- Output:
  - Merged array of intervals for overlapping intevals
- Solution:
  - Sort and compare start and end values
  ```py
  class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort(key=lambda x: x[0]) # sort by start value
        merged = [intervals.pop(0)] # move first interval to merged interval list for comparison
        for interval in intervals:
            prev = merged.pop() # compare last interval from merged list with current
            if interval[0] <= prev[1]: # merge when overlap
                merged += [[prev[0], max(interval[1], prev[1])]] # pick larger end value between overlapping intervals
            else: # add two lists when not overlap
                merged += [[prev[0], prev[1]], [interval[0], interval[1]]]
        return merged
  ```

### 61. Rotate List

- Input:
  - A singly linked list with the following structure
  ```py
  class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
  ```
- Output:
  - A rotated linked list moved by `k`
    - one rotation move the last node to the front
- Solution:
  - Make list a cycle and break
  ```py
  class Solution:
    def rotateRight(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        if not head: return None
        node = head
        # find list length and make it a cycle
        n = 0 # count list from first node
        while node:
            if not node.next:
                node.next = head
                n += 1 # add one more at the edge
                break
            node = node.next
            n += 1 # count number of assignment
        # break the cycle at last node at n - k%n
        for _ in range(n - k%n):
            node = node.next # first run assign head to node
        # now node is the last node
        head = node.next # get new head
        node.next = None # cut the cycle at last node
        return head
  ```

### 67. Add Binary

- Input:
  - a binary string `a`
  - a binary string `b`
- Output:
  - a binary string which is the sum of the binary `a` and `b`
- Solution:
  - Use built-in function
    - bin result in python starts with `0b` prefix
  ```py
  class Solution:
    def addBinary(self, a: str, b: str) -> str:
        return bin(int(a, 2) + int(b, 2))[2:]
  ```
  - Iterate bits from right to left
  ```py
  class Solution:
    def addBinary(self, a: str, b: str) -> str:
        extra = 0
        res = ""
        if len(a) < len(b):
            a, b = b, a # make sure a is the longer string
        j = len(b) - 1 # get last idx of b
        for i in a[::-1]: # for each char of a from right to left
            if j >= 0: # if b pointer is still valid
                c = int(b[j]) + int(i) + extra # get sum
            else: # if a still not finished
                c = int(i) + extra
            if c < 2: # prepend result
                res = str(c) + res
                extra = 0
            else: # prepend result and handle extra bit
                res = str(c%2) + res
                extra = 1
            j -= 1
        else: # if there is extra bit when iteration of a and b are finished
            if extra:
                res = "1" + res
        return res
  ```
  - Iteration method (Simplified version)
  ```py
  class Solution:
    def addBinary(self, a: str, b: str) -> str:
        if len(a) < len(b):
            a, b = b, a # make sure a is the longer string
        j = len(b) - 1 # get last idx of b
        carry = 0
        res = ""
        for i in a[::-1]: # for each char of a from right to left
            c = carry + int(i) # add carry and bit from a
            if j >= 0: # if b pointer is still valid
                c += int(b[j]) # add bit from b
                j -= 1 # update pointer
            res = str(c%2) + res # update result
            carry = c//2 # update carry
        else: # if there is extra bit when iteration of a and b are finished
            if carry:
                res = "1" + res
        return res
  ```

### 69. Sqrt(x)

- Input:
  - Given a non-negative integer
- Output:
  - return the square root of the given integer
  - rounded the result down to the nearest integer
  - answer must be `>=` zero
- Assumption:
  - Built-in function or operator is not available
- Solution:

  - Brutal - `O(n)`
  - Iterative Binary Search - `O(logN)`

  ```py
  class Solution:
      def mySqrt(self, x: int) -> int:
          l, r = 0, x # set left and right range for the binary search
          while l <= r: # Exit when l value reaches r value
              mid = l + (r-l)//2 # return mid point of r and l
              if mid * mid <= x < (mid+1)*(mid+1): return mid # check if mid is the answer
              elif x < mid * mid: r = mid - 1 # reduce mid when it's too big
              else:  l = mid + 1 # increase mid when it's too small

  ```

  - Recursive Binary Search - `O(logN)`

  ```py
  def binarySearch(l, r, x):
      if l > r: return
      mid = l + (r-l)//2
      if mid * mid <= x < (mid+1)*(mid+1): return mid
      elif x < mid * mid: return binarySearch(l, mid - 1, x)
      else: return binarySearch(mid + 1, r, x)
  class Solution:
      def mySqrt(self, x: int) -> int:
          return binarySearch(0, x, x)
  ```

  - [Newton's method I](https://leetcode.com/problems/sqrtx/solutions/2350089/very-easy-100-fully-explained-java-c-python-js-c-python3/) for solving `r^2-x=0`
    - Newton's method $$x_{n+1}=x_n+(/frac{f(x)}{f'(x)})$$

  ```py
  class Solution:
      def mySqrt(self, x: int) -> int:
          r = x
          while r*r > x: #continue to optimaize from a largest number until r square is less than x
              r = (r + x//r) // 2 # use simplified formula
          return r
  ```

  - [Newton's method II](https://leetcode.com/problems/sqrtx/solutions/2732386/o-1-solution-in-python-newton-raphson-method/)

  ```py
  class Solution:
      def mySqrt(self, x: int) -> int:
          res = x//2 + 1
          for i in range(20): # The range is beased on the size of largest number and precision (integer)
              res = res - (res*res - x)/(2 * res) # Use the original formula
          return int(res)
  ```

### 70. Climbing Stairs

- Input:
  - Number of stairs
- Output:
  - Number of possible ways of climbing if 1 or 2 steps is allowed to take each time
- Solution
  - Brutal force with dps - `O(2^n)`
    - Not practical for large `n`
  ```py
  class Solution:
      count = 0
      def climb(self, height, n):
          if height == n:
              self.count += 1 # Add a possible way when height meet target
              return
          elif height > n:
              return # Ignore when it goes beyond
          self.climb(height + 1, n) # Try climb 1 step next
          self.climb(height + 2, n) # Try climb 2 steps next
      def climbStairs(self, n: int) -> int:
          self.climb(1, n) # starts with 1 steps
          self.climb(2, n) # starts with 2 steps
          return self.count
  class Solution: # Refactor and clean up
      def climbStairs(self, n: int) -> int:
          def climb(height, n):
              if height == n:
                  return 1
              elif height > n:
                  return 0
              return climb(height + 1, n) + climb(height + 2, n)
          return climb(1, n) + climb(2, n)
  ```
  - Brutal force from top down - `O(2^n)`
    - All current step is reachable from one or two steps below
    - Starts from step `n`, get the number of ways until step `0` is reached
  ```py
  class Solution:
    def climbStairs(self, n: int) -> int:
        if n == 0 or n == 1: # handle base case to avoid reaching negative step
            return 1
        return self.climbStairs(n-1) + self.climbStairs(n-2)
  ```
  - [Fibonacci sequence with Top-Down DP](https://leetcode.com/problems/climbing-stairs/solutions/1792723/python-in-depth-walkthrough-explanation-dp-top-down-bottom-up/) - `O(n)`
    - The number of stairs and the result are the Fibonacci sequence position and its value
    - It forms a Finonacci sequence because the number of ways to each step is always the sum of the ways to reach last step and the second last step
    - Store result in a dictionary backwards
  ```py
  class Solution:
      def climbStairs(self, n: int) -> int:
          memo = {1: 1, 2: 2} # Init base case
          def climb(n):
              if n in memo:
                  return memo[n] # Return res if dict has n in keys
              else: # If n is not found
                  memo[n] = climb(n-1) + climb(n-2) # Get n from previous terms
                  return memo[n] # Return res
          return climb(n)
  class Solution: # Optionally, use python cache decorator
      @cache
      def climbStairs(self, n: int) -> int:
          if n <= 2: return n # base case
          return self.climbStairs(n - 1) + self.climbStairs(n - 2)
  ```
  - [Fibonacci sequence with Bottom-Up DP](https://leetcode.com/problems/climbing-stairs/solutions/1792723/python-in-depth-walkthrough-explanation-dp-top-down-bottom-up/)
  ```py
  class Solution:
      def climbStairs(self, n: int) -> int:
          if n <= 2: return n # Return base case early or n = 1 is too small to save base case
          dp = [0] * n # Generate list with n length
          dp[0], dp[1] = 1, 2 # Save base case
          for i in range(2, n): # Processing when n > 2
              dp[i] = dp[i - 1] + dp[i - 2]
          return dp[n-1] # find result for n with its index n - 1
  ```
  - Fibonacci sequence with Bottom-Up DP without using empty list for space optimization - `O(n)`
    ```py
    class Solution(object):
        def climbStairs(self, n):
            if n<=2: return n # handle base case
            n1, n2 = 1, 2
            for _ in range(2, n): # calculate third terms and above
                current = n1 + n2 # get sum of previous two terms
                n1, n2 = n2, current # update n1, n2
            return current
    ```

### 71. Simplify Path

- Input:
  - an absolute path for a Unix-style file system in a string
- Output:
  - A simplited path
    - remove additional `/`
    - ignore `.` if it's in the path
    - remove `..` in the middle of the path
    - treat any other dot patterns including `...` as dir names
- Solutions:
  - Reverse processing with conditional appending
  ```py
  class Solution:
    def simplifyPath(self, path: str) -> str:
        paths = path.split('/')[::-1]
        filtered_paths = []
        skip = 0
        for p in paths:
            if p == '..':
                skip += 1
            elif p and p != '.':
                if skip > 0:
                    skip -= 1
                else:
                    filtered_paths.append(p)
        return '/' + '/'.join(filtered_paths[::-1])
  ```
  - Stack
  ```py
  class Solution:
    def simplifyPath(self, path: str) -> str:
        paths = path.split('/')
        filtered_paths = []
        for p in paths:
            if p == '..':
                if filtered_paths:
                    filtered_paths.pop()
            elif p and p != '.':
                filtered_paths.append(p)
        return '/' + '/'.join(filtered_paths)
  ```

### 74. Search a 2D Matrix

- Input:
  - A `m` by `n` array with integer sorted in non-decreasing order row by row
  - A target number
- Output
  - True if the target number exists, otherwise False
- Assumption:
  - Solution must use `O(log(m*n))` time complexity
- Solution:
  - Recursive binary search by column and then row
  ```py
  class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        # Define binary search method find the closest index
        def binarySearch(input, target, left, right):
            if left > right: return right # use smaller guess value to match row index
            mid = left + (right - left) // 2
            midValue = input[mid][0] if isinstance(input[mid], list) else input[mid] # get first row value if mid value is a list when guessing row idx
            if midValue == target:
                return mid
            elif midValue < target:
                return binarySearch(input, target, mid + 1, right)
            else:
                return binarySearch(input, target, left, right - 1)
        rowIdx = binarySearch(matrix, target, 0, len(matrix)-1)
        colIdx = binarySearch(matrix[rowIdx], target, 0, len(matrix[rowIdx])-1)
        return matrix[rowIdx][colIdx] == target
  ```
  - Use `0 - n*m` based index with iterative binary search
  ```py
  class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        m, n = len(matrix), len(matrix[0])
        left, right = 0, m * n - 1
        while left <= right:
            mid = left + (right - left) // 2
            mid_row, mid_col = divmod(mid, n)
            # divmod(mid, n) returns (mid//m, mid%m)
            if matrix[mid_row][mid_col] == target: return True
            elif matrix[mid_row][mid_col] < target:
                left = mid + 1
            else:
                right = mid - 1
        return False
  ```

### 77. Combinations

- Input:
  - Two integers `n` and `k`
- Output:
  - All possible combinations `k` numbers chosen from `[1, n]`
- Assumptions:
  - The order of the answer does not matter
- Solution:
  - Backtracking
  ```py
  class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        res = []
        def backtracking(start, path):
            if len(path) == k:
                res.append(path[:])  # Append a copy of the current path
                return
            for i in range(start, n + 1):
                path.append(i)
                backtracking(i + 1, path)  # Move to the next number
                path.pop()  # Backtrack
        backtracking(1, [])
        return res
  ```

### 80. Remove Duplicates from Sorted Array II

- Input:
  - A sorted array `nums`
- Output:
  - Remove all elements that appears more than twice in `nums` in-place by keeping the result in the first part of the array
  - Return number of filtered elements that should be kept
- Assumption:
  - `nums` is sorted in non-decreasing order
  - The remaining of the `nums` beyond filtered elements is not important
  - The input array cannot be empty
- Solution:
  - Two pointer for loop
  ```py
  class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        index = 1 # Track last write location
        count = 1 # Track number of duplicates
        for i in range(1, len(nums)): # from index 1 to last
            if nums[i] != nums[i-1]: # When current is unique
                nums[index] = nums[i] # write to last edited location
                index += 1 # update write pointer
                count = 1 # reset duplicate count
            else: # for duplicated elements
                count += 1 # increase count
                if count == 2: # write only when second duplicate is met
                    nums[index] = nums[i]
                    index += 1
        return index
  ```
  - [Two pointer for loop II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/solutions/4511964/easy-o-n-python-java-go-c-beginner-friendly)
  ```py
  class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        index = 1
        occurance = 1
        for i in range(1, len(nums)):
            if nums[i] == nums[i-1]: # track occurance separately
                occurance += 1
            else:
                occurance = 1
            if occurance <= 2: # write when count is less or equal than 2
                nums[index] = nums[i]
                index += 1
        return index
  ```

### 88. Merge Sorted Array

- Input:
  - Two sorted arrays of integers, `nums1` and `nums2`
  - The lengths of the arrays, `m` and `n`
- Output:
  - A merged sorted array, completed in-place on the first array `nums1`
- Assumption:
  - For `nums1`, there will be `n` zeros appended to the right of `nums1` as input
- Solution:
  - Use built-in sort method after replacing zeros in `nums1` with each element of `nums2`
  - Assign large number amongst two arrays to `nums1` from right to left
    - Two pointers method
      ```py
      class Solution:
        def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
          i = m - 1  # Pointer for non-zero elements in nums1
          j = n - 1  # Pointer for elements in nums2
          for k in range(m + n - 1, -1, -1): # Iterate merged list backwards
            if j < 0: # All elements in nums2 have been processed
                break # No more change is needed on nums1
            elif i < 0: # All elements in nums1 have been processed
                nums1[k] = nums2[j] # Copy remaining elements from nums2 to nums1
                j -= 1
            elif nums1[i] > nums2[j]: # Current element in nums1 is larger
                nums1[k] = nums1[i] # Copy the larger element in nums1 into the current last index
                i -= 1 # Update pointer for nums1
            else: # Current element in nums2 is larger
                nums1[k] = nums2[j] # Copy the larger element in nums2 into the current last index
                j -= 1 # Update pointer for nums2
      ```
    - Simplified two pointers method
      ```py
      class Solution:
        def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
          i = m - 1
          j = n - 1
          for k in range(m + n - 1, -1, -1):
              # Summary edge cases in one condition
              if j < 0 or (i >= 0 and nums1[i] > nums2[j]):
                  nums1[k] = nums1[i]
                  i -= 1
              else:
                  nums1[k] = nums2[j]
                  j -= 1
      ```
    - While loop with three pointers method
      ```py
      class Solution:
        def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
          i = m - 1 # pointer for nums1 index
          j = n - 1 # pointer for nums2 index
          k = m + n - 1 # pointer for merged array index
          while j >= 0: # Loop until nums2 is completely processed
              # When j < 0, it will automatically break
              if i >= 0 and nums1[i] > nums2[j]:
                  nums1[k] = nums1[i]
                  i -= 1
              else:
                  nums1[k] = nums2[j]
                  j -= 1
              k -= 1
      ```

### 89. Gray Code

- Input:
  - Integer `n`
- Output:
  - An `n-bit gray code sequence` with `2^n` elements where:
    - Every integer is in the inclusive range `[0, 2^n - 1]`,
    - The first integer is `0`,
    - An integer appears no more than once in the sequence,
    - The binary representation of every pair of adjacent integers differs by exactly one bit, and
    - The binary representation of the first and last integers differs by exactly one bit
- Example:
  - Input: `n = 3`
  - Output: `[0,1,3,2]` where the binary representation is `[00,01,11,10]`
    - There are other valid outputs for a given input
- Solution

  - [XOR](https://leetcode.com/problems/gray-code/solutions/245076/4-lines-elegant-fast-and-easy-understand-python-solution/) lowest one-bit of the integer counter `i` for `n` times
    - Lowest one-bit of `i` equals `Y&(~Y+1)`, since `(~Y+1)=-Y` according 2's complement used in Python for signed integers, `Y&(~Y+1) = Y&-Y`
    - | i   | bin(i) | i&-i | output[i] |
      | --- | ------ | ---- | --------- |
      | 0   | 000    | 000  | 000       |
      | 1   | 001    | 001  | 001       |
      | 2   | 010    | 010  | 011       |
      | 3   | 011    | 001  | 010       |
      | 4   | 100    | 100  | 110       |
      | 5   | 101    | 001  | 111       |
      | 6   | 110    | 010  | 101       |
      | 7   | 111    | 001  | 100       |
    - `output[i]=output[i-1]^(i&-i)` given `output[0]=000`

  ```py
  def grayCode(self, n: int) -> 'List[int]':
    res = [0]
    for i in range(1, 2**n):
      res.append(res[-1] ^ (i & -i))
    return res
  ```

  - [Mirror Pattern](https://leetcode.com/problems/gray-code/solutions/30007/python-easy-bit-manipulation-solution/)
    - Procedure:
      - For `n=1`: 0 1
      - For `n=2`:
        - First half is results from `n=1` with leading zeros (00 01)
        - Second half the reversed result from `n=1` with leading ones (11 10)
        - As a result the output is `00 01 11 10`
      - For `n=3`:
        - First half: `00 01 11 10` add zeros -> `000 001 011 010`
        - Second half: `00 01 11 10` reverse -> `10 11 01 00` add leading ones -> `110 111 101 100`

  ```py
  def grayCode(self, n: int) -> List[int]:
      res = [0,1]
      for i in range(2,n+1): # iterate n-1 times starting from n=2 for n=3, n=4, n=5 ...
          for j in range(len(res)-1,-1,-1): # reverse first half and add leading ones for each n length
              res.append(res[j] | 1<<i-1) # Add element in second half to res one by one
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
              node = stack.pop() # Check the last element in stack which is the left most child node in tree
              res.append(node.val) # Save value
              # Save left child's right node as root, so all of its left nodes can be pushed to end of stack in next while root loop
              root = node.right
              # Visit the parent of the left leaf in next interation until stack is empty or no more right node
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

### 98. Validate Binary Search Tree

- Input:
  - The root node of a tree with the following structure
  ```py
  class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
  ```
- Output:
  - return true if its a binary search tree, or false otherwise
    - The BST will always has nodes on left side strictly smaller than root node, and nodes on the right side greater than root node for any subtrees
- Solution:
  - Check BST property: the inorder traversal will gives a sorted list
  ```py
  class Solution:
      def isValidBST(self, root: Optional[TreeNode]) -> bool:
          def convertBST(node):
              if not node: return []
              return convertBST(node.left) + [node.val] + convertBST(node.right)
          treeList = convertBST(root) # convert BST to list
          # check if list is sorted without equal adjacent values,
          for i in range(1, len(treeList)):
              if treeList[i] <= treeList[i-1]:
                  return False
          return True
          # the check can be replaced with `return sorted(treeList) == treeList and len(treeList) == len(set(treeList))`
  ```
  - Validating the BST properties during the traversal
  ```py
  class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        def validate(node, low=float('-inf'), high=float('inf')):
            if not node:
                return True
            if not (low < node.val < high):
                return False
            return (validate(node.left, low, node.val) and
                    validate(node.right, node.val, high))
        return validate(root)
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
  - DFS - Recursion - `O(n)`
    - Return true when leaf node is reached, and exit early when there is an unequal comparision
  ```py
  class Solution:
      def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
          if not p and not q: # Two node are leaf nodes
              return True # exit condition I
          if not q or not p: # Only one node is leaf node other is not
              return False # exit condition II
          if p.val != q.val: # Exit until unequality is found
              return False # exit condition III
          return self.isSameTree(p.right, q.right) and self.isSameTree(p.left, q.left) # Split comparision and use 'and' operator for all results
  ```
  - BFS - Iteration - `O(n)`
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

### 101. Symmetric Tree

- Input:
  - A binary tree
- Output:
  - True if the tree is symmetric
- Assumption:
  - root node is always not empty
- Solution:
  - Compare child nodes
  ```py
  class Solution:
      def isSymmetric(self, root: Optional[TreeNode]) -> bool:
          def isMirror(left, right): # check if two inputs has value
              if not left and not right:
                  return True # True if two are empty
              if not left or not right:
                  return False # False if only one is empty
              # If both input have value, check equality and pass the comparison to mirrored child nodes
              return left.val == right.val and isMirror(left.left, right.right) and isMirror(left.right, right.left)
          return isMirror(root.left, root.right)
  ```

### 104. Maximum Depth of Binary Tree

- Input:
  - A root node of a tree with the following structure
  ```py
  class TreeNode:
      def __init__(self, val=0, left=None, right=None):
          self.val = val
          self.left = left
          self.right = right
  ```
- Output:
  - The max depth of the tree
- Solution:
  - Recursion
  ```py
  class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if root is None:
            return 0 # Count from the lowest leaf node
        return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1 # each return from the lowest leaf node will increment the returned depth by one
  ```

### 105. Construct Binary Tree from Preorder and Inorder Traversal

- Input:
  - An array of integer generated from preorder traversal of a tree
  - An array of integer generated from inorder traversal of a tree
- Output:
  - The original tree with the following structure
  ```py
  class TreeNode:
      def __init__(self, val=0, left=None, right=None):
          self.val = val
          self.left = left
          self.right = right
  ```
- Assumption:
  - `inorder` and `postorder` array consist of unique values.
- Solution:
  - Recursive method to build subtrees - `O(n^2)`
  ```py
  class Solution:
      def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
          # preorder list helps us find root nodes and root nodes of subtrees
          # inorder list helps us find size of subtrees
          root = TreeNode(preorder.pop(0))
          self.buildSubTree(root, preorder, inorder)
          return root
      def buildSubTree(self, root, preorder, inorder):
          rootIdx = inorder.index(root.val)
          leftSize = rootIdx # the number of element on left of rootIdx
          if leftSize > 0:
              root.left = TreeNode(preorder.pop(0))
              self.buildSubTree(root.left, preorder, inorder[:rootIdx])
          rightSize = len(inorder) - 1 - rootIdx # the number of element on right of rootIdx
          if rightSize > 0:
              root.right = TreeNode(preorder.pop(0))
              self.buildSubTree(root.right, preorder, inorder[rootIdx + 1:len(inorder)])
  ```
  - Simplify by using one method - `O(n^2)`
  ```py
  class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        if not inorder: # check if more subtree can be added
            return None
        root = TreeNode(preorder.pop(0))
        index = inorder.index(root.val)
        root.left = self.buildTree(preorder, inorder[:index])
        root.right = self.buildTree(preorder, inorder[index + 1:])
        return root
  ```
  - Optimize by eliminating list slicing and index search with hashmap within each recursive call - `O(n)`
  ```py
  class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        inorderMap = {val: idx for idx, val in enumerate(inorder)}
        def buildSubTree(left: int, right: int) -> Optional[TreeNode]:
            if left > right: # check if subtree size is empty
                return None
            root = TreeNode(preorder.pop(0))
            index = inorderMap[root.val]
            root.left = buildSubTree(left, index - 1)
            root.right = buildSubTree(index + 1, right)
            return root
        return buildSubTree(0, len(inorder) - 1)
  ```

### 106. Construct Binary Tree from Inorder and Postorder Traversal

- Input:
  - An array of integer generated from inorder traversal of a tree
  - An array of integer generated from postorder traversal of a tree
- Output:
  - The original tree with the following structure
  ```py
  class TreeNode:
      def __init__(self, val=0, left=None, right=None):
          self.val = val
          self.left = left
          self.right = right
  ```
- Assumption:
  - `inorder` and `postorder` array consist of unique values.
- Solution:
  - Recursive method to build subtrees - `O(n^2)`
  ```py
  class Solution:
      def buildTree(self, inorder: List[int], postorder: List[int]) -> Optional[TreeNode]:
          # postorder root node and root of subtrees are always at the end
          # inorder list helps us find size of subtrees
          if not inorder: return
          root = TreeNode(postorder.pop())
          rootIdx = inorder.index(root.val)
          root.right = self.buildTree(inorder[rootIdx + 1:], postorder)
          root.left = self.buildTree(inorder[:rootIdx], postorder)
          return root
  ```

### 108. Convert Sorted Array to Binary Search Tree

- Input:
  - An sorted list in ascending order
- Output:
  - A balanced binary search tree
- Solution
  - Recursive method to build subtrees - `O(nlogn)`
    - `n` array slicing for `logn` recursions where `logn` is the height of the balanced tree
  ```py
  class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        # pick mid value then use it to create root node for the tree and its subtrees
        if not nums: return
        midIdx = len(nums) // 2
        node = TreeNode(nums[midIdx])
        node.left = self.sortedArrayToBST(nums[:midIdx])
        node.right = self.sortedArrayToBST(nums[midIdx+1:])
        return node
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
  - `True` if the binary tree is balanced
    - For a balanced tree, no 2 leaf nodes differ in distance from the root by more than 1
- Assumption:
  - Return `True` when tree is empty
- Solution:
  - Check depth difference between left and right child for all nodes - `O(n^2)`
    - Parent node height equals the max height between right and left child trees plus one
    - `O(n^2)` as each node will check all its child nodes for height difference
    - From the example below, each `isBalance()` will trigger the `getDepth()`, `2n` times
  ```py
  def getDepth(node): # Define a function to return the depth of any given node
      if not node: return 0
      return 1 + max(getDepth(node.left), getDepth(node.right)) # Current node depth uses the deepest child depth plus 1
  class Solution:
      def isBalanced(self, root: TreeNode) -> bool:
          if not root: return True
          # From the root check the left and right nodes' depth, and recursively check the childern nodes of the left and right nodes with the isBalanced function
          return abs(getDepth(root.left) - getDepth(root.right)) <= 1 and self.isBalanced(root.left) and self.isBalanced(root.right)
  ```
  - Check depth of nodes from bottom up - `O(n)`
    - Use DFS to track the nodes' height and mark the unbalanced node as -1 in one search
  ```py
  def dfs(root):
      if not root: return 0
      leftHeight = dfs(root.left)
      rightHeight = dfs(root.right)
      # Leaf node reached, backtracking starts from leftHeight/rightHeight equals to zero
      if leftHeight == -1 or rightHeight == -1: return -1 # if child nodes is already unbalanced
      if abs(leftHeight - rightHeight) > 1: return -1 # check if current node is balanced
      return max(leftHeight, rightHeight) + 1 # if all check passed, return node height for further comparison
  class Solution:
      def isBalanced(self, root: TreeNode) -> bool:
          return dfs(root) != -1 # Only one dfs is triggered here
  ```

### 111. Minimum Depth of Binary Tree

- Input:
  - A binary tree, `root`
- Output:
  - The min depth of the tree
    - The min depth if the shortest depth between root and its leaf
- Solution:
  - DFS
  ```py
  class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:
        if not root: return 0 # base case
        elif not root.left: return self.minDepth(root.right) + 1 # ignore min height of nodes without left leaf
        elif not root.right: return self.minDepth(root.left) + 1 # ignore min height of nodes without right leaf
        else: return min(self.minDepth(root.left), self.minDepth(root.right)) + 1
  ```

### 112. Path Sum

- Input:
  - The root node of a tree with the following structure
  ```py
  class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
  ```
  - An integer, `targetSum`
- Output:
  - True if the sum of a path of the tree from top to bottom equals `targetSum`
- Solution:
  - Find all sum in all paths and check membership using recursive dfs
  ```py
  class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        pathSum = set()
        def dfs(node, sum):
            if not node: return # base case
            sum += node.val
            if not node.left and not node.right: # check leaf node
                pathSum.add(sum)
            dfs(node.left, sum)
            dfs(node.right, sum)
            sum -= node.val
        dfs(root, 0)
        return targetSum in pathSum
  ```
  - Check sum at leaf node
  ```py
  class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        def dfs(node, sum):
            if not node: return False
            sum += node.val
            if not node.left and not node.right:
                return sum == targetSum
            else:
                return dfs(node.left, sum) or dfs(node.right, sum)
            sum -= node.val
        return dfs(root, 0)
  ```
  - Subtract `targetSum` from `hasPathSum`, so there is no need to create new inner method
  ```py
  class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root: return False
        targetSum -= root.val
        if not root.left and not root.right:
            return targetSum == 0
        return self.hasPathSum(root.left, targetSum) or self.hasPathSum(root.right, targetSum)
  ```
  - Simplify by moving data processing to parameter passing
  ```py
  class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root: return False
        if not root.left and not root.right: return targetSum - root.val == 0
        return self.hasPathSum(root.left, targetSum-root.val) or self.hasPathSum(root.right, targetSum-root.val)
  ```

### 113. Path Sum II

- Input:
  - The root node of a tree with the following structure
  ```py
  class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
  ```
  - An integer, `targetSum`
- Output:
  - List of a list of path node value that has sum equals to the `targetSum`
- Solution:
  - Check Sum of all paths
  ```py
  class Solution:
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> List[List[int]]:
        paths = []
        def dfs(node, path):
            if not node: return
            path.append(node.val)
            if not node.left and not node.right:
                if targetSum == sum(path):
                    paths.append(path.copy()) # use a copy new list instead of the reference
            dfs(node.left, path)
            dfs(node.right, path)
            path.pop()
        dfs(root, [])
        return paths
  ```
  - Make use of the return value
  ```py
  class Solution:
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> List[List[int]]:
        def dfs(node, path):
            if not node: return []
            path.append(node.val)
            res = []
            if not node.left and not node.right:
                if targetSum == sum(path):
                    res = [list(path)] # another way to create a copy
            else:
                res.extend(dfs(node.left, path)) # extend perform better than list concat as `+` create a new list, while extend only modify res in-place by adding elements from another iterable
                res.extend(dfs(node.right, path))
            path.pop()
            return res
        return dfs(root, [])
  ```
  - Use substrction to find if path sum equals target

### 116. Populating Next Right Pointers in Each Node

- Input:
  - A perfect binary tree with the following structure
  ```py
  class Node:
    def __init__(self, val: int = 0, left: 'Node' = None, right: 'Node' = None, next: 'Node' = None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next
  ```
- Output:
  - Assign next to all node to the right at the same level
- Assumption:
  - next value of all nodes are initialized as `None`
- Solution:
  - Use queue to access tree level by level
  ```py
  class Solution:
    def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
        if not root: return None
        queue = deque([root])
        last = None
        while queue:
            for _ in range(len(queue)): # Iterate nodes at the same level
                current = queue.popleft()
                if last:
                    last.next = current # connect last node with current if exists
                if current.left: # add child nodes if exists, check left only for perfect tree
                    queue.append(current.left)
                    queue.append(current.right)
                last = current # update last node
            last = None # reset last for new level
        return root
  ```
  - Recursion - track node level by level with hashmap
  ```py
  class Solution:
      def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
          connections = {}
          def connect_level(node, depth=0):
              if not node:
                  return
              # Code block before recursion call is executed from top to bottom
              if depth in connections: # if this level has prev node
                  connections[depth].next = node # assign the prev's next to current
              connections[depth] = node # update current as prev node
              connect_level(node.left, depth + 1)
              connect_level(node.right, depth + 1)
          connect_level(root)
  ```
  - Recursion - constant extra space
  ```py
  class Solution:
    def connect(self, root: Optional[Node]) -> Optional[Node]:
        def connect_nodes(node: Optional[Node]):
            if not node or not node.left:
                return
            node.left.next = node.right # connect left right child for each node
            if node.next: # connect right child to adjacent left child node from its next
                node.right.next = node.next.left
            connect_nodes(node.left)
            connect_nodes(node.right)
        connect_nodes(root)
        return root
  ```

### 121. Best Time to Buy and Sell Stock

- Input:
  - A list of stock prices by day in order
- Output:
  - The max profit one can made from one transaction
    - Profit is measured in one share
    - 0 if no profit can be made
- Assumptions
  - price is between `0` and `10000`
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
  - Simplified one pass comparision
  ```py
  class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        low = 10000
        profit = 0
        for i in prices:
            if i < low: low = i
            profit = max(i - low, profit)
        return profit
  ```

### 122. Best Time to Buy and Sell Stock II

- Input:
  - A list of stock prices by day in order
- Output:
  - The max profit one can made from multiple transactions
    - One can buy and sell on the same day
    - 0 if no profit can be made
    - Only one share is available
- Assumptions
  - price is between `0` and `10000`
- Solution:
  - One pass comparision - `O(n)`
    - Sum all the difference when price on next day is higher than the price on current day
  ```py
  class Solution:
      def maxProfit(self, prices: List[int]) -> int:
          current = 10000
          profit = 0
          for p in prices: # For all daily prices
              if p > current: # when the daily price is higher
                  profit+=p-current # sum up the profit
              current = p # make the daily price the next current price
          return profit
  ```

### 125. Valid Palindrome

- Input:
  - A String
- Output:
  - True if it is palindrome after remove all non-alphanumeric characters in lower case, or false otherwise
- Solution
  - Reverse string with slicing
  ```py
  class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = ''.join(c.lower() for c in s if c.isalnum())
        return s == s[::-1]
  ```
  - Two Pointer
  ```py
  class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = ''.join(c.lower() for c in s if c.isalnum())
        start = 0
        end = len(s) - 1
        while start < end:
            if s[start] != s[end]: return False
            start += 1
            end -= 1
        return True
  ```

### 129. Sum Root to Leaf Numbers

- Input:
  - root of a binary tree containing digit from 0 to 9
- Output:
  - The sum of number form along the path from root to leaf
- Solution:
  - Use dfs to track paths
  ```py
  class Solution:
    def sumNumbers(self, root: Optional[TreeNode]) -> int:
        paths = []
        def dfs(root, pathNum):
            if not root:
                return None
            pathNum += str(root.val) # Modify paths from inner method via reference
            # Hint if sum is stored as integer sum, it won't be editable from inner method, unless using nonlocal keyword
            if not root.left and not root.right:
                paths.append(int(pathNum))
            dfs(root.left, pathNum)
            dfs(root.right, pathNum)
        dfs(root, "")
        return sum(paths)
  ```
  - Optimized version
  ```py
  class Solution:
    def sumNumbers(self, root: Optional[TreeNode]) -> int:
        def dfs(node, current_sum):
            if not node:
                return 0
            current_sum = current_sum * 10 + node.val
            if not node.left and not node.right:
                return current_sum
            return dfs(node.left, current_sum) + dfs(node.right, current_sum)
        return dfs(root, 0)
  ```

### 130. Surrounded Regions

- Input:
  - A 2-D array with `"X"` and `"O"`
- Output:
  - Modify the board in-place, so captured regions of `"O"` are replaced by `"X"`
  - A region can be captured when its surrounded by `"X"`from all horizontally and vertically adjcent cells
- Assumption:
  - regions with `"O"` that is on the boundary of the board can not be surrounded
- Solution:
  - Change regions on boundary to `"-"`, then capture all other inner `"O"` - `O(m×n)`
  ```py
  class Solution:
    def solve(self, board: List[List[str]]) -> None:
        m, n = len(board), len(board[0])
        def dfs(i, j):
            if i < 0 or j < 0 or i >= m or j >= n or board[i][j] != "O": return # exit when area is "X" or "-" or out of boundary
            board[i][j] = "-"
            dfs(i+1, j)
            dfs(i, j+1)
            dfs(i-1, j)
            dfs(i, j-1)
        for i in range(m):
            for j in range(n):
                if i == 0 or i == m - 1 or j == 0 or j == n - 1: # Check boarder
                    dfs(i,j) # Change region on boundary to "-"
        for i in range(m): # capture inner "O" with "X" as they dont connect to "O" regions on boundary
            for j in range(n):
                if board[i][j] == "O":
                    board[i][j] = "X"
        for i in range(m): # change "-" back to "O"
            for j in range(n):
                if board[i][j] == "-":
                    board[i][j] = "O"
  ```

### 135. Candy

- Input:
  - An integer array represents a list of ratings for `n` children in line
    - The length of the array is `n`
- Output:
  - The minimum candies for all children if each child get at least one and kid with higher rating receive more candy than its neighbors
    - When two adjcent kids have same ratings there is no restriction
- Solution:
  - Divide the line and adjust the min of each sub-array
  - Use candies list to track distribution

### 141. Linked List Cycle

- Input:
  - The head of a singly linked list with the following structure
  ```py
  class ListNode:
      def __init__(self, x):
          self.val = x
          self.next = None
  ```
- Output:
  - True if the tailing node link back to any node before it, or false otherwise
- Solution:
  - Set node value to None in a single scan
  ```py
  class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        while head and head.next: # Check if list is empty and has next node
            head.val, head = None, head.next # Remove the value of the node and move on to the next node
            if head.val is None: return True # Return true if a node with its value removed is found
        return False # Return False when the list is empty or has proper tailing node with next equal to None
  ```
  - [Two pointers](https://leetcode.com/problems/linked-list-cycle/solutions/5280767/video-using-two-pointers) - Floyd's Cycle-Finding Algorithm
    - Two pointer move at two speed, if there is a circle they will eventually meet
  ```py
  class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        fast = head
        slow = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
            if fast == slow:
                return True
        return False
  ```
  - Hash Table - Store traveled node in a set
  ```py
  class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        traveled_list = set()
        while head and head.next:
            if head in traveled_list:
                return True
            traveled_list.add(head)
            head = head.next
        return False
  ```

### 146. LRU Cache

- Implement the `LRUCache` class:
  - `LRUCache(int capacity)` Initialize the LRU cache with positive size capacity.
  - `int get(int key)` Return the value of the key if the key exists, otherwise return -1.
  - `void put(int key, int value)` Update the value of the key if the key exists. Otherwise, add the key-value pair to the cache. If the number of keys exceeds the capacity from this operation, evict the least recently used key.
  - The functions get and put must each run in O(1) average time complexity.
- Solution:
  - Use dictionary stores data and list to track used order - `O(n)` due to `list.remove(idx)`
  ```py
  class LRUCache:
    def __init__(self, capacity: int):
        self.capacity = capacity
        self.order = []
        self.data = {}
    def get(self, key: int) -> int:
        if key in self.data:
            self.order.remove(key)
            self.order.append(key)
            return self.data[key]
        else:
            return -1
    def put(self, key: int, value: int) -> None:
        if key not in self.data:
            if len(self.data) == self.capacity:
                least_key = self.order.pop(0)
                del self.data[least_key]
        else:
            self.order.remove(key)
        self.order.append(key)
        self.data[key] = value
  ```
  - Use ordered dictionary - internally implemented with doubly linked list
  ```py
  class LRUCache:
    def __init__(self, capacity: int):
        self.capacity = capacity
        self.data = OrderedDict()
    def get(self, key: int) -> int:
        if key in self.data:
            self.data.move_to_end(key)
            return self.data[key]
        else:
            return -1
    def put(self, key: int, value: int) -> None:
        if key not in self.data:
            if len(self.data) == self.capacity:
                self.data.popitem(last=False)
        else:
            self.data.move_to_end(key)
        # updating an existing key will not change its order
        # new key are always placed at the end
        self.data[key] = value
  ```

### 151. Reverse Words in a String

- Input:
  - A string with words
- Output:
  - A string with words in reversed order separated by single spaces
- Assumption:
  - The original string may have multiple spaces between words or on both ends
- Solution:

  - Python string manipulation

  ```py
  class Solution:
    def reverseWords(self, s: str) -> str:
        return " ".join((s.split()[::-1]))
  ```

  - [One pass](https://leetcode.com/problems/reverse-words-in-a-string/solutions/2808468/python3-faster-than-97-without-using-split/?envType=study-plan-v2&envId=leetcode-75) solution without using the split method

  ```py
  class Solution:
    def reverseWords(self, s: str) -> str:
        res = []
        temp = ""
        for c in s:
            if c != " ":
                temp += c
            elif temp != "":
                res.append(temp)
                temp = ""
        if temp != "":
            res.append(temp)
        return " ".join(res[::-1])
  ```

### 155. Min Stack

- Build a stack class that can push, pop, top, and retrieving the minimum element in constant time (`O(1)`)
- Assumption:
  - Methods `pop`, `top` and `getMin` operations will always be called on non-empty stacks
- Solution:

  - Use a another stack called `minStack` to track the min value after each operation

  ```py
  class MinStack:

    def __init__(self):
        self.data = []
        self.minStack = []

    def push(self, val: int) -> None:
        self.data.append(val)
        if not self.minStack or val <= self.minStack[-1]:
            self.minStack.append(val) # push min value to stack when its empty or smaller than last min

    def pop(self) -> None:
        val = self.data.pop()
        if self.minStack and val == self.minStack[-1]:
            self.minStack.pop() # pop the last min if the data stack top is the min

    def top(self) -> int:
        return self.data[-1]

    def getMin(self) -> int:
        return self.minStack[-1]
  ```

### 162. Find Peak Element

- Input:
  - A list of integer
- Output:
  - The index of one of any local peak element
- Assumption:
  - First and last element only need to check if its greater than the inner elements
  - No equal adjacent elements in the given list
  - Solution must take `O(logn)` time
- Solution:
  - Modified binary search - A local peak must exist on the side with element greater than the mid
  ```py
  class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        l, r = 0, len(nums) - 1
        while l <= r:
            m = l + (r-l) // 2
            if m > 0 and nums[m] < nums[m-1]: # left element greater
                r = m - 1
            elif m < len(nums) - 1 and nums[m] < nums[m+1]: # right element greater
                l = m + 1
            else: # when peak is met or the edge of higher side is met
                return m
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
  - Solution must use only constant extra space
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
  ```py
  class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        l, r = 0, len(numbers) - 1
        while l < r:
            s = numbers[l] + numbers[r]
            if s < target:
                l += 1
            elif s > target:
                r -= 1
            else:
                return [l + 1, r + 1]
  ```
  - Two-pointer 2 - `O(n)`
    - Create two pointers where one points at the first index in the array and the other points at the second index
    - If the sum of the values at the pointers is less than the target, shift both pointers over one
    - If the values summed are greater, shift the first pointer left one

### 169. Majority Element

- Input:
  - An array `nums`
- Output:
  - The majority element which occurs more than half of the size of the array
- Solution:
  - Sorting and check the two ends of the first half
  ```py
  class Solution:
    def majorityElement(self, nums: List[int]) -> int:
      n = len(nums)
      nums.sort()
      for i in range(n-n//2):
        if nums[i] == nums[i+n//2]:
        return nums[i]
  ```
  - [Sorting and check midpoint](https://leetcode.com/problems/majority-element/solutions/3676530/3-method-s-beats-100-c-java-python-beginner-friendly)
  ```py
  class Solution:
    def majorityElement(self, nums: List[int]) -> int:
      nums.sort()
      n = len(nums)
      return nums[n//2]
  ```
  - Hash Map
  ```py
  class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        counters = {}
        for i in nums:
          counters[i] = counters.setdefault(i, 0) + 1
          if counters[i] > len(nums)//2: # Return once count is greater than half size
            return i
  ```
  - [Moore Voting Algorithm](https://leetcode.com/problems/majority-element/solutions/3676530/3-method-s-beats-100-c-java-python-beginner-friendly)
    - Use a candidate to vote against all other numbers from left to right, the last candidate will be the majority number
    - The majority element will be selected as candiate eventually, no matter when it gets selected
    - All other element will be "consumed" by the mojority element if it is not selected
  ```py
  class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        count = 0
        candidate = 0
        for i in nums: # In one pass
            if count == 0: # Assign new candidate When count is zero
                candidate = i
                count = 1
            elif i == candidate:
                count += 1 # add count if current element is same as candidate
            else:
                count -= 1 # consume a vote if current element is different
        return candidate # return the surviving candidate
  ```

### 189. Rotate Array

- Input:
  - An integer array `nums`
  - An integer `k`
- Output:
  - An integer array which has all element in `nums` rotate to the right by `k` steps
- Assumption:
  - `k` is greater or equal than `0`
- Solution
  - Move element groups to the right by `k` steps with two `temp` variables
    - The element group is consisted of all elements from one element at a starting point plus all others `k` steps after it, if the end of the array is reached the pointer can wrap around until it repeat itself
    - There are a set number of element groups that can cover all elements in the array
    - The number of group is defined as the GCD of the length of `nums` and `k`
    - The starting point for each group starts at index `0` then increment by `1` for the next group if the GCD is greater than `1`
  ```py
  class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        n = len(nums)
        groups = gcd(k, n)
        for j in range(groups): # for each starting point at j
            last_num = nums[j]
            for i in range(1, n//groups + 1): # the number of each element group is n//groups
                next_num = nums[(i*k+j)%n]
                nums[(i*k+j)%n] = last_num
                last_num = next_num
  ```
  - Swap element groups between the first and the next `k`'s elements
  ```py
  class Solution:
  def rotate(self, nums: List[int], k: int) -> None:
      n = len(nums)
      groups = gcd(k, n)
      for j in range(groups):
          for i in range(1, n//groups + 1):
              # Swap element between first element in each group and the next element in the group
              nums[j], nums[(i*k+j)%n] = nums[(i*k+j)%n], nums[j]
  ```

### 191. Number of 1 Bits

- Input:
  - a positive integer `n`
- Output:
  - The number of set bits (ones) in its binary form
    - The hamming weight of `n`
- Solution
  - Built-in function
  ```py
  class Solution:
    def hammingWeight(self, n: int) -> int:
        return bin(n).count('1')
  ```
  - Bit Manipulation
  ```py
  class Solution:
    def hammingWeight(self, n: int) -> int:
      count = 0
      while n:
          count += n & 1  # Increment count if the last bit is 1
          n >>= 1  # Right shift decimal number by 1 in its binary form to process the next bit
      return count
  ```
  - Brian Kernighan's Algorithm
  ```py
  class Solution:
    def hammingWeight(self, n: int) -> int:
      count = 0
      while n: # As long as there is a one in its binary representation
          n &= (n - 1)  # Change the rightmost 1 bit to 0 bit of its binary representation
          count += 1
      return count
  ```

### 198. House Robber

- Input:
  - An array of integer
- Output:
  - The max sum if the picked numbers cannot be adjacent with each other
- Solution:
  - Recursive Top-Down Brutal Force
    - From the last number, there are two options at each number
      - Take the current - Get the sum of the current plus the max sum until reaching second number before
      - Skip the current - Get the max sum until one before the current
  ```py
  class Solution:
      def rob(self, nums: List[int]) -> int:
          def rob_helper(nums, i): # `i` tracks the location to be selected
              if i < 0: return 0 # base case when it goes beyand top case
              return max(rob_helper(nums, i - 2) + nums[i], rob_helper(nums, i - 1)) # choose the max between not skip or skip
          return rob_helper(nums, len(nums) - 1)
  ```
  - DP Top-Down using dictionary
  ```py
  class Solution:
    def rob(self, nums: List[int]) -> int:
        def rob_helper(nums, i, memo):
            if i < 0: return 0
            if i in memo: return memo[i] # if result exists, return immediately
            memo[i] = max(rob_helper(nums, i - 2, memo) + nums[i], rob_helper(nums, i - 1, memo))
            return memo[i]
        memo = {}
        return rob_helper(nums, len(nums) - 1, memo)
  ```
  - DP Top-Down using list
  ```py
  class Solution:
    def rob(self, nums: List[int]) -> int:
        def rob_helper(nums, i, memo):
            if i < 0: return 0
            if memo[i] >= 0: return memo[i] # if result exists, return immediately
            memo[i] = max(rob_helper(nums, i - 2, memo) + nums[i], rob_helper(nums, i - 1, memo))
            return memo[i]
        memo = [-1] * len(nums) # init list with -1
        return rob_helper(nums, len(nums) - 1, memo)
  ```
  - DP Bottom-Up - From the second number there are the same two options from the Top-Down approach
  ```py
  class Solution:
    def rob(self, nums: List[int]) -> int:
        if len(nums) == 0: return 0
        dp = [0] * (len(nums) + 1) # init result list with an extra position at beginning with value zero
        dp[0], dp[1] = 0, nums[0] # for the first number, max sum is always itself
        for i in range(1, len(nums)): # start looping from the second number
            dp[i + 1] = max(dp[i], dp[i - 1] +  nums[i])
        return dp[len(nums)]
  ```
  - DP Bottom-Up with space optimization
  ```py
  class Solution:
    def rob(self, nums: List[int]) -> int:
        if len(nums) == 0: return 0
        prev1 = prev2 = 0
        for num in nums:
            prev1, prev2 = max(prev2 + num, prev1), prev1
        return prev1
  ```

### 200. Number of Islands

- Input:
  - A 2-D array with `"1"`represents land and `"0"` represents water
- Output:
  - Number of island that are formed by consecutive lands
- Assumption:
  - land can only connects horizontally and vertically
  - The size of grid is from `1x1` to `300x300`
- Solution:
  - Iterate through all cells, find land and its adjcent land using dfs, then change it to water and increment island count
    - `O(m×n)` - The dfs function is called once for each cell that contains a `"1"`
  ```py
  class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        m, n = len(grid), len(grid[0]) # find grid size
        def dfs(i,j): # check four direction, stop when index out of bound or reach water
            if i < 0 or j < 0 or i == m or j == n or grid[i][j] == "0": return
            grid[i][j] = "0" # Change tracked cell to water
            dfs(i,j+1)
            dfs(i+1,j)
            dfs(i,j-1)
            dfs(i-1,j)
        count = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == "1": # get starting point from top-left
                    count += 1 # count number of starting point
                    dfs(i,j) # change all adjcent lands to the starting point to water
        return count
  ```

### 202. Happy Number

- Input:
  - An integer
- Output:
  - True if it is a happy number, or false otherwise
    - Happy number will end up as 1 if keep calculating the square sum of its digits
    - Unhappy number will stuck in a loop and never reach 1
- Solution
  - Loop detection with hashset
    - store intermidiate result to hash set
    - check duplicates before proceeding
  ```py
  class Solution:
      def isHappy(self, n: int) -> bool:
          hset = set()
          while n != 1:
              if n in hset: return False # Try to add input first
              hset.add(n)
              n = sum([int(i)**2 for i in str(n)])
          return True
  ```

### 205. Isomorphic Strings

- Input:
  - Two strings `s` and `t`
- Output:
  - True if two strings are isomorphic
    - Isomorphic means one string can become the other one by changing characters only
    - `aa` can be changed to any other letters with the same form, like `bb` or `zz`
    - Isomorphic must be true from `s` to `t` and from `t` to `s`
- Assumption:
  - two strings have the same length
- Solution:
  - Use dictionary to map letters and list of indices, then compare dict values
  ```py
  class Solution:
      def isIsomorphic(self, s: str, t: str) -> bool:
          s_map = {}
          t_map = {}
          for i in range(len(s)):
              s_map[s[i]] = s_map.setdefault(s[i], []) + [i]
              t_map[t[i]] = t_map.setdefault(t[i], []) + [i]
          return list(s_map.values()) == list(t_map.values())
  ```
  - Use dictionary to map letters from `s` and letter from `t` at the same location
  ```py
  class Solution:
      def isIsomorphic(self, s: str, t: str) -> bool:
          if len(set(s)) != len(set(t)): # Check if s has more unique characters that can be added in the st_dict without returning false
              return False
          st_dict = {}
          for i in range(len(s)):
              if s[i] not in st_dict: # Add coresponding letter in `t` as the value of first seen letter in `s`
                  st_dict[s[i]] = t[i]
              elif st_dict[s[i]] != t[i]: # Check if repeated letter in `s` has same corresponding letter in `t`
                  return False
          return True
  ```

### 207. Course Schedule

- Input:
  - An array of course id
  - An array of prerequisite relations where an element `[a, b]` indicates `b` is a prerequisite of `a`
- Output:
  - `True` if all courses can be taken, otherwise return `False`
- Solution:
  - Build graph with course-pre map, then use dfs to find cycle
  ```py
  class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        # Create Course-Prerequisites Map
        courseMap = defaultdict(list)
        for course, pre in prerequisites:
            courseMap[course].append(pre)
        # Define dfs to traverse through course graph
        traveled = set()
        def dfs(course):
            if course in traveled: return False # cycle found if course already been added
            if course not in courseMap: return True # can finish course when pre has no pre
            traveled.add(course) # add newly traveled course
            for pre in courseMap[course]: # travel the pre of current course
                if not dfs(pre): return False # check loop
            traveled.remove(course) # reset traveled set to parent node
            del courseMap[course] # speed up process by removing pre of checked course
            return True # return True when no return in last loop
        # Find cycle for each course in courseMap's key
        for course in list(courseMap.keys()):
            if not dfs(course): return False # return false when at least one if false
        return True
  ```

### 208. Implement Trie (Prefix Tree)

- Implement a trie/prefix tree structure:
  - `Trie()` Initializes the trie object.
  - `void insert(String word)` Inserts the string word into the trie.
  - `boolean search(String word)` Returns true if the string word is in the trie (i.e., was inserted before), and false otherwise.
  - `boolean startsWith(String prefix)` Returns true if there is a previously inserted string word that has the prefix `prefix`, and false otherwise.
- Solution
  - Nested dictionary
  ```py
  class Trie:
      def __init__(self):
          self.root={}
      def insert(self, word: str) -> None:
          cur=self.root
          for letter in word:
              if letter not in cur:
                  cur[letter]={}
              cur=cur[letter]
          cur['*']='' # insert "apple" will get {'a': {'p': {'p': {'l': {'e': {'*': ''}}}}}}
      def search(self, word: str) -> bool:
          cur=self.root
          for letter in word:
              if letter not in cur:
                  return False
              cur=cur[letter]
          return '*' in cur
      def startsWith(self, prefix: str) -> bool:
          cur=self.root
          for letter in prefix:
              if letter not in cur:
                  return False
              cur=cur[letter]
          return True
  ```

### 209. Minimum Size Subarray Sum

- Input:
  - An array of positive integers `nums`
  - A target integer
- Output:
  - The small subarray that has sum greater or equal to the target
- Assumption:
  - max length is smaller than or equal to `100000`
- Solution:
  - Sliding Window - Track the smallest subarray by adding element from the right until sum is greater than target, then remove the leftmost element and use the second as starting point, then repeat
  ```py
  class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        end, min_span, n, sub_sum = 1, 100001, len(nums), nums[0]
        for start in range(n): # For each element
            while end < n and sub_sum < target:
                sub_sum += nums[end]
                end += 1 # increase subarray size and update sum if small
            if sub_sum >= target: # update smallest size if subarray is found
                span = end - start
                if min_span > span:
                    min_span = span
            sub_sum -= nums[start] # remove first element in subarray for next starting point
        if min_span > 100000: return 0 # return 0 when no subarray is found
        return min_span
  ```

### 210. Course Schedule II

- Input:
  - An array of course id
  - An array of prerequisite relations where an element `[a, b]` indicates `b` is a prerequisite of `a`
- Output:
  - A valid order of course to be taken, otherwise return `[]`
- Solution:
  - Topological Sort - `O(Edge+Node)`
  ```py
  class Solution:
    def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
        prereq = {c:[] for c in range(numCourses)}
        for crs, pre in prerequisites:
            prereq[crs].append(pre)
        output = []
        visit, cycle = set(), set()
        def dfs(crs):
            if crs in cycle: return False # if cycle is formed
            if crs in visit: return True # if the course has been validated
            cycle.add(crs) # record the courses in path
            for pre in prereq[crs]: # for each prereq course of the course
                if not dfs(pre): return False # check its prereq with dfs
            cycle.remove(crs) # cleanup path
            visit.add(crs) # track visited node
            output.append(crs) # add the subnode as prereq in order
            return True
        for c in range(numCourses): # check each course in range
            if not dfs(c): return []
        return output # otherwise return result
  ```

### 211. Design Add and Search Words Data Structure

- Design a data class which has the following methods:
  - `WordDictionary()` Initializes the object.
  - `void addWord(word)` Adds word to the data structure, it can be matched later.
  - `bool search(word)` Returns true if there is any string in the data structure that matches word or false otherwise. word may contain dots '.' where dots can be matched with any letter.
- Solution:
  - Trie structure with modified search using BFS for wildcard `.`
  ```py
  class WordDictionary:
      def __init__(self):
          self.root = {}
      def addWord(self, word: str) -> None:
          cur = self.root
          for letter in word:
              if letter not in cur:
                  cur[letter]={}
              cur = cur[letter]
          cur['*'] = None
      def search(self, word: str) -> bool:
          stack = [(self.root, word)]
          while stack:
              node, remaining_word = stack.pop()
              if not remaining_word:
                  if '*' in node:
                      return True
                  continue
              first_char = remaining_word[0]
              if first_char == '.':
                  for child in node:
                      if child != '*':
                          stack.append((node[child], remaining_word[1:]))
              else:
                  if first_char in node:
                      stack.append((node[first_char], remaining_word[1:]))
          return False
  ```
  - Trie stucture with modified search using DFS for wildcard `.`
  ```py
  class WordDictionary:
      def __init__(self):
          self.root = {}
      def addWord(self, word: str) -> None:
          cur = self.root
          for letter in word:
              if letter not in cur:
                    cur[letter]={}
              cur = cur[letter]
          cur['*'] = None
      def search(self, word: str) -> bool:
          return self.dfs(self.root, word)
      def dfs(self, node, word: str) -> bool:
          if not word:
              return '*' in node
          first_char = word[0]
          if first_char == '.':
              for child in node:
                  if child != '*':
                      if self.dfs(node[child], word[1:]):
                          return True
              return False
          else:
              if first_char in node:
                  return self.dfs(node[first_char], word[1:])
              return False
  ```

### 215. Kth Largest Element in an Array

- Input:
  - An integer array
  - An integer `k`
- Output:
  - The kth largest integer in the given array
- Assumtion:
  - Sorting is not allowed
- [Solution](https://leetcode.com/problems/kth-largest-element-in-an-array/solutions/3906260/100-3-approaches-video-heap-quickselect-sorting/?envType=study-plan-v2&envId=leetcode-75):
  - Min-heap
  ```py
  class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        k_heap = [] # init new heap list
        for num in nums:
            if len(k_heap) < k: # add element until there are k of them
                heapq.heappush(k_heap, num)
            else: # add k+1th and remove extra
                heapq.heappushpop(k_heap, num)
        return k_heap[0] # return smallest of the k largest in heap
        # one liner solution - return heapq.nlargest(k, nums)[-1]
  ```
  - Quickselect - Find nth max/min in a list by returning the nth element when it is selected as the pivot point
  ```py
  class Solution:
      def findKthLargest(self, nums: List[int], k: int) -> int:
          res, greater, lesser = 0, [], []
          pivot = nums.pop()
          for x in nums:
              if x >= pivot:
                  greater += [x]
              else:
                  lesser += [x]
          if len(greater) + 1 == k:
              return pivot
          elif len(greater) + 1 > k: # if pivot is too left
              res = self.findKthLargest(greater, k)
          else: # if pivot is too right
              res = self.findKthLargest(lesser, k-len(greater)-1)
          return res
  ```

### 217. Contains Duplicate

- Input:
  - An array of integers
- Output:
  - true if any value appears at least twice, or false otherwise
- Solutions:
  - Hashmap with set
  ```py
  class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        bins = set()
        for n in nums:
            if n in bins:
                return True
            bins.add(n)
        return False
  ```

### 219. Contains Duplicate II

- Input:
  - An array of integers
  - An integer, `k`
- Output:
  - true if any value appears at least twice within nearest `k`, or false otherwise
- Solution:
  - Hashmap stores element as key and index as value
  ```py
  class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        map = {}
        for i in range(len(nums)):
            if nums[i] in map:  # Only need to check last saved as its closest
                if i - map[nums[i]] <= k: # i is always greater than saved index
                    return True
            map[nums[i]] = i
        return False
  ```

### 222. Count Complete Tree Nodes

- Input:
  - A root of a complete binary tree with the following structure
  ```py
  class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
  ```
- Output:
  - The number of node in tree
- Solution:
  - Use class variable during tree traversal - `O(n)`
  ```py
  class Solution:
    count = 0
    def dfs(self, node):
            if not node: return
            self.count += 1
            self.dfs(node.left)
            self.dfs(node.right)
    def countNodes(self, root: Optional[TreeNode]) -> int:
        self.dfs(root)
        return self.count
  ```
  - Return plue one during tree traversal - `O(n)`
  ```py
  class Solution:
    def countNodes(self, root: Optional[TreeNode]) -> int:
        if root is None: return 0
        return 1 + self.countNodes(root.left) + self.countNodes(root.right)
  ```
  - Compare left boundary height and right boundary height to check perfect subtrees - `O(log^2N)`
    - For a perfect tree with height `h`, it has `2^h-1` nodes
  ```py
  class Solution:
    def countNodes(self, root: Optional[TreeNode]) -> int:
        if not root: return 0
        leftHeight = self.getLeftHeight(root)
        rightHeight = self.getRightHeight(root)
        if leftHeight == rightHeight: # If left and right boundary height is same, the tree is perfect
            return 2 ** leftHeight - 1 # Add the nodes from a perfect tree using its height
        else: # If subtree is not perfect add root node count and check its child nodes
            return 1 + self.countNodes(root.left) + self.countNodes(root.right)
    def getLeftHeight(self, node): # Get left boundary height
        height = 0
        while node:
            height += 1
            node = node.left
        return height
    def getRightHeight(self, node): # Get right boundary height
        height = 0
        while node:
            height += 1
            node = node.right
        return height
  ```
  - Compare left boundary height of subnodes
  ```py
  class Solution:
    def countNodes(self, root: Optional[TreeNode]) -> int:
        def leftHeight(node):
            height = 0
            while node:
                height += 1
                node = node.left
            return height
        if not root:
            return 0
        leftNodeHeight = leftHeight(root.left)
        rightNodeHeight = leftHeight(root.right)
        if leftNodeHeight == rightNodeHeight:
            # Left subtree is full, count its nodes plus the root and recurse on right subtree
            return (1 << leftNodeHeight) + self.countNodes(root.right)
        else:
            # Right subtree is full (one less level), count its nodes plus the root and recurse on left subtree
            return (1 << rightNodeHeight) + self.countNodes(root.left)
  ```

### 226. Invert Binary Tree

- Input:
  - A root of a binary tree with the following structure
  ```py
  class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
  ```
- Output:
  - A root with all the values from each nodes left/right node inverted
- Solution:
  - Pre-order traversal
  ```py
  class Solution:
      def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
          if root: # Only process node that is not none, Exit on none nodes
              root.left, root.right = root.right, root.left # Switch
              self.invertTree(root.left) # Call switch recursively on left nodes
              self.invertTree(root.right) # Call switch recursively on right nodes
          return root # return root when reaching this line after all recursions are finished
  ```
  - BFS
  ```py
  class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root: return
        stack = [root]
        while stack:
            node = stack.pop()
            node.left, node.right = node.right, node.left
            if node.left: stack.append(node.left)
            if node.right: stack.append(node.right)
        return root
  ```

### 228. Summary Ranges

- Input:
  - A sorted integer array in ascending order
- Output:
  - Summarize the consecutive number into intervals
- Example:
  - Input: `nums` = `[0,1,2,4,5,7]`
  - Output: `["0->2","4->5","7"]`
- Solution:
  - Compare adjacent pairs
  ```py
  class Solution:
      def summaryRanges(self, nums: List[int]) -> List[str]:
          intervals = []
          output = []
          left = 0
          for i in range(1, len(nums)): # for each pair of adjacent numbers starting from 0 and 1
              if nums[i] != nums[i - 1] + 1: # if they are not incremented by 1
                  intervals.append([nums[left], nums[i - 1]]) # record the intervals
                  left = i # update left boundary
          if nums: intervals.append([nums[left], nums[-1]]) # handle edge cases for empty list and record the last interval
          for s in intervals: # Format the output from interval to string
              if s[0] == s[1]:
                  output.append(str(s[0]))
              else:
                  output.append(f"{s[0]}->{s[1]}")
          return output
  ```

### 230. Kth Smallest Element in a BST

- Input:
  - A binary search tree `root`
  - An integer `k`
- Output:
  - The kth smallest element
- Solution:
  - Inorder Traversal in binary search tree
  ```py
  class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        self.idx = 1 # Use conter to count sorted traversal result
        self.res = 0 # Store the target element value
        def inOrderTraversal(node):
            if not node: return
            inOrderTraversal(node.left)
            if self.idx == k:
                self.res = node.val
            self.idx += 1
            inOrderTraversal(node.right)
        inOrderTraversal(root)
        return self.res
  ```

### 238. Product of Array Except Self

- Input:
  - An array of integer `nums`
- Output:
  - An array of integer `answer` where `answer[i]` equals the product of all elements except `nums[i]`
- Assumption:
  - All integers can fit in a 32-bit integer
  - Solution must be `O(n)` in time
  - Division operation is not allowed in the solution
- Solution:
  - Using pre-calculated prefix/suffix product array
    - Each product at `i` is essentially the product of all numbers the left of `i` times the product of all numbers the right of `i`
    - The summary all prefix product and suffix product for each element at `i` can optimaize the solution to `O(n)`
    ```py
    class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        length = len(nums)
        pre_array, suf_array = [1]*length, [1]*length
        for i in range(1, length):
            pre_array[i] = pre_array[i-1] * nums[i-1]
            suf_array[length-i-1] = suf_array[length-i] * nums[length-i]
        return [pre_array[i] * suf_array[i] for i in range(length)]
    ```
  - O(1) Space complexity solution excluding space taken by solution array
  ```py
  class Solution:
      def productExceptSelf(self, nums: List[int]) -> List[int]:
          n = len(nums)
          res = [1] * n # only one answer array is declared
          suffix = 1
          for i in range(1, n):
              res[i] = res[i-1]*nums[i-1] # Get Prefix product array
          for i in range(n-1, -1, -1):
              res[i] *= suffix # Track suffix product with integer
              suffix *= nums[i] # Update to answer array from right to left
          return res
  ```

### 242. Valid Anagram

- Input:
  - String, `s`
  - String, `t`
- Output:
  - True if two strings can be equal by reordering the letters, or false otherwise
- Solution:
  - Counter
  ```py
  class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return Counter(s) == Counter(t)
  ```

### 274. H-Index

- Input:
  - An array list number of citations for each published papers of a researcher
- Output:
  - The H-Index of this researcher
    - The H-Index is the highest number `h` such that a researcher has published `h` papers, each of which has been cited at least `h` times
- Solution:
  - Sorting and counting - After sorting citation in descending order the first `h` paper with more than `h` citation indicates the `h` index
  ```py
  class Solution:
    def hIndex(self, citations: List[int]) -> int:
        n = len(citations)
        citations.sort(reverse=True)
        for i in range(n):
            if citations[i] < i + 1: # return when citation is less than paper number
                return i
        return n # if all citations are greater than paper count, return papaer number
  ```

### 290. Word Pattern

- Input:
  - A pattern string like `aaa` or `abc`, each pattern represent a word
  - A string of words separated by empty spaces
- Output:
  - True if the string follows the pattern
- Example:
  - Input:
    - pattern = "abba", s = "dog cat cat dog"
  - Output:
    - True
- Solution:
  - Use dictionary to store pattern letter as key and represented word as value
  ```py
  class Solution:
    def wordPattern(self, pattern: str, s: str) -> bool:
        pattern_map = {}
        words = s.split()
        if len(set(words)) != len(set(pattern)): # Check same words represented by different patterns
            return False
        if len(words) != len(pattern): # Check equal length
            return False
        for i in range(len(pattern)):
            pattern_symbol = pattern[i]
            if pattern_symbol not in pattern_map: # Save pattern as key and word as value
                pattern_map[pattern_symbol] = words[i]
            elif pattern_map[pattern_symbol] != words[i]: # Check same pattern with different value
                return False
        return True
  ```
  - [Use the conditions for bijectivity](https://leetcode.com/problems/word-pattern/solutions/2977027/python-3-2-lines-w-explanation-t-s-95-99)
    - The counts of distinct elements in two groups and the count of distinct mappings are all equal
    - `zip_longest` This method creates pairs of corresponding elements from `pattern` and `s`
      - If one of the list is longer, the paired value from the shorter list will be filled with `None`
  ```py
  class Solution:
    def wordPattern(self, pattern: str, s: str) -> bool:
        s = s.split()
        return (len(set(pattern)) ==
                len(set(s)) ==
                len(set(zip_longest(pattern,s))))
  ```
  - Use two sets to track new pattern and words, then use a dictionary to track new mapping
  - Store mapping in a dictionary and use pattern to reconstruct `s` string then compare it with the original `s`

### 300

- Input:
  - Given an integer array `nums`
- Output:
  - The length of the longest strictly increasing subsequence
- Solution:
  - Optimized DP - tracks the the smallest possible tail values from substring of size 1 in an array called `sub`
  ```py
  import bisect
  def lengthOfLIS(nums):
      sub = []
      for num in nums:
          # Find the index to replace using binary search
          idx = bisect.bisect_left(sub, num)
          if idx == len(sub):
              sub.append(num)  # If num is larger than all elements in sub
          else:
              sub[idx] = num  # Replace existing value with a smaller one
      return len(sub)
  ```

### 322. Coin Change

- Input:
  - A list of integer representing coin types
  - A target number
- Output:
  - The min number of coins required to form the target number
- Solutions:
  - DP - decision-making process is to decide whether using or not using the each coin when forming the best result for target amount from 0 to the target number
    - Bottom-Up Approach
    ```py
    def coinChange(coins, amount):
        dp = [float('inf')] * (amount + 1)
        dp[0] = 0
        for coin in coins:
            for i in range(coin, amount + 1):
                dp[i] = min(dp[i], dp[i - coin] + 1)
        return dp[amount] if dp[amount] != float('inf') else -1
    ```
    - Top-Down Approach
    ```py
    def coinChange(coins, amount):
        memo = {}
        def dfs(remaining):
            if remaining == 0:
                return 0
            if remaining < 0:
                return float('inf')
            if remaining in memo:
                return memo[remaining]
            min_coins = float('inf')
            for coin in coins:
                min_coins = min(min_coins, dfs(remaining - coin) + 1)
            memo[remaining] = min_coins
            return min_coins
        result = dfs(amount)
        return result if result != float('inf') else -1
    ```

### 334. Increasing Triplet Subsequence

- Input:
  - an integer array `nums`
- Output:
  - True if `nums[i] < nums[j] < nums[k]`, where indices `i < j < k`
- Solution:

  - [If-else one pass](https://leetcode.com/problems/increasing-triplet-subsequence/solutions/3549612/python-easy-solution/?envType=study-plan-v2&envId=leetcode-75)

  ```py
  class Solution:
    def increasingTriplet(self, nums: List[int]) -> bool:
        first = second = float('inf')
        for n in nums:
            if n <= first: # find the smallest as first
                first = n # update new first whenever n is smaller
            elif n <= second: # find any value that is larger than first and lower than any historical second value
                second = n # keep the lowest second value until third is found
            else:
                return True # return whenever a third value is bigger than second
        return False
  ```

### 338. Counting Bits

- Input:
  - a number `n`
- Output:
  - A list of hamming weight for numbers from `0` to `n`
- Solution:
  - DP (Bottom-up)
  ```py
  class Solution:
    def countBits(self, n: int) -> List[int]:
        ans = [0] * (n + 1)
        for i in range(1, n + 1):
            ans[i] = ans[i >> 1] + (i & 1)
            # same as, ans[i] = ans[i // 2] + (i & 1)
        return ans
  ```

### 345. Reverse Vowels of a String

- Input:
  - A string
- Output:
  - A string with its vowels replaced in reversed order
- Assumptions:
  - Vowels can be in both lower/uppercases
- Solution:

  - One pass with two pointer

  ```py
  class Solution:
      def reverseVowels(self, s: str) -> str:
          vowels = ['a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U']
          s = list(s) # list performs faster
          end = len(s) - 1 # Track the index of the second vowel from the back
          for i in range(len(s)):
              if i == end: break # return when first letter reaches the latest index of the second
              if s[i] in vowels:
                  for j in range(end, i, -1):
                      end = j - 1
                      if s[j] in vowels:
                          s[i], s[j] = s[j], s[i]
                          # s = s[:i] + s[j] + s[i+1:j] + s[i] + s[j+1:] # slower alternatives without list conversion
                          break
                  if end == i+1: return ''.join(s) # Return when the second vowel is not found after all remaining letter are checked from the back
          return ''.join(s)
  ```

### 355. Design Twitter

- Implement the Twitter class with the following methods:

  - `Twitter()` Initializes your twitter object.
  - `void postTweet(int userId, int tweetId)` Composes a new tweet with ID tweetId by the user userId. Each call to this function will be made with a unique tweetId.
  - `List<Integer> getNewsFeed(int userId)` Retrieves the 10 most recent tweet IDs in the user's news feed. Each item in the news feed must be posted by users who the user followed or by the user themself. Tweets must be ordered from most recent to least recent.
  - `void follow(int followerId, int followeeId)` The user with ID followerId started following the user with ID followeeId.
  - `void unfollow(int followerId, int followeeId)` The user with ID followerId started unfollowing the user with ID followeeId.

- Solution

```py
class Twitter:

    def __init__(self):
        self.tweetMap = defaultdict(list) # mapping from userID to list of tweetID
        self.tweetTime = [] # a list of tweet id tracks posting order
        self.followingMap = defaultdict(set) # mapping from follower to followee set

    def postTweet(self, userId: int, tweetId: int) -> None:
        self.tweetMap[userId].append(tweetId)
        self.tweetTime.append(tweetId)

    def getNewsFeed(self, userId: int) -> List[int]:
        relatedUsers = {userId} | self.followingMap.get(userId, set())
        tweetQuery = []
        for user in relatedUsers:
            tweetQuery.extend(self.tweetMap.get(user, []))
        feed = []
        for tweet in self.tweetTime[::-1]: # iterate from most recent
            if tweet in tweetQuery:
                feed.append(tweet)
                if len(feed) == 10:
                    break
        return feed

    def follow(self, followerId: int, followeeId: int) -> None:
        if followerId != followeeId:  # Prevent self-following
            self.followingMap[followerId].add(followeeId)

    def unfollow(self, followerId: int, followeeId: int) -> None:
        if followeeId in self.followingMap[followerId]:
            self.followingMap[followerId].remove(followeeId)
    # TODO - can use heap, can replace tweetTime list into a time counter integer
```

### 373. Find K Pairs with Smallest Sums

- Input:
  - two integer arrays sorted in non-decreasing order
  - an integer, `k`
- Output:
  - `k` pairs of elements from two array with the smallest sums
- Assumption:
  - A pair is valid as long as the combination of index from two arrays is unique
  - There will be duplicated elements in an array
- Solution:
  - Brutal force `sorted(itertools.product(nums1, nums2), key=sum)[:k]`
  - Brutal force on heap `heapq.nsmallest(k, itertools.product(nums1, nums2), key=sum)`
  - Brutal force with itertools that computes result as needed - Takes `O(m + k*log(m))` time and `O(m)` extra space
  ```py
  class Solution:
    def kSmallestPairs(self, nums1, nums2, k):
        streams = map(lambda u: ([u+v, u, v] for v in nums2), nums1)
        stream = heapq.merge(*streams) # merge lists of tuples from stream in to one sorted list of tuples
        return [suv[1:] for suv in itertools.islice(stream, k)] # use islice instead of index slicing for better performance
  ```
  - Push and pop element pair `(0, 0)`, then `(0, 1)` and `(1, 0)` into heap, pop smallest and push `(i+1, j)` and `(i, j+1)` of the pop one
  ```py
  class Solution:
    def kSmallestPairs(self, nums1, nums2, k):
      queue = []
      def push(i, j):
        if i < len(nums1) and j < len(nums2):
          heapq.heappush(queue, [nums1[i] + nums2[j], i, j])
      push(0, 0)
      result = []
      while queue and len(result) < k:
        _, i, j = heapq.heappop(queue)
        result.append([nums1[i], nums2[j]])
        push(i, j + 1)
        if j == 0:
          push(i + 1, 0)
      return result
  ```
  - Push pair of first `k` of `nums1` and first of `nums2` into heap, pop smallest and push the next pair containing second element from `nums2` - `O(klogk)`
  ```py
  class Solution:
    def kSmallestPairs(self, nums1, nums2, k):
        result, queue, length2 = [], [], len(nums2)
        for i in range(k): # for the first k element in nums1
            if i < len(nums1): # in case k is over the length of nums1
                heapq.heappush(queue, [nums1[i] + nums2[0], i, 0]) # push pair contains (sum, i, j=0)
        while len(result) < k and queue:
            total, idx1, idx2 = heapq.heappop(queue)
            result.append([nums1[idx1], nums2[idx2]]) # push popped smallest result
            if idx2 + 1 < length2: # push the next pair containing next element in nums2 into the priority queue if exists
                heapq.heappush(queue, [nums1[idx1] + nums2[idx2 + 1], idx1, idx2+1])
        return result  # Return the k smallest pairs
  ```

### 380. Insert Delete GetRandom O(1)

- Implement the RandomizedSet class with each function works in average `O(1)` time complexity
  - `RandomizedSet()` - Initializes the RandomizedSet object.
  - `bool insert(int val)` - Inserts an item val into the set if not present. Returns true if the item was not present, false otherwise.
  - `bool remove(int val)` - Removes an item val from the set if present. Returns true if the item was present, false otherwise.
  - `int getRandom()` Returns a random element from the current set of elements (it's guaranteed that at least one element exists when this method is called). Each element must have the same probability of being returned.
- Solution

  - Data array plus value/index mapping
    - Use an array to store the list data
    - Use a dictionary tracks the mapping between value and location, the value is stored as key for existence check

  ```py
  class RandomizedSet:

    def __init__(self):
        self.map = {} # Use dict to track element and index
        self.data = [] # Use list to store data

    def insert(self, val: int) -> bool:
        if val in self.map:
            return False
        else:
            self.map[val] = len(self.data) # use previous len as new element idx
            self.data.append(val) # add element to data list
            return True

    def remove(self, val: int) -> bool:
        if val in self.map:
            self.data[self.map[val]] = self.data[-1] # Assign last element to the removing location
            self.map[self.data[-1]] = self.map[val] # update last element index in self.map
            self.data.pop() # remove last element
            del self.map[val] # delete the key for val
            return True
        else:
            return False

    def getRandom(self) -> int:
        return random.choice(self.data)
  ```

### 383. Ransom Note

- Input:
  - A string `ransomNote`
  - A string `magazine`
- Output:
  - True if `ransomNote` can be constructed by using the letters from the `magazine`, or false otherwise
    - Each letter can be only used once
- Assumption:
  - Both strings contain only lowercase letters
- Solution:
  - Counter method
  ```py
  from collections import Counter
  class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
      mag_count = Counter(magazine)
      ran_count = Counter(ransomNote)
      for k, v in ran_count.items():
        if v > mag_count.get(k, 0): return False
      return True
  ```
  - Simplified Counter
  ```py
  class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        return not (Counter(ransomNote) - Counter(magazine)) # return True if the substracted counter is empty
  ```
  - [Replace first occurrence](https://leetcode.com/problems/ransom-note/solutions/5442404/solution-by-dare2solve-detailed-explanation-clean-code)
  ```py
  class Solution:
      def canConstruct(self, ransomNote: str, magazine: str) -> bool:
          for char in magazine: # for each char in magazine
              ransomNote = ransomNote.replace(char, '', 1) # remove one letter from ransomNote
          return ransomNote == '' # True if no letter from ransomNote is left
  ```

### 392. Is Subsequence

- Input:
  - A string `s`
  - A string `t`
- Output:
  - True is `s` is a subsequence of `t`, or false otherwise
    - A subsequence is obtain by removing some characters from the original string
- Solutions:
  - Two Pointer
  ```py
  class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        i, j = 0, 0 # i tracks t index, j tracks s index
        while i < len(t) and j < len(s):
            if t[i] == s[j]: # when match is found in order
                j += 1 # move to next char of the subsequence
            i += 1 # each iteration compare one char from the original string
        return j == len(s) # check if all char in s has a match
  ```

### 399. Evaluate Division

- Input:
  - A list of string pairs
    - each string represents a variable for a large number
  - A list of number represents the result of division of the pairs from left to right
  - A list of string pairs that to be queried
- Output:
  - A list of number represents the division result of the queries
- Assumption:
  - Indeterminate result is `-1`
- Solution:
  - graph method
  ```py
  class Solution:
    def calcEquation(self, equations: List[List[str]], values: List[float], queries: List[List[str]]) -> List[float]:
        graph = defaultdict(dict)
        # Build the graph
        for (dividend, divisor), value in zip(equations, values):
            graph[dividend][divisor] = value # add two way paths as keys and qoutient as value
            graph[divisor][dividend] = 1 / value
        def dfs(start, end, visited):
            if start not in graph or end not in graph:
                return -1.0 # return -1 if input from query doesn't exist in graph
            if start == end:
                return 1.0 # base case when end is reached
            visited.add(start) # use visited set to prevent cycling
            for neighbor, value in graph[start].items(): # from all possible paths from start
                if neighbor not in visited:
                    result = dfs(neighbor, end, visited) # continue explore connected paths until neighbor is the end
                    if result != -1.0: # if result if valid
                        return result * value # accumulate qoutient by multiplication
            visited.remove(start) # backtracking remove visited node after all its paths are explored
            return -1.0 # return -1 by default
        results = []
        for dividend, divisor in queries: # find answers for all queries
            results.append(dfs(dividend, divisor, set()))
        return results
  ```

### 443. String Compression

- Input:
  - An array of characters
- Output:
  - Compress the input array by letters and the number of duplicated letters it follows as single chars
  - Return the length of the compressed array in integer
- Assumption:
  - Modify the input array in place
- Solution:

  - Two pointer - tracks the start location of each unique letter and number of deplicated letters

  ```py
  class Solution:
    def compress(self, chars: List[str]) -> int:
      ans = 0 # track compressing progress
      i = 0 # tracks reading progress
      while i < len(chars):
          letter = chars[i] # for each letter in the loop
          count = 0 # no duplicated letter is found yet
          # For each remaining letters in current loop if duplicated letter is found
          while i < len(chars) and chars[i] == letter:
              count += 1
              i += 1
          chars[ans] = letter # output result
          ans += 1
          if count > 1: # Handling digit to chars in output
              for c in str(count):
                  chars[ans] = c
                  ans += 1
      return ans
  ```

### 530. Minimum Absolute Difference in BST

- Input:
  - A binary search tree, `root`
- Output:
  - The smallest difference between each nodes
- Assumption:
  - Value of each node is between 0 and 100000
- Solution:
  - In Order Traversal
    - It returns sorted values
  ```py
  class Solution:
    def getMinimumDifference(self, root: Optional[TreeNode]) -> int:
        self.prev = -100000 # Generate biggest diif for root node val
        self.minDiff = 100000 # Assume it has largest diff
        def inOrderTraversal(node):
            if not node: return
            inOrderTraversal(node.left)
            # Check current node val with previous node val and take min diff
            self.minDiff = min(node.val - self.prev, self.minDiff)
            self.prev = node.val
            inOrderTraversal(node.right)
        inOrderTraversal(root)
        return self.minDiff
  ```

### 605. Can Place Flowers

- Input:
  - An integer array `flowerbed` containing `1` or `0` - `1` means the plot is planted with flower, `0` means it's empty
  - An integer - The number of new flowers to be planted in the flowerbed with empty adjacent plots
- Output:
  - A boolean - True if all new flowers can be planted and False otherwise
- Solution:

  - One pass
    - Counting the number of consecutive empty plots of 3, 5, 7 etc...
    - For edge cases add `[1, 0]` and `[0, 1]` on both side so the first and last empty plots in the `flowerbed` can be treated as potential plots correctly

  ```py
  class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        counter, plot = 0, 0
        for i in [1,0] + flowerbed + [0,1]:
            if i == 1:
                plot += int((counter-1)/2)
                counter = 0
            else:
                counter += 1
            # Optimization: Early stopping when available plot count starts to surpass requested plot number
            if plot == n: return True
        return plot >= n

  ```

### 637. Average of Levels in Binary Tree

- Input:
  - The `root` of a binary tree
- Output:
  - A list of average values amongst all elements in each level of the given tree
- Assumption:
  - The answer is accurate to the fifth decimal places
- Solution:
  - [BFS](https://leetcode.com/problems/average-of-levels-in-binary-tree/solutions/1874688/easy-bfs-recursion-solution-90-w-beginner-level-interview-notes)
  ```py
  class Solution:
    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
        q, ans = deque([root]), [] # Init a double-ended queue
        while q:
            qlen=len(q)
            row = 0
            for _ in range(qlen): # for each element in the current depth level
                node = q.popleft() # get and remove the left most element
                row += node.val # Incre the value
                if node.left: q.append(node.left) # add child to queue if exists
                if node.right: q.append(node.right)
            ans.append(row/qlen) # Get the avg of the current level
        return ans
  ```
  - DFS
  ```py
  class Solution:
    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
        tree_dict = {}
        def dfs(node, level):
            if not node: return
            if level in tree_dict:
                tree_dict[level] += [node.val]
            else:
                tree_dict[level] = [node.val]
            dfs(node.left, level + 1)
            dfs(node.right, level + 1)
        dfs(root, 0)
        # The order of keys start from top to bottom since data is added before recursive calls
        # After python 3.7, the order of key are kept based on its creation order
        return [mean(v) for v in tree_dict.values()]
  ```
  - DFS simplied with defaultdict data type
  ```py
  class Solution:
    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
        tree_dict = defaultdict(list)
        def dfs(node, level):
            if not node: return
            tree_dict[level].append(node.val) # empty list will be assigned if key does not exist
            dfs(node.left, level + 1)
            dfs(node.right, level + 1)
        dfs(root, 0)
        return [mean(v) for v in tree_dict.values()]
  ```

### 643. Maximum Average Subarray I

- Input:
  - an integer array `nums` with length `n`
  - an integer `k`
- Output:
  - The max average value of a contiguous subarray of `nums` with length `k`
- Assumption:
  - Calculation error should be within `10^-5`
- Solution:

  - Brutal, compose subarray and each max in one pass `O(n*k)`

  ```py
  class Solution:
      def findMaxAverage(self, nums: List[int], k: int) -> float:
          max_sum = float('-inf')
          for i in range(len(nums)-k+1):
              cur_sum = sum(nums[i:k+i])
              if max_sum < cur_sum: max_sum = cur_sum
          return round(max_sum/k, 5) # return the average after dividing by k
  ```

  - Sliding Window - Use the previous sum to get the next sum by substracting leaving element on the left and adding incoming element on the right

  ```py
  class Solution:
      def findMaxAverage(self, nums: List[int], k: int) -> float:
          cur_sum = sum(nums[:k])
          max_sum = cur_sum
          for i in range(len(nums)-k):
              next_sum = cur_sum - nums[i] + nums[i+k]
              cur_sum = next_sum
              if max_sum < cur_sum: max_sum = cur_sum
          return round(max_sum/k, 5) # return the average after dividing by k
  ```

### 647. Palindromic Substrings

- Input:
  - A string
- Output:
  - The number of substring which is a palindrome
- Solution:

### 700. Search in a Binary Search Tree

- Input:
  - Root of a binary search tree
  - an integer `val`
- Output:
  - The node with value `val`
  - Return `None` if not found
- Solution:

  - Recursive search

  ```py
  # Definition for a binary tree node.
  # class TreeNode:
  #     def __init__(self, val=0, left=None, right=None):
  #         self.val = val
  #         self.left = left
  #         self.right = right
  class Solution:
      def searchBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
          if not root: return None
          elif val == root.val: return root
          elif val > root.val: return self.searchBST(root.right, val)
          else: return self.searchBST(root.left, val)

  ```

### 724. Find Pivot Index

- Input:
  - Integer array
- Output:
  - The pivot index where the sum of left subarray equals sum of right subarray
- Assumption:
  - The element on the pivot index is not included when calculating the sum
  - Return the first index when equal
  - left sum is `0` when index is at `0`
- Solution:

  - Update both sum in one pass from the left

  ```py
  class Solution:
      def pivotIndex(self, nums: List[int]) -> int:
          left, right, nums = 0, sum(nums), [0]+nums
          for i in range(1, len(nums)):
              left += nums[i-1]
              right -= nums[i]
              if left == right: return i-1
          return -1
  ```

### 684. Redundant Connection

- Input:
  - A list of `n` edges of a graph represented `[i, j]` where `i` and `j` are the node numbers
- Output:
  - The last edge in the list that can make the graph a tree if it is removed
- Solution:

  - Union Find

  ```py
  class UnionFind:
      def __init__(self, n):
          # Initialize parent and rank arrays for 0-based indexing
          self.parent = list(range(n))
          self.rank = [1] * n

      def find_parent(self, x):
          # Find the root of x with path compression
          if self.parent[x] != x:
              self.parent[x] = self.find_parent(self.parent[x])
          return self.parent[x]

      def union(self, v1, v2):
          # Find roots of v1 and v2
          p1, p2 = self.find_parent(v1), self.find_parent(v2)
          # If they are already in the same set, a cycle is detected
          if p1 == p2:
              return False
          # Union by rank: attach the smaller tree under the larger one
          if self.rank[p1] > self.rank[p2]:
              self.parent[p2] = p1
              self.rank[p1] += self.rank[p2]
          else:
              self.parent[p1] = p2
              self.rank[p2] += self.rank[p1]
          return True

  class Solution:
      def findRedundantConnection(self, edges: List[List[int]]) -> List[int]:
          graph = UnionFind(len(edges)+1) # input node starting from 1 to n
          # Process each edge in the graph
          for v1, v2 in edges:
              # If union fails, the edge creates a cycle and is redundant
              if not graph.union(v1, v2):
                  return [v1, v2]
  ```

### 973. K Closest Points to Origin

- Input:
  - An integer `k`
  - A list of integer coordinates `(x, y)`
- Output:
  - the `k` coordinates closest to origin `(0, 0)`
- Assumption:
  - The order of the result doesn't matter
- Solutions
  - heap
  ```py
  class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        distanceHeap = []
        for x, y in points:
            heapq.heappush(distanceHeap, (-(x*x+y*y), x, y))
            if len(distanceHeap) > k:
                heapq.heappop(distanceHeap)
        return [list(distance[1:]) for distance in distanceHeap]
  ```

### 1071. Greatest Common Divisor of Strings

- Input:
  - Two Strings
- Output:
  - The largest string that divides both given strings
  - A string divides string `x` when it can be formed by `x` concatenated with itself one or more times
- Solution:

  - Brutal Force - `O(min(m,n)*(m+n))` where `m`, `n` are the length of the given strings
    - Check if the shorter input string is divisible by both given strings
    - Reduce the length of the shorter one letter at a time and check the divisibility in each iteration

  ```py
  class Solution:

      def check_div(self, divisor, dividend):
          if len(dividend)%len(divisor) == 0:
              quotient = int(len(dividend)/len(divisor))
              return quotient * divisor == dividend
          else:
              return False

      def gcdOfStrings(self, str1: str, str2: str) -> str:
          short_str = str1 if len(str1) < len(str2) else str2
          for i in range(len(short_str)):
              if i==0:
                  check_str = short_str
              else:
                  check_str = short_str[:-i]
              if self.check_div(check_str, str1) and self.check_div(check_str, str2):
                  return check_str
          return ''
  ```

  - GCD Function
    - Check if GCF exists by interchange the string and check check for equality
    - Use the `gcd()` method from math package to find the length of repeated gcd string

  ```py
  class Solution:
    def gcdOfStrings(self, str1: str, str2: str) -> str:
        return str1[:gcd(len(str1),len(str2))] if str1 + str2 == str2 + str1 else ''
  ```

### 1207. Unique Number of Occurrences

- Input:
  - an array of integers `arr`
- Output:
  - `true` if the number of occurrences of each value in the array is unique or `false` otherwise
- Solution:

  - Sort, count and save count in list, then check duplication
  - Save values' frequency as key in dictionary and check duplicated counters by using set length

  ```py
  class Solution:
    def uniqueOccurrences(self, arr: List[int]) -> bool:
        arr_dict = {}
        for n in arr: arr_dict[n] = arr_dict.get(n, 0) + 1 # get frequency map
        return len(set(arr_dict.values()))  == len(arr_dict) # check number of unique counts

  ```

### 1431. Kids With the Greatest Number of Candies

- Input:
  - List of integer `candies` - the number of candies each kid has
  - Integer `extraCandies` - the number of candies that to be given for one of the kids
- Output:
  - List of boolean - true if the kid at each index will possess the most candies if extra candies are given to it
- Assumption:
  - Multiple kids can have the greatest number of candies
- Solution

  - One pass

  ```py
  class Solution:
    def kidsWithCandies(self, candies: List[int], extraCandies: int) -> List[bool]:
        return [extraCandies + candy >= max(candies) for candy in candies]
  ```

### 1492. The kth Factor of n

- Input:
  - An integer `n`
  - An integer `k`
- Output:
  - the `k`th factor of `n` if all its factors are order in ascending order
- Solutions:
  - Iteration from `1` to `n` - `O(n)`
  ```py
  class Solution:
    def kthFactor(self, n: int, k: int) -> int:
        factors = []
        for i in range(1, n+1):
            if n % i == 0:
                factors.append(i) # add factor when found
        res = -1 if len(factors) < k else factors[k-1] # return kth if exists
        return res
  ```
  - Iteration from `1` to `n` with counter to save space - `O(n)`
  ```py
  class Solution:
    def kthFactor(self, n: int, k: int) -> int:
        count = 0
        for i in range(1, n + 1):
            if n % i == 0:
                count += 1
                if count == k:
                    return i
        return -1
  ```
  - Iteration from `1` to `sqrt(n)` - `O(sqrt(n))`
  ```py
  class Solution:
    def kthFactor(self, n: int, k: int) -> int:
        lowerFactors = [] # Store factors from 1 to sqrt(n)
        upperFactors = [] # Store factors reversely for co-factors
        for i in range(1, int(n**0.5) + 1):
            if n % i == 0:
                lowerFactors.append(i)
                if i != n // i:  # Avoid adding the square root twice
                    upperFactors.append(n // i) # use // to get integer, / returns a float
        factors = lowerFactors + upperFactors[::-1]
        return factors[k - 1] if k <= len(factors) else -1
  ```

### 1732. Find the Highest Altitude

- Input:
  - An integer array where each element indicates the altitude different between each road trip
- Output:
  - The highest altitude amongst the end of all trips
- Altitude:
  - The starting point has altitude `0`
- Solution:

  - Creating altitude array and get max

  ```py
  class Solution:
    def largestAltitude(self, gain: List[int]) -> int:
        alt = [0]
        for diff in gain:
            alt.append(alt[-1]+diff)
        return max(alt)
        # One Liner Equivalent
        # return max([0]+accumulate(gain))
  ```

  - Track max in one pass

```py
class Solution:
    def largestAltitude(self, gain: List[int]) -> int:
        max_alt, last_alt = 0, 0
        for diff in gain:
            last_alt += diff
            max_alt = max(max_alt, last_alt)
        return max_alt
```

### 1768. Merge Strings Alternately

- Input:
  - Two words
- Output:
  - Merged string letter by letter altervatively from both words, and append remaining letters from the longer word
- Solution:

  - One While loop for both strings

  ```py
  class Solution:
      def mergeAlternately(self, word1: str, word2: str) -> str:
          merged = ""
          while word1 or word2:
              if word1: merged += word1[0]
              word1 = word1[1:]
              if word2: merged += word2[0]
              word2 = word2[1:]

          return merged
  ```

### 2215. Find the Difference of Two Arrays

- Input:
  - Two integer arrays
- Output:
  - A 2-D array with two elements where:
    - First element contains a list unique elements in first array but not in second
    - Second element contains a list unique elements in second array but not in first
- Assumption:
  - The order doesn't matter
- Solution:

  - HashSet operation

  ```py
  class Solution:
    def findDifference(self, nums1: List[int], nums2: List[int]) -> List[List[int]]:
        set1, set2 = set(nums1), set(nums2)
        return [list(set1-set2), list(set2-set1)]
  ```
