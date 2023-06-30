# Data Structures

# Arrays
Is a sequence/collection of elements that can be individually referenced by using an index to a unique identifier.

## Static Arrays
A static array is a fixed length container containing n elements *indexable* from the range \[0, n-1]. All the adresses are adjacent.

![[Pasted image 20230531204531.png]]

Note: *indexable* means that each slot/index in the array can be referenced with a number.

## Dynamic Arrays
A dynamic array can grow and shrink in size in order to behave the elements in the most consistent way possible.

![[Pasted image 20230531204736.png]]

## Complexity Analysis

![[Pasted image 20230531205356.png]]

# Linked Lists
A linked list is a sequential list of nodes that hold data which point to other nodes also containing data. The last node always points to null, meaning that are no more nodes after this point.

**Terminology:**
- **Head:** The first node in a linked list.
- **Tail:** The last node in a linked list.
- **Pointer:** Reference to another node.
- **Node:** An object containing data and pointer(s).

## Singly Linked Lists
Singly linked lists only hold reference to the next node.

![[Pasted image 20230531182154.png]]

## Doubly Linked Lists
Doubly linked lists hold reference to the next and the previous node.

![[Pasted image 20230531182235.png]]

## Singly Linked x Doubly Linked

![[Pasted image 20230531205557.png]]

## Complexity Analysis

![[Pasted image 20230531205513.png]]

# Stacks
A stack is a one-ended linear data structure which modelas a real world stack by having two primary operation, namely *push* and *pop*.

![[Pasted image 20230531204436.png]]

## Complexity Analysis

![[Pasted image 20230531205208.png]]

# Queues
A queue is a linear data structure which models real world queues by having two primary operations, namely *enqueue* and *dequeue*.

**Terminology:**
- **Enqueue = Adding = Offering:** add an element to the queue back.
- **Dequeue = Polling = Removing:** remove an element from the queue front. 

![[Pasted image 20230531212158.png]]

## Complexity Analysis

![[Pasted image 20230531213017.png]]

# Priority Queue
A priority queue is an abstract data type (ADT) that operates similar to anormal queue except that each element has a certain priority. The priority of the elements in the priority queue determine the order in which elements are removed from the PQ.

**Note:** Priority queues only supports comparable data, meaning the data inserted into the priority queue must be able to be ordered in some way either from least to greatest or greatest to least. This is so that we are able to assign relative priorities to each element.

## Complexity Analysis PQ with Binary Heap

![[Pasted image 20230605174132.png]]
![[Pasted image 20230605174342.png]]

## Turning Min PQ into Max PQ
**Problem:** Often the standard library of most programming languages only provide a min PQ which sorts by smallest elements first, but sometimes we need a Max PQ.

Since elements in a priority queue are comparable they implement some sort of comparable interface which we can simply negate to achieve a Max heap.

![[Pasted image 20230605184103.png]]
![[Pasted image 20230605184145.png]]

## Binary Heap Representation

![[Pasted image 20230605190105.png]]

## Adding Elements to Binary Heap
**Priority queues** are usually implemented with **heaps** since this gives them the best possible time complexity.

The **priority queue** (PQ) is an abstract data type (ADT), hence heaps are not the only way to implement PQs. As an example, we could use unsorted list, but this would not give us the best possible time complexity.

There are many types of **heaps** we could use to implement a **priority queue**, including: **binary heap**, **Fibonacci heap**, **binomial heap**, **pairing heap** etc.

### Bubble Up
To insert a new element in a **heap**, the algorithm **bubble up** is used. It is to put the new item in the first vacant cell of the array. Then move it up in the **heap** based on its value compared to its parent. In a max **heap**, it should be below a node with a larger key and above 1 or 2 child nodes with smaller keys.

## Removing Elements From a Binary Heap
The remove operation is to remove the element with the highest value, which is the first one in the **array**. When we remove the first element in the **array**, we move the last element to fill out the empty spot. But this element’s value might be smaller than its children’s. 

### Bubble Down
**Bubble down** is an algorithm used in **heap** deletion. It is to compare the parent node with child nodes in a sub-tree. If the parent node is smaller, you should switch the parent element with child nodes in a **max heap**.

## Removing Elements From Binary Heap in O(log(n))
---
The inefficiency of the removal algorithm comes from the fact that we have to perform a **linear search** to find out where an element is indexed at. What if instead we did a lookup using a **hashtable** to find out where a node is indexed at?

A **hashtable** provides a constant time lookup and update for a mapping from a key (the node value) to a value (the index).

![[Pasted image 20230605233213.png]]

# Bibliography
https://youtu.be/RBSGKlAvoiM
https://www.geeksforgeeks.org/how-do-dynamic-arrays-work/