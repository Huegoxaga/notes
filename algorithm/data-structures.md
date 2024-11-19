# Data Structures

- Data structure is a systematic way of organizing and accessing data.

## Integer

- Unsigned interger has range `[0, 2^bitSize - 1]` where the `bitSize` is the number of bits
- Signed interger has range `[-2^(bitSize-1), 2^(bitSize-1) - 1]` where the `bitSize` is the number of bits

## Array

- An ordered collection of data.
- It has indices for access the elements, usually starts at 0 from left to right.
- It has a fixed size, defined when the array is declared.

## List

- like an array but its size can be changed after the declaration.
- The first element in the list has index = 0.
- Every element on the list other than the first has a predecessor.
- Every element on the list other than the last has a successor.

### Array List

- They are Lists data structures designed base on array data structures.
- Also known as vector in C++ or earliest versions of Java.
- It internally declares a new array everything when the list size changes.
- Dynamic array is a technique used to improve the data structure. It always declares some empty elements on both sides of the array to lower the chances for creating and copying the array, every time the array change sizes.
- It uses contiguous allocation, list elements occupy consecutive memory locations.
  - Insertion or deletion of elements in the middle of the list involves the laborious relocation of all elements that come after.
- It allows random access access elements by jumping to any given element without going through its predecessors.

### Linked List

- A type of list that treats all of its elements as nodes.
- The nodes not only has the value for the element, it also stores a reference(link) to its adjacent elements.
- The reference to a linked list is just the reference to the head node.
- It uses linked allocation.
- It uses sequential access, it accesses nodes starting from the head all the time.
- This type of data structure is referred to a self-referential structure or recursive data structure.
- An empty list is represented with a head reference whose value is null.
- Link Lists have the following types:
  - Singly Linked Lists - All of its node has a reference to the next node of the list.
    - The first node is called the head, the last node is call the tail.
    - The tail node has a null reference.
  - Circularly Linked Lists - When a singly linked list has its tail node reference to the head node, the head and the tail are connected to form a circularly linked list.
  - Doubly Linked Lists - All of its node not only has a reference to the next node, but also has a reference to the previous node.
    - provide easy access to both side of certain node.
    - There is header node at the beginning and tailer node at the end.
    - Header node and tailer node do not store data. Together, they are called sentinels or guards, to protect the boundary, because either next node or previous node of the sentinels are not defined.
- Removing Nodes
  - To remove the first node of a list, set the head reference to its successor.
  - To remove a node other than the first, set a reference to the predecessor of the targeted node. Route the successor link in the predecessor around the targeted node.

### Positional List

- It uses a cursor instead of indices to locate each elements.

## Stack

- It is a collection of objects are inserted and removed according to the last-in, first-out principle.
- It is originated from a stack of plates in a spring-loaded, cafeteria plate dispenser.
- Inserting data is called push, removing data is called pop.
- A stack can be implemented by using an array to hold the items being stored.
  - need a variable called `top` which stores the end index(the first empty slot) for the stack in the array.
  - The exception thrown when an attempt is made to push a value onto a stack whose array if full is called a stack overflow exception.
  - The exception thrown when an attempt is made to pop an empty stack is sometimes called stack underflow.
- ArrayList can be used to create a generic stack structure.
- A linked list can be used to implement a stack by using the head node object of the list as the "top" of the stack.

## Queue

- Queues are first-in, first-out. It has a first come, first server principle.
- Adding data to the `rear` is called enqueue, removing data from the `front` is call dequeue.
- For an array-based implementation, it should:
  - track the front and rear of the array. Adding new elements and removing old elements in order of increasing index.
  - wrap around to the beginning of the array when the queue reaches the end.
  - Use an integer variable to track the size.
- A linked list can be used to implement a queue.
  - The head of the linked list is used as the front of the queue.
  - The end of the linked list is used as the rear of the queue.

### Priority Queue

- A queue that has all of its element with a priority key.
- When dequeuing an element the priority key is considered first. Then, among all the elements with the highest priority, first-in, first-out.
- The key can be called minimal key. When represented by an integer, usually a lower number has a higher priority.

## Deck

- It also known as double-ended queues.
- It supports insertion and deletion at both the front and the end of the queue.

## Tree

- It stores objects in a hierarchical structure, like a tree.
- The top node is called the root.
- Each node(except root) has one parent node, and zero or more child node.
- All nodes with a common parent are called siblings.
- A node is called internal if it has a child node.
- A node is called external or leaf if it has no child node.
- An edge of a tree is a pair of a node with parent and child relationship, the order does not matter.
- A path of a tree is a serial of nodes with direct parent and child relationships.
- The depth is used to describe how many levels a node is below the root node.
- The height is used to describe the max depth among all nodes for a tree.
- The subtree is generated by treating a tree's node as the root of a new tree.
- nodes on one the same path have the ancestor and descendant relationship.

### Ordered Tree

- A tree structure that place all the sibling nodes in an order.

### Binary Tree

- All of the nodes have at most two children.
- The children of the nodes are described as the left child and the right child.
  - The left child may be a root of a left subtree, the same for the right child.
- The children are ordered as the left child is the first child.
- For a proper binary tree, all of its internal nodes have two children. Otherwise, it can be called an improper binary tree.
- Traversal of a tree is a way of access all nodes of a tree.
- It can be implemented using the same concept as a linked-list. Each node will have a value and two links to the left child node and right child node.
  - A binary tree is represented by a reference to its root node.
  - An empty binary tree is represented with a reference whose value is null.
- There are three recursive traversal techniques for binary tree:
  - `Preorder traversal` - visits the root first, and then recursively traverses the left and right subtrees.(recursive methods for left and right subtree run last)
  - `Inorder traversal` - traverses the left subtree, then visits the root, and then traverses the right subtree.(recursive methods for left subtree run first, recursive methods for right subtree run last)
    - traverses in a sorted order, from smallest to largest.
  - `Postorder traversal` - traverses the left and right subtrees, and then visits the root.(recursive methods for left and right subtree run first)
- Types of binary trees:
  - `Full Binary Tree` is a Binary Tree in which every node has 0 or 2 children
  - `Complete Binary Tree` has all levels completely filled with nodes except the last level and in the last level, all the nodes are as left side as possible at the last level
  - `Perfect Binary Tree` is a Binary Tree in which all internal nodes have 2 children and all the leaf nodes are at the same depth or same level
    - For a perfect binary tree with height `h`, it has `2^h-1` nodes
  - `Balanced Binary Tree` is a Binary tree in which height of the left and the right sub-trees of every node may differ by at most `1`
  - `Degenerate(or Pathological) Binary Tree` is a Binary Tree where every parent node has only one child node
- Application of binary trees:
  - `Binary Search Tree` - Used in many search applications where data is constantly entering/leaving, such as the map and set objects in many languages' libraries.
    - Left child is always smaller than the root, Right child is always bigger than the root.
    - In a binary search tree (BST), an in-order traversal is used to return a sorted (ordered) list of data
    - To implement the binary search tree, adding and searching methods are recursive with base cases that check if the root is empty and non-base case that traverses the tree.
    - To remove a node in the binary search tree. There are three cases:
      - Removal of a Leaf Node
      - Removal of a Node with a single child
      - Removal of a node with two child node
        - successor of a node is smallest node from its right subtree
          - For leaf node successor, it is the highest parent node that is the right subnode of its parent
        - predecessor of a node the largest node from its left subtree
        - For this case, the node will be replaced by its successor or predecessor, then reorganinze the rest
  - `Binary Space Partition` - Used in almost every 3D video game to determine what objects need to be rendered.
  - `Binary Trees` - Used in almost every high-bandwidth router for storing router-tables.
  - `Hash Trees` - used in p2p programs and specialized image-signatures in which a hash needs to be verified, but the whole file is not available.
  - `Huffman Coding Tree` - used in compression algorithms, such as those used by the .jpeg and .mp3 file-formats.
  - `Syntax Tree` - Constructed by compilers and (implicitly) calculators to parse expressions.
  - `T-tree` - Though most databases use some form of B-tree to store data on the drive, databases which keep all (most) their data in memory often use T-trees to do so.

### Heap

- It can be used to implement priority queue, perform sort with heap sort, and implement algorithms like Dijkstra’s shortest path and Prim’s minimum spanning tree
- A heap is always a complete binary tree
- There are two types of heap
  - In a max-heap, the child node key is always greater or equal to its parent node key.
  - In a min-heap, the child node key is always smaller or equal to its parent node key.
- When represented by an array, the element is in order from top to bottom layer by layer, from left to right
- For heap with `n` nodes, the height of a heap, height of the root equals `θ(lgn)`, or `floor(lgn)`
- When the root is `A[1]`
  - Parent of `A[i] = A[floor(i/2)]`
  - Left child of `A[i] = A[2i]`
  - Right child of `A[i] = A[2i+1]`
- Insert a node into a min-heap:
  1. Insert the new node at the next available position (bottom-most, left-most spot)
  2. Bubble up (heapify up): Compare the new node with its parent
  3. If the new node is smaller (bigger for max-heap) than its parent, swap them
  4. Repeat step 3 until the heap property is restored (or the node reaches the root)
- Delete a node from a min-heap:
  1. Replace the root with the last node (bottom-most, right-most node)
  2. Remove the last node
  3. Bubble down (heapify down): Compare the new root with its smallest child
  4. If the new root is larger than its smallest child, swap them
  5. Repeat step 3 until the heap property is restored (or the node becomes a leaf)
- Insertion and deletion takes of heap tree with `n` nodes take `O(lgn)` time as those operations iterate along its height

## Maps

- It has a collection of key-value pairs(also called entries or mapping).
- Key can be of any data type, and they are unique.
- It is also known as associative arrays.
- The key and value are generally not stored in the same object.

### Hash table

- A structure that help implement maps.
- In a hash table all possible keys in a map can found its associated integer values in the table.
- It use hash function or hash algorithm is consist of hash code and compression function.
  - Hashcode finds or converts the integer value of all keys in the ordered hash table.
    - A good hash code can avoid getting the same integer value as much as possible(avoid collisions).
    - For Integer objects, you can use the integer value of the object (or its absolute value).
    - For Character objects, you can use the UNICODE value for the character.
    - For String objects, you can use a function that takes into account the UNICODE values of the characters that make up the string, as well as the position occupied by each character.
    - For Object types, you can use some function on the non-mutable components of the object.
  - Compression function generate and rearrange the new collection that has the same length as the map.

### Multimap

- They are maps that allows a key maps to multiple values.

### Linked Map

- A ordered map.
- Generally based on the insertion order.

## Set

- A unordered collection of elements, contains unique values only.
- Support membership operation for sets defined in Math.
- Internally Set are treated as Keys of a map.
- The hash function for HashSet has the following features.
  - Elements are usually broken down into groups by the compression function, then they are stored in an array of bucket.
  - Each bucket can have an array of element for the same group.
  - Each bucket has an array of elements with the same length.

### Multiset

- Also known as bag, are set that allow duplicated values.

### Linked Set

- An ordered Set.
- Generally based on the insertion order.

