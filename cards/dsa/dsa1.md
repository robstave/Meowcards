# Data Structures and Algorithms Interview Questions

<!-- Card Start -->

### Front

What is the time complexity of accessing an element in an array by index?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n²)

### Back

**Correct Answer**: A) O(1)

**Explanation**: Arrays provide constant time access to elements when you know the index, as the memory address can be calculated directly using the formula: base_address + (index × element_size).

<!-- Card End -->

<!-- Card Start -->

### Front

Which data structure follows the LIFO (Last In, First Out) principle?

A) Queue  
B) Stack  
C) Array  
D) Linked List

### Back

**Correct Answer**: B) Stack

**Explanation**: A stack follows the LIFO principle where the last element added is the first one to be removed. Operations include push (add) and pop (remove) from the top.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the worst-case time complexity of binary search?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n log n)

### Back

**Correct Answer**: B) O(log n)

**Explanation**: Binary search repeatedly divides the search space in half, resulting in logarithmic time complexity. This requires the array to be sorted.

<!-- Card End -->

<!-- Card Start -->

### Front

Which sorting algorithm has the best average-case time complexity?

A) Bubble Sort  
B) Selection Sort  
C) Merge Sort  
D) Insertion Sort

### Back

**Correct Answer**: C) Merge Sort

**Explanation**: Merge Sort consistently performs at O(n log n) in all cases (best, average, and worst). It uses a divide-and-conquer approach.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the space complexity of a recursive function that makes n recursive calls?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n²)

### Back

**Correct Answer**: C) O(n)

**Explanation**: Each recursive call adds a new frame to the call stack. With n recursive calls, the space complexity is O(n) due to the stack space required.

<!-- Card End -->

<!-- Card Start -->

### Front

In a hash table with good hash function, what is the average time complexity for insertion?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n log n)

### Back

**Correct Answer**: A) O(1)

**Explanation**: With a good hash function and proper load factor, hash tables provide constant time insertion on average by directly computing the storage location.

<!-- Card End -->

<!-- Card Start -->

### Front

Which traversal of a binary tree visits nodes in ascending order for a Binary Search Tree?

A) Pre-order  
B) In-order  
C) Post-order  
D) Level-order

### Back

**Correct Answer**: B) In-order

**Explanation**: In-order traversal (left, root, right) of a BST visits nodes in sorted ascending order due to the BST property where left < root < right.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the minimum number of nodes in a complete binary tree of height h?

A) 2^h  
B) 2^h - 1  
C) 2^(h-1)  
D) 2^h + 1

### Back

**Correct Answer**: A) 2^h

**Explanation**: A complete binary tree of height h has all levels filled except possibly the last, with minimum nodes when the last level has only one node: 2^0 + 2^1 + ... + 2^(h-1) + 1 = 2^h.

<!-- Card End -->

<!-- Card Start -->

### Front

Which operation is NOT efficient in a singly linked list?

A) Insertion at the beginning  
B) Deletion at the beginning  
C) Access by index  
D) Insertion after a given node

### Back

**Correct Answer**: C) Access by index

**Explanation**: Accessing an element by index in a singly linked list requires traversing from the head, resulting in O(n) time complexity, unlike arrays which offer O(1) access.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the worst-case time complexity of QuickSort?

A) O(n log n)  
B) O(n)  
C) O(n²)  
D) O(log n)

### Back

**Correct Answer**: C) O(n²)

**Explanation**: QuickSort's worst case occurs when the pivot is always the smallest or largest element, leading to unbalanced partitions and O(n²) time complexity.

<!-- Card End -->

<!-- Card Start -->

### Front

In a priority queue implemented as a binary heap, what is the time complexity to extract the maximum element?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n log n)

### Back

**Correct Answer**: B) O(log n)

**Explanation**: Extracting the maximum requires removing the root and then re-heapifying by bubbling down, which takes O(log n) time in a binary heap.

<!-- Card End -->

<!-- Card Start -->

### Front

Which graph traversal algorithm uses a queue data structure?

A) Depth-First Search (DFS)  
B) Breadth-First Search (BFS)  
C) Dijkstra's Algorithm  
D) Topological Sort

### Back

**Correct Answer**: B) Breadth-First Search (BFS)

**Explanation**: BFS uses a queue to visit nodes level by level, ensuring all nodes at distance k are visited before any node at distance k+1.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the space complexity of an iterative implementation of binary search?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n log n)

### Back

**Correct Answer**: A) O(1)

**Explanation**: Iterative binary search uses only a few variables (low, high, mid) regardless of input size, resulting in constant space complexity.

<!-- Card End -->

<!-- Card Start -->

### Front

Which data structure is best suited for implementing undo functionality in applications?

A) Queue  
B) Stack  
C) Array  
D) Hash Table

### Back

**Correct Answer**: B) Stack

**Explanation**: Undo functionality requires LIFO behavior - the most recent action should be undone first, making stack the ideal choice.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the time complexity of finding the kth smallest element using a min-heap?

A) O(1)  
B) O(k)  
C) O(k log n)  
D) O(n log n)

### Back

**Correct Answer**: C) O(k log n)

**Explanation**: Extract the minimum k times from the heap. Each extraction takes O(log n) time, so total time is O(k log n).

<!-- Card End -->

<!-- Card Start -->

### Front

In Dynamic Programming, what does "optimal substructure" mean?

A) The problem can be broken into subproblems  
B) Subproblems overlap  
C) An optimal solution contains optimal solutions to subproblems  
D) The solution uses memoization

### Back

**Correct Answer**: C) An optimal solution contains optimal solutions to subproblems

**Explanation**: Optimal substructure means that an optimal solution to the problem contains optimal solutions to its subproblems, allowing us to build up solutions.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the average time complexity for searching in a balanced Binary Search Tree?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n log n)

### Back

**Correct Answer**: B) O(log n)

**Explanation**: In a balanced BST, the height is O(log n), and searching follows a path from root to leaf, taking O(log n) time.

<!-- Card End -->

<!-- Card Start -->

### Front

Which algorithm is used to find the shortest path in a weighted graph with no negative edges?

A) BFS  
B) DFS  
C) Dijkstra's Algorithm  
D) Bellman-Ford Algorithm

### Back

**Correct Answer**: C) Dijkstra's Algorithm

**Explanation**: Dijkstra's algorithm efficiently finds shortest paths in weighted graphs with non-negative edge weights using a greedy approach with a priority queue.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the worst-case time complexity of insertion in a hash table?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n²)

### Back

**Correct Answer**: C) O(n)

**Explanation**: In the worst case, all keys hash to the same bucket, creating a linked list of length n, making insertion O(n).

<!-- Card End -->

<!-- Card Start -->

### Front

Which sorting algorithm is stable and has O(n) best-case time complexity?

A) Quick Sort  
B) Heap Sort  
C) Insertion Sort  
D) Selection Sort

### Back

**Correct Answer**: C) Insertion Sort

**Explanation**: Insertion Sort is stable (maintains relative order of equal elements) and has O(n) best-case when the array is already sorted.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the maximum number of edges in a simple undirected graph with n vertices?

A) n  
B) n-1  
C) n(n-1)/2  
D) n²

### Back

**Correct Answer**: C) n(n-1)/2

**Explanation**: Each vertex can connect to (n-1) other vertices. Total possible edges = n(n-1)/2 (dividing by 2 because edges are undirected).

<!-- Card End -->

<!-- Card Start -->

### Front

Which condition must be satisfied for a graph to have an Eulerian path?

A) All vertices have even degree  
B) Exactly 0 or 2 vertices have odd degree  
C) The graph is connected  
D) Both B and C

### Back

**Correct Answer**: D) Both B and C

**Explanation**: For an Eulerian path to exist, the graph must be connected AND have exactly 0 or 2 vertices with odd degree.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the time complexity of the naive string matching algorithm?

A) O(n)  
B) O(m)  
C) O(n + m)  
D) O(n × m)

### Back

**Correct Answer**: D) O(n × m)

**Explanation**: The naive approach checks each position in the text (n positions) and compares with the pattern (m characters), resulting in O(n × m) time complexity.

<!-- Card End -->

<!-- Card Start -->

### Front

In a circular queue of size n, how many elements can be stored?

A) n  
B) n-1  
C) n+1  
D) 2n

### Back

**Correct Answer**: B) n-1

**Explanation**: In a circular queue, one position is kept empty to distinguish between full and empty conditions, so only (n-1) elements can be stored.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the space complexity of Merge Sort?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n log n)

### Back

**Correct Answer**: C) O(n)

**Explanation**: Merge Sort requires additional space for the temporary arrays used during the merge process, resulting in O(n) space complexity.

<!-- Card End -->

<!-- Card Start -->

### Front

Which data structure allows efficient insertion and deletion at both ends?

A) Stack  
B) Queue  
C) Deque  
D) Array

### Back

**Correct Answer**: C) Deque

**Explanation**: A deque (double-ended queue) allows O(1) insertion and deletion operations at both the front and rear ends.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the minimum height of a binary tree with n nodes?

A) log₂(n)  
B) ⌊log₂(n)⌋  
C) ⌈log₂(n+1)⌉  
D) n

### Back

**Correct Answer**: B) ⌊log₂(n)⌋

**Explanation**: The minimum height occurs in a complete binary tree. For n nodes, the height is ⌊log₂(n)⌋ (floor of log base 2 of n).

<!-- Card End -->

<!-- Card Start -->

### Front

Which algorithm technique is used in the Knapsack problem?

A) Greedy  
B) Divide and Conquer  
C) Dynamic Programming  
D) Backtracking

### Back

**Correct Answer**: C) Dynamic Programming

**Explanation**: The 0/1 Knapsack problem exhibits optimal substructure and overlapping subproblems, making Dynamic Programming the most efficient approach.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the time complexity of checking if a binary tree is balanced?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n log n)

### Back

**Correct Answer**: C) O(n)

**Explanation**: To check if a tree is balanced, we need to compute the height of each subtree, visiting each node once, resulting in O(n) time complexity.

<!-- Card End -->

<!-- Card Start -->

### Front

In a trie data structure, what does each node typically represent?

A) A complete word  
B) A character  
C) A prefix  
D) A suffix

### Back

**Correct Answer**: B) A character

**Explanation**: In a trie, each node represents a single character, and paths from root to leaf represent complete words or prefixes.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the worst-case time complexity for deleting a node from a Binary Search Tree?

A) O(1)  
B) O(log n)  
C) O(n)  
D) O(n log n)

### Back

**Correct Answer**: C) O(n)

**Explanation**: In the worst case, the BST is skewed (like a linked list), and deletion requires traversing the entire tree, taking O(n) time.

<!-- Card End -->

<!-- Card Start -->

### Front

Which algorithm is most suitable for finding all pairs shortest paths?

A) Dijkstra's Algorithm  
B) Bellman-Ford Algorithm  
C) Floyd-Warshall Algorithm  
D) A* Algorithm

### Back

**Correct Answer**: C) Floyd-Warshall Algorithm

**Explanation**: Floyd-Warshall algorithm efficiently finds shortest paths between all pairs of vertices in O(n³) time using dynamic programming.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the advantage of using a doubly linked list over a singly linked list?

A) Less memory usage  
B) Faster insertion at the beginning  
C) Bidirectional traversal  
D) Better cache performance

### Back

**Correct Answer**: C) Bidirectional traversal

**Explanation**: Doubly linked lists allow traversal in both directions due to the previous pointer, enabling efficient backward navigation and deletion of arbitrary nodes.

<!-- Card End -->

<!-- Card Start -->

### Front

In the context of algorithm analysis, what does "amortized time complexity" refer to?

A) Best-case time complexity  
B) Worst-case time complexity  
C) Average time per operation over a sequence  
D) Space-time trade-off

### Back

**Correct Answer**: C) Average time per operation over a sequence

**Explanation**: Amortized analysis considers the average performance over a sequence of operations, smoothing out expensive operations across multiple cheap ones.

<!-- Card End -->

<!-- Card Start -->

### Front

Which data structure is typically used to implement BFS in graph traversal?

A) Stack  
B) Queue  
C) Priority Queue  
D) Deque

### Back

**Correct Answer**: B) Queue

**Explanation**: BFS uses a FIFO queue to ensure that vertices are visited level by level, maintaining the breadth-first order.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the time complexity of building a heap from an unsorted array?

A) O(log n)  
B) O(n)  
C) O(n log n)  
D) O(n²)

### Back

**Correct Answer**: B) O(n)

**Explanation**: Building a heap using the "heapify" approach from bottom-up takes O(n) time, which is more efficient than inserting elements one by one.

<!-- Card End -->

<!-- Card Start -->

### Front

Which property is violated if a Binary Search Tree becomes unbalanced?

A) BST property  
B) Heap property  
C) Time complexity efficiency  
D) Node connectivity

### Back

**Correct Answer**: C) Time complexity efficiency

**Explanation**: An unbalanced BST still maintains the BST property, but operations degrade from O(log n) to O(n) time complexity in the worst case.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the primary advantage of using merge sort over quick sort?

A) Better average-case performance  
B) Less memory usage  
C) Guaranteed O(n log n) performance  
D) Simpler implementation

### Back

**Correct Answer**: C) Guaranteed O(n log n) performance

**Explanation**: Merge sort always performs in O(n log n) time regardless of input, while quick sort can degrade to O(n²) in the worst case.

<!-- Card End -->

<!-- Card Start -->

### Front

In a graph with V vertices and E edges, what is the space complexity of an adjacency matrix representation?

A) O(V)  
B) O(E)  
C) O(V²)  
D) O(V + E)

### Back

**Correct Answer**: C) O(V²)

**Explanation**: An adjacency matrix requires a V×V matrix to represent all possible edges between vertices, regardless of the actual number of edges.

<!-- Card End -->

<!-- Card Start -->

### Front

Which algorithm design paradigm does binary search follow?

A) Greedy  
B) Dynamic Programming  
C) Divide and Conquer  
D) Backtracking

### Back

**Correct Answer**: C) Divide and Conquer

**Explanation**: Binary search repeatedly divides the problem space in half, solving the problem by conquering smaller subproblems.

<!-- Card End -->

<!-- Card Start -->

### Front

What is the maximum number of comparisons needed to find an element in a sorted array of size n using binary search?

A) n  
B) n/2  
C) log₂(n)  
D) ⌈log₂(n+1)⌉

### Back

**Correct Answer**: D) ⌈log₂(n+1)⌉

**Explanation**: Binary search makes at most ⌈log₂(n+1)⌉ comparisons, where ⌈⌉ represents the ceiling function, accounting for the worst-case scenario.

<!-- Card End -->