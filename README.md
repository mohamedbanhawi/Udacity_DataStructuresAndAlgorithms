# Udacity_DataStructuresAndAlgorithms
Notes and some code based on the https://www.udacity.com/course/data-structures-and-algorithms-in-python--ud513

**1- Efficiency**
- Space and time complexity.
- Notation:
	- Big O notation O(n).
	- Worse case is used as an upper bound. Can calculate best, & average.

**2- List-Based Collection**
- Collection is a group of things
	- No particular or inherent order.
      - All elements don’t need to be of the same type.
- **Arrays, Linked Lists, Stacks and Queues**.
- *Lists*:
	- Objects have an order.
      - Not the same type.
      - No length or set size
      - No inherent order.
- *Arrays*:
	- Each array has an index.
      - Insertion and deletion is difficult/inefficient in arrays [O(n)]
- *Linked List*:
	- No indices.
      - Each element knows what’s the next element is. (Instead of an index in the case of an array)
      - Inseration and deletion is rather easy. [O(1)]
      - Usually the same as an array in Python e.g.
      - Doubly Linked List stores both next and previous element.
- *Stacks*
	- List based data structure.
	- Can only access the most recent element (like a news feed). LIFO
       - Add is **push**, remove is **pop** this operation is O(1).
       - You can use a linked list or arrays to implement a stack
- *Queues*
    - List based data structure
    - Opposite of a stack, FIFO.
    - Head is oldest, tail is newest.
    - Eneque (add) and dequeue (remove)
    - Deques is a generalisation where you can enque and deque from both sides.
     - *Prioriy Queue* - remove the highest priority 

**3- Searching and Sorting**
- *Binary search*:
	- Sorted array:
       - Keep dividing the array in half.
       - O(log(n))
- *Recursion*:
	- Function that runs within a function.
- *Sorting*:
	- In place: no need to copy the data structure. I.e. space complexity O(1).
       - E.g insertion sort https://en.m.wikipedia.org/wiki/Insertion_sort
- *Bubble sort* is the naive approach *in each loop the larget element will bubble to the end*.
-  Naive bubble sort is O(n^2) and O(1) space complexity.
- *Merge sort*: split an array as much as possible. Ie divide and conquer.
	- o(nlog(n)) time and space o(n).
- * Quick sort*:
   - Select a pivot, move everything lower before and higher after.
    - Repeat with a pivot after and pivot before.
    - Worstcase is o(n^2), average and best: o(nlog(n)) time and space is o(1) i.e. in place.

**4- Maps and Hashing**
- *Maps* are a key and a value structure also refered to as dictionaries.
- *Sets*: a collection of elements that have no orders but do not allow for repeated values.
	- The keys for a map are a set, i.e they are unique.
- *Hash*: allows you to lookup any element by value in constant time.
	- Convert a value (hashing) into an index.
       - Collision might occur of indices are not unqiue, collisions can be fixed by changing the function or creating a bucket of elements with the same hash.
	- The bucket can be another hash function.
       - The load factor = entries / bucket
- *Hash maps* <key, value>, create a hash for the key.
	- Can work with string keys using ASCII values.

**5- Trees**
- Tree is an extension of linked list.
	- The first element is a root
	- A tree can have several next elements (unlike linked list).
	- Nodes are elements of a tree.
	- Trees must be connected from the root.
	- No cycles i.e. no two ways to reach a node.
- Properties
	- *Levels* how many edges to reach the root from leaf + 1 
	- Nodes are described as *parents / children* relationship.
	- Connections are called *edges*.
	- *Leaves* are external nodes (i.e. no children)
	- The *height* of a node is the number of edges to the to a leaf
	- The *depth* of a node is the number of edges to the root.
- *Traversing a tree*
	- A way to check all nodes
	- Two main methods, DFS, BFS (level traversal).
	- DFS: Preorder (check off a node before seeing children)
	- DFS: Inorder (check off a node when seeing a left child) - go from left to right 
	- DFS: Postorder (check off a node after seeing all children)
- *Binary Tree*
	- A tree where a node can only have a maximum of two children.
	- Insertion is requires traversing through the tree to find a leaf node or a child node. 
		- At every level we can add twice as many elements,
		- Search is O(n)
		- Therfore insertion is O(logn) worst case scenario, i.e. going through all levels to reach a node.
	- *BST (Binary Search Tree)* is a type of binary tree.
		- Every value on the left is larger
		- Search is O(logn) worst case height of the tree.
		- Unbalanced BST, is the worst case scenario.
- *Heap*
	- Tree (not binary) arranged in order such that the root is largerst (max heap) or smallest value (min heaps)
	- Root max value is a called the peak.
	- Search is O(n).
	- Reorder the tree based on the heap property i.e heapify.
	- Insert and delete is O(logn) using *heapify* i.e height of the tree for a binary heap.
	- Heaps can be implemente as arrays as they are complete i.e each level must be full before moving to a lower level. *to save some space*
- *Red black tree* 
	-  binary tree that is self-balancing
	-  (1) nodes are labelled as red or black
	-  (2) null leaf nodes which are black.
	-  (3) if a node is red, all children must be black
	-  (4) the path from a node to a descendent null node will contain the same number of black nodes.
	-  (5) inserting red nodes


**6- Graphs**

- Modelling relationships between objects.
- Consists of nodes (vertices) and edges.
- Two connected nodes are *adjacent*
- Edges can have a direction *directed graph*
- *Acyclic graphs* have no cycles.
- DAG (directed acyclic graph).
- Connectivity: all vertices are reachable.
- Connectivity = minimum number of elements that can be removed before the graph is disconnected.
- Graphs can be represented using a 2D edge list. [[edge], [edge], [edge]]
- Graphs can be represnted using an adjacency list [[0], [1,2]]
- Graphs can be represnted using an adjacency matrix (nxn) where n is the number of elements, if nodes (i,j) are connected therefore m(i,j) = 1, and m(i,i) = 0.
- DFS can be used. Seen nodes are added into the stack, if you reach a seen node, pop from stack and return to the previous node.
- BFS, search each edge of a node, then mark as seen, add to a queue.
- Efficiency is O(2*E + V) ~ O(E)


**7 - Case studies**
- *Shortest Path Problem*
	- For an unweighted graph, BFS is the shorted path solution.
- *Dijkstra's Algorithm*
	- All vertices are assigned a distance value
	- Start with infinity
	- using a min priority queue using extract min. always take a node with the lowest value (greedy algorithm) O(V^2)
- * Knapsack Problem*
	- You have a limited weight capacity.
	- Many items with limited weight and values.
	- It is required to maximize value.
- *Travelling Salesman Problem*:
	- NP hard (cannot be solved in polynomial time).
	- Exact (not polynomial, but optimal)
	- Approximate (polynomial but not optimal)
	- Dynamic programming: Held-Karp algorithm
	- Christofides Algorithm (convert the graph into the tree).

**8- Questions**
- Clarifying the Question
- Confirming Inputs
- Test cases
- Brain storming
- Runtime analysis
- Coding
- Debugging
- Wrap up
- Pramp
