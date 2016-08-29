#Data Structures

A survey of common structures and how to work with them

-
-
## A primer on Complexity

- The number of operations performed by an algorithm is its complexity
- Complexity is a relative measure, using variables for input/data size
- Complexity is represented with "Big O" notation (It's showtime!)
  - Big O notation refers to the worst-case scenario, simplified to an order of magnitude
  - Example notations: `O(1)`, `O(n)`, `O(log n)`, `O(n * m)`, `O(n^2)`...

-
### Examples

Printing every element in an array: O(n)

```Java
int n = theArray.length;
for(int i = 0; i < n; i++){
  System.out.println(theArray[i]);
}
```

-
### Examples

- Multiplying every element of an array times every other element: O(n^2)

```Java
int n = theArray.length;
for(int i = 0; i < n; i++){
  for(int j = 0; j < n; j++){
    System.out.println(theArray[i] * theArray[j]);
  }
}
```


-
-
## Arrays

-
### Sorting arrays

- Insertion sort
- Selection Sort
- Bubble sort

-
### Searching arrays

Return the index for the element if found, -1 otherwise

- search linearly
- binary search (sorted only)


-
-
## Linked Lists

-
### Linked List Vocabulary

- Node - an element in a linked list. Contains a value and references to the next (and sometimes previous) node
- Head - The first node in a linked list
- Tail - the last node in a linked list

-
### Linked lists

 - a series of nodes, each with a reference to the next one
 - Keeps a reference to the Head (first) node
 - Random Access is slow but adding and removing elements is faster than arrays

-
### Doubly linked lists

- Doubly linked lists have a reference to the previous node as well as next
- Can be more useful for iteration
- Can be used to implement stacks and queues


-
-
## Maps

-
### Maps

- Also known as Dictionaries or Associative Arrays
- Associate keys to values
- Can be implemented in many data structures

-
-
## Trees

-
### Tree Vocabulary

- Root - the top-level node of a tree (like the linked list head)
- Leaf - A node with no children
- Subtree - Any node and all of its children
- Traversal - visiting/examining each element in a tree only once
- Depth - the distance of a node from the root
- Height - The maximum depth of a tree
- -arity - the number of children a tree node can have

-
### -Arity

- Analogy: A binary star system has two stars, a trinary star system has three stars.
- binary trees have up to 2 children per node, trinary trees have up to 3
- Trees can have fixed or variable arity
- Linked lists are technically unary trees

-
### -Arity notation

1. Unary, Singulary, 1-ary
2. Binary, 2-ary
3. Trinary, 3-ary
4. Quaternary, 4-ary
5. 5-ary
6. 6-ary

...etc.

-
### Tree Traversal (aka Searching)

- Breadth-first search
- Depth-first search
- Depth-limited search

-
-
## Graphs

-
### Graph vocabulary

- Vertex - a node in a graph (plural: vertices)
- Edge - the connection between two nodes
- Path - the sequence of edges and vertices traversed to move from one vertex to another

-
### Graph features

- Edges represent relationships between vertices
- Edges can have a weight (or cost) associated with them
- Any vertex can be connected to any other vertex, sometimes multiple times
  - This can create cycles in graphs; these are valid and can produce interesting results
- Edges can be directed or undirected. Directed edges can only be traversed in a fixed direction

-
### Trees are a subset of graphs

A few restrictions:
- Trees cannot have cycles
- Trees' edges are directed away from the root

-
-
## Additional Resources

- [List of Data Structures](https://en.wikipedia.org/wiki/List_of_data_structures)
- [Tree Traversal](https://en.wikipedia.org/wiki/Tree_traversal)
- [Data Structures and Algorithms on TutorialsPoint](http://www.tutorialspoint.com/data_structures_algorithms/index.htm)